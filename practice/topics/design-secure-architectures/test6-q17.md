# Question 17

Can't connect to new EC2 instance via Remote Desktop. Has public IP, IGW, route tables in place.

What else should be done?

## Options

A. Allow inbound port 22.

B. Create a new instance.

C. Allow inbound port 3389.

D. Restart the instance.

## Correct Answer

**C. Allow inbound port 3389.**

## Explanation

Remote Desktop Protocol (RDP):
- **Port 3389**: TCP/UDP for Windows RDP
- **Security group**: Must allow inbound from your IP
- **Windows instances**: Need RDP, not SSH
- **Default**: Security groups block RDP

### Why other options are incorrect:

- **A** - Port 22 is for SSH (Linux), not RDP.

- **B, D** - New instance unlikely to have issues; check SG first.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/troubleshooting-windows-instances.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design Secure Architectures
