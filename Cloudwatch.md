# CloudWatch Metrics

- It is a service to monitor AWS resources and the application that run on AWS.
- You can use Amazon CloudWatch Events to detect and react to changes in the state of a pipeline, stage, or action. 

## Cloudwatch metrics:
- Period: default 60 seconds. 1s <= perios <= 86400. A period is the length of time associated with a specific Amazon CloudWatch statistic. Periods are defined in numbers of seconds, and valid values for period are 1, 5, 10, 30, or any multiple of 60. 
- Evaluation Period is the number of the most recent periods, or data points, to evaluate when determining alarm state.
- Datapoints to Alarm is the number of data points within the evaluation period that must be breaching to cause the alarm to go to the ALARM state. The breaching data points don't have to be consecutive, they just must all be within the last number of data points equal to Evaluation Period.

## Example of metrics:
Available EC2 metrics generally fall into three types:

- NetworkIn/NetworkOut
- DiskReadOps/DiskWriteOps
- DiskReadBytes/DiskWriteBytes
- CPUUtilization
- CPUCreditUsage

# Cloudtrail
Cloudtrail is a service to track logs, monitor and retain account activity.

