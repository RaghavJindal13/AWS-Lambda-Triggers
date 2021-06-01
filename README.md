<h1 align="center">
 <img src="https://images.squarespace-cdn.com/content/v1/51814c87e4b0c1fda9c1fc50/1528473310893-RH0HG7R5C0QURMFQJBSU/ke17ZwdGBToddI8pDm48kOyctPanBqSdf7WQMpY1FsRZw-zPPgdn4jUwVcJE1ZvWQUxwkmyExglNqGp0IvTJZUJFbgE-7XRK3dMEBRBhUpyD4IQ_uEhoqbBUjTJFcqKvko9JlUzuVmtjr1UPhOA5qkTLSJODyitRxw8OQt1oetw/600px-AWS_Lambda_logo.svg.png" width="50" height="50" /> AWS Lambda
</h1>


AWS Lambda provides you a serverless architecture and allows you to run a piece of code in the cloud after an event trigger is activated.\
AWS Lambda is a zero-administration compute platform for the back-end web developers that runs your code for you on the AWS Cloud and provides you with a fine-grained pricing structure.\
AWS Lambda runs your backend code on its own AWS compute fleet of Amazon EC2 instances across multiple Availbility zones in a region which provides the high avilability,security,performance,and scalability of AWS infrastructure.

<br></br>
<table>
  <tr>
    <th colspan=2>Execution Role (Common Execution Role Available).</th>
  </tr>
  <tr>
    <td><b>AWSLambdaBasicExecutionRole</b></td>
    <td>Grants permissions only for the Amazon CloudWatch Logs actions to write logs.</td>
  </tr>
  <tr>
    <td><b>AWSLambdaKinesisExecutionRole</b></td>
    <td>Grants permissions for Amazon Kinesis Streams actions, and CloudWatch Logs actions.</td>
  </tr>
  <tr>
    <td><b>AWSLambdaDynamoDBExecutionRole</b></td>
    <td>Grants permissions for DynamoDB streams actions and CloudWatch Logs actions.</td>
  </tr>
  <tr>
    <td><b>AWSLambdaVPCAccessExecutionRole</b></td>
    <td>Grants permissions for Amazon Elastic Compute Cloud (Amazon EC2) actions to manage elastic network interfaces (ENIs).</td>
  </tr>
  <tr>
    <td><b>AWSXrayWriteOnlyAccess</b></td>
    <td>Grants permission for X-ray to to upload trace data to debug and analyze.</td>
  </tr>
</table>


## VPC
```
1. When you enable VPC, your Lambda function will lose default internet access.
2. If you require external internet access for your function, ensure that your security group allows outbound connections.
   and that your VPC has a NAT gateway.
``` 
## Concurrency
~~~
1. Concurrent Execution refers to the execution of number of function at a given time. By default the limit\ is 1000 across all function within a given region.
2. AWS Lambda keeps 100 for the unreserved function.
3. So, if there are 1000 then you can select from 900 and reserve concurrency for selected function and rest 100 is used for the unreserved function.
~~~

## DLQ (Dead Letter Queue)
~~~
1. Failed Lambda is invoked twice by default and the event is discarded.
2. DLQ instruct lamnda to send unprocessed events to AWS SQS or AWS SNS.
3. DLQ helps you troubleshoot and examine the unprocessed request.
~~~
## Cron Job
~~~
1. Cron Jobs allow you to automate certain commands or scripts on your server to complete repetitive tasks automatically.
2. Cron Job can be set to run by 15 minute or hourly increments, a day of the week or month, or any combination of these.
3. This means that you can trigger the Lambda function automatically fter every time interval which is specified.
4. rate(1 day) OR cron(0 17 ? * MON-FRI *)  --0 mins 17hrs every month mon to fri every year.
~~~
## Throttle
~~~
1. Throttle will set reserved concurrency of the function to zero and it will throttle all future invocation.
2. If the function is throttled then it will fail to run.
3. If the fucntion is ran from Lambda console then it will throw "Calling the Invoke API failed with message: Rate Exceeded."
~~~
## Invoke Lambda function from another Lambda Function
~~~
1. create two lambda functions and add awsLambdaRole in the existing basic rule.
2. A Lambda can invoke another Lambda.
3. A Lambda in one region can invoke another lambda in other region.
4. A Lambda can invoke same Lambda.
5. Invoke same Lamba with different version.
~~~

## EC2 instance state and status check via Lambda function
~~~
1. Check state and ststus of all ec2 instances.
2. Get the state change notification in s3 bucket.
3. Trigger email notification of ec2 instance state change.
4. SSH into ec2 instance via lambda function.
5. Fetch date and time of stopped ec2 instance.
~~~
## Trigger email notification
~~~
1. Flow will be like whenever we make a cnagse in s3 bucker lambda will trigger SES.
2. Under the S3 bucket properties enable events.
3. You can also send the file which have been modified or added in the mail.
~~~
