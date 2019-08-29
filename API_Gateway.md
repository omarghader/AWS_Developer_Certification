# API Gateway
Amazon API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale
Official Doc: https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-basic-concept.html

## API Gateway Concepts:
- Create a REST API and expose a backend, Lambda function, or other AWS services
- Expose different version of API using stages.
- Send each API endpoint to a different target.
- Run efficiently with low cost.
- Scale Effortlessly.
- Track and control usage by API key.
- Throttle requests to prevent attacks.


## API Gateway Caching
- You can enable caching on you API Gateway for a stage
- You can reduce the number of calls to your backend
- TTL Default : 300s. Maximum : 3600 secondn

## Controlling Access to API GATEWAY
- *Resource policies* : create resource-based policies to allow/deny access to your APIs and methods from specified source IP addresses or VPC endpoints.
- *Standard AWS IAM roles and policies* : control who can create and manage your APIs as well as who can invoke them. 
- *IAM tags* can be used together with IAM policies to control access. 
- *Endpoint Policies*: allow you to attach IAM resource policies to interface VPC endpoints to improve the security of your private APIs
- *Lambda authorizers* : are Lambda functions that control access to REST API methods using bearer token authentication as well as information described by headers, paths, query strings, stage variables, or context variables request parameters. Lambda authorizers are used to control who can invoke REST API methods.
- *Amazon Cognito* : user pools.

- *Cross-origin resource sharing (CORS)*: control cross-domain resource requests.
- *Client-side SSL certificates* : verify that HTTP requests are from API Gateway.
- *AWS WAF* : protect your API Gateway API from common web exploits.
- *Usage plans*: provide API keys to your customers — and then track and limit usage of your API stages and methods for each API key.
