# Question 28

A company runs a messaging application in the ap-northeast-1 and ap-southeast-2 region. A Solutions Architect needs to create a routing policy wherein a larger portion of traffic from the Philippines and North India will be routed to the resource in the ap-northeast-1 region.

Which Route 53 routing policy should the Solutions Architect use?

## Options

A. Latency Routing

B. Geolocation Routing

C. Geoproximity Routing

D. Weighted Routing

## Correct Answer

**C. Geoproximity Routing**

## Explanation

Geoproximity Routing lets Amazon Route 53 route traffic to your resources based on the geographic location of your users and your resources. You can optionally choose to route more traffic or less to a given resource by specifying a value, known as a bias.

A bias expands or shrinks the size of the geographic region from which traffic is routed to a resource.

### Why other options are incorrect:

- **B** - Geolocation can't control coverage size.

- **A** - Latency routing is for performance, not geography.

- **D** - Weighted routing is for proportional traffic distribution.

## References

- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html
- https://tutorialsdojo.com/latency-routing-vs-geoproximity-routing-vs-geolocation-routing/

## Domain

Design Resilient Architectures
