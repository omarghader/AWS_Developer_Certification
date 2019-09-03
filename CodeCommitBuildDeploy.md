# CodeCommit
It is a souce control service, very similar to git.

# CodeBuild
A fully managed CI/CD that compiles source code, run tests.

# CodeDeploy
It is an automated deployments service which allows you to deploy your application code automatically to your EC2 instances, on-premises systems and lambda functions.

## Deployment approches
- Two different deployment approaches available: In-Place and Blue/Green
- If you need to roll back, rededploy prev version.

## AppSpec file 
- The Appspec file is used to define the parameters that will be used for a CodeDeploy deployment.
- The file structure depends on whether you are deploying to Lambda or EC2/on premise instance.

### Lambda Deployments 
the file can be written in YAML or JSON. They contain the following fields:

1.Resources : The name and properties of the Lambda function to deploy.
2.Version: Reserved for future use - currently the only allowed value is 0.0
3.Hooks: specifies Lambda function to run at a certain time in the process etc.
There are two hooks allowed:

BeforeAllowTraffic: used to specify the task and function that needs to be excuted before the traffic is routed to the new lambda function
e.g test validating deployment

AfterAllowTraffic : used to specify the task and function that needs to be excuted after the traffic is routed to the new lambda function
e.g validation tests for traffc analaysis

### EC2
1. version: Reserved for future use - currently the only allowed value is 0.0
2. OS: The name of the operating system you are using.
3. Files: source and destination folder.
4. Hooks: scripts that need to run at set point in the deployment lifecycle.
(e.g) Unzip files prior to deployment lifecycle, run functional tests.


YAML file only for EC2 deployments.

Hooks:
- The content in the 'hooks' section of the AppSpec file varies, depending on the compute platform for your deployment.
- The 'hooks' section for an EC2/On-Premises deployment contains mappings that link deployment lifecycle event hooks to one or more scripts.
- The 'hooks' section for a Lambda or an Amazon ECS deployment specifies Lambda validation functions to run during a deployment lifecycle event. 
- If an event hook is not present, no operation is executed for that event. 
- This section is required only if you are running scripts or Lambda validation functions as part of the deployment.

Hook Categories:
Application Stop: Gracefully stop the application in preparation for deploying the new revision.
Download Bundle: The Code Deploy agent copies the file to a temporary location.
BeforeInstall: Details of any installation script, backing up current revision, decrypting files
Install: The code deploy agent copies the file from temporary location to correct location
AfterInstall: Details of any post application scripts e.g configuration tasks, change file permission.
ApplicationStart: restart any services that were stopped during ApplicationStop
ValidateService: Details of any test to validate the service

Then these 3 final hooks are executed for re-registering. They are also executed before beginning.
BeforeBlockTraffic: Run Tasks on instances before they are deregistered from a load balancer
BlockTraffic: Deregister instances from a load balancer
AfterBlockTraffic: Run tasks on instances after they are deregistered from a load balancer

### ECS
BeforeInstall-->AfterInstall-->AfterAllowTestTraffic-->BeforeAllowTraffic-->AfterAllowTraffic
(Start, Install, TestTraffic, AllowTraffic, and End)

FOR EC2/On-Premises
Without Classic Load Balancer
ApplicationStop -> Before Install -> AfterInstall -> Application Start -> Validate Service
With Classic Load Balancer
Block Traffic -> Application STop -> The above shit

FOR LAMBDA
BeforeAllowTraffic -->  AllowTraffic-->AfterAllowTraffic
(Start, AllowTraffic, and End )
