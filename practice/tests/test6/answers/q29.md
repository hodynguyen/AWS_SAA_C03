# Question 29

CloudFormation template is reviewed. Why will it fail?

## Options

A. Invalid Parameters section.

B. Missing Conditions section.

C. Missing Resources section.

D. Wrong AWSTemplateFormatVersion.

## Correct Answer

**C. Missing Resources section.**

## Explanation

CloudFormation sections:
- **Resources**: ONLY required section
- **Optional**: Parameters, Conditions, Outputs, etc.
- **Template anatomy**: Resources define AWS infrastructure
- **Validation**: Template fails without Resources

### Why other options are incorrect:

- **A** - Parameters is optional and valid.

- **B** - Conditions is optional.

- **D** - 2010-09-09 is the correct version.

## References

- http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-anatomy.html
- https://tutorialsdojo.com/aws-cloudformation/

## Domain

Design Resilient Architectures
