# CloudFormation 
Define infrastructure as Code in JSON or YAML

- Free of charge
- There is basic template to be respected.
- The result of cloudFormation is called stack.

## Structure:
The main sections in the cloud formation template is
- Parameters: Custom Input Value
- Conditions: Provision resources based on environment
- Resources: (mandatatory) The resources to create
- Mappings: Create Custom Mappings like region: AMI
- Transforms: reference code located in s3, eg Lambda Code or reusable snippets of cloud formation code.

Only resources section is required for template to execute. [Important]
You can use the Parameters section to take in values at runtime.

- Use Fn::GetAtt to get the output data in the CF.
- By Default Automatic rollback for error are enables.
- CF is free, underline resources are charged.
- CF use Fn:GetAtt to output data


### Service Role
A service role is an AWS Identity and Access Management (IAM) role that allows AWS CloudFormation to make calls to resources in a stack on your behalf.
