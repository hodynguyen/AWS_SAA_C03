# Question 30

EC2 instances with Systems Manager need configuration without RDP or SSH connections.

What can be used?

## Options

A. AWS CodePipeline

B. Run Command

C. AWS Config

D. EC2Config

## Correct Answer

**B. Run Command**

## Explanation

Systems Manager Run Command:
- **Remote execution**: Run commands without SSH/RDP
- **Scalable**: Execute on multiple instances simultaneously
- **Secure**: Uses IAM for authorization
- **Agentless feel**: Uses SSM Agent already installed

### Why other options are incorrect:

- **A** - CodePipeline is for CI/CD, not instance configuration.

- **C** - AWS Config tracks compliance, doesn't configure instances.

- **D** - EC2Config is legacy Windows service, not for remote commands.

## References

- https://docs.aws.amazon.com/systems-manager/latest/userguide/execute-remote-commands.html
- https://tutorialsdojo.com/aws-systems-manager/

## Domain

Design Secure Architectures
