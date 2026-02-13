# Redis Persistence: RDB vs AOF (Deep Dive)

To ensure data isn't lost when Redis restarts, it supports two persistence models.

## 1. RDB (Redis Database Snapshot)
- **What it is**: A Point-in-Time snapshot of your entire dataset at specified intervals.
- **Example Config**: `save 900 1` (Save snapshot if at least 1 key changed in 900 seconds).
- **Mechanism (Forking)**:
    1. Redis parent process creates a child process (fork).
    2. Child process writes data to a temp RDB file.
    3. Old RDB file is replaced by the new one.
    4. **Parent process (Main thread) is never blocked** by disk I/O.
- **Pros**:
    - **Compact**: The file is small (compressed binary). Great for backups/DR.
    - **Faster Restore**: Redis loads an RDB file much faster than replaying AOF logs.
    - **Performance**: Maximizes Redis performance (parent process does no I/O).
- **Cons**:
    - **Data Loss**: If Redis crashes, you lose all data since the last snapshot (could be minutes).
    - **Heavy Fork**: Forking a process with 100GB of RAM takes time and CPU, potentially stalling the server for milliseconds.

## 2. AOF (Append Only File)
- **What it is**: A log of every write operation received by the server.
- **Example**: `SET key 1`, `INCR key`. AOF stores these commands as text.
- **Fsync Policies (Safety vs Speed)**:
    - `appendfsync always`: Sync to disk after *every* write. Safest (Zero data loss) but Slowest (Limited by disk speed).
    - `appendfsync everysec` (**Default**): Sync once per second. Fast enough, only lose 1s of data if crash.
    - `appendfsync no`: Let OS decide when to flush. Fastest but risky.
- **Pros**:
    - **Durable**: Minimum data loss (1 second usually).
    - **Readable**: AOF is just a text file. If you accidentally run `FLUSHALL`, you can stop Redis, remove the last line, and restart to recover!
- **Cons**:
    - **File Size**: AOF files grow infinitely (1 million `INCR` commands = 1 million lines).
    - **Slower Restore**: Replaying 1 million commands takes longer than loading a binary dump.
    - **Rewrite**: Redis must periodically run "AOF Rewrite" (in background) to compact the log (e.g., replace 100 `INCR` with one `SET key 100`).

## 3. Storage Auto Scaling (AOF Rewrite)
- **Problem**: When AOF file gets too big (e.g., 100GB), Disk is full.
- **Solution**: AWS ElastiCache automatically handles **AOF Rewrite** to shrink the file size without blocking the server.

## 4. Which one to use?
- **Recommended**: **Enable Both**.
    - Redis will use AOF to restore data (because it's more complete).
    - RDB is useful for backups to S3.
- **If you only want Cache**: Disable both (Pure in-memory).
