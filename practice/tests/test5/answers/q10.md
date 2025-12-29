# Question 10

An Auto Scaling group needs to adjust capacity based on scaling metrics and threshold values with step adjustments that vary based on alarm breach size.

Which scaling policy type is most suitable?

## Options

A. Scheduled Scaling

B. Step scaling

C. Simple scaling

D. Target tracking scaling

## Correct Answer

**B. Step scaling**

## Explanation

Step scaling:
- **Multiple adjustments**: Different actions based on breach magnitude
- **Metric thresholds**: Configure CloudWatch alarm triggers
- **Continuous response**: Responds to additional alarms during scaling
- **Granular control**: Scale more aggressively for larger breaches

### Why other options are incorrect:

- **A** - Scheduled scaling is time-based, not metric-based.

- **C** - Simple scaling uses single adjustment, not variable steps.

- **D** - Target tracking maintains a specific metric value, not step adjustments.

## References

- https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scale-based-on-demand.html
- https://tutorialsdojo.com/amazon-ec2-auto-scaling/

## Domain

Design High-Performing Architectures
