# Question 51

Multiple ALBs across regions. Need to reduce whitelist IPs on corporate firewall.

Which approach?

## Options

A. Global Accelerator with endpoint group per region + ALBs.

B. NLB with Elastic IP + ALBs as targets.

C. Global Accelerator with endpoints for EC2 private IPs.

D. Lambda to track ALB IPs and update firewall.

## Correct Answer

**A. Global Accelerator with endpoint group per region + ALBs.**

## Explanation

AWS Global Accelerator:
- **Two static IPs**: Whitelist only these IPs
- **Endpoint groups**: One per region
- **ALBs as endpoints**: Inside each group
- **Auto-updates**: No need to track IPs

### Why other options are incorrect:

- **B** - NLB can't route to ALBs across regions.

- **C** - Associate ALBs, not private EC2 IPs.

- **D** - High overhead; Global Accelerator is simpler.

## References

- https://docs.aws.amazon.com/global-accelerator/latest/dg/about-endpoint-groups.html
- https://tutorialsdojo.com/aws-global-accelerator/

## Domain

Design Secure Architectures
