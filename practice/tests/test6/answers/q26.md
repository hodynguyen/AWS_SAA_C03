# Question 26

CloudFront origin hit for every request instead of edge cache. Even for commonly requested objects.

What is a possible cause?

## Options

A. Cached object file sizes too large.

B. Cache-Control max-age set to zero.

C. Two primary origins in origin group.

D. Objects not requested before.

## Correct Answer

**B. Cache-Control max-age set to zero.**

## Explanation

CloudFront caching:
- **max-age=0**: Objects expire immediately
- **Always fetch from origin**: No edge caching
- **Cache-Control header**: Controls TTL
- **Solution**: Increase max-age value

### Why other options are incorrect:

- **A** - File size doesn't affect cache hit ratio.

- **C** - Can't have two primary origins; only primary + secondary.

- **D** - Scenario says "commonly requested," so they were requested.

## References

- http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Expiration.html
- https://tutorialsdojo.com/amazon-cloudfront/

## Domain

Design High-Performing Architectures
