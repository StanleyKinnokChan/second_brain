# AWS Lambda

- **Overview**

    [[AWS Lambda/Untitled.png]]

    - Function-as-a-service (FaaS) - short running & focused (**Serverless!**)
    - a deployment package - a **piece of code** with specific **runtime** (Python 3.8) in **a runtime env.**
    - env. has a **direct memory** + **indirect CPU** allocation, CPU scales with memory
    - billed for the duration that a function runs
    - as default, each time you run lambda function it is in a new env.
    - **15 mins function timeout**
    - common uses
        - serverless applications (S3, API gateway, Lambda)
        - file processing (S3, S3 event, lambda)
        - database triggers (dynamoDB, Streams, lamda)
        - serverless CRON (event brdge/ CWEvents + lambda)
        - real time stream data processing (kinesis+lambda)
- **Two Network mode**
    1. public lambda

        [[AWS Lambda/Untitled 1.png]]

    2. Private Lambda

        [[AWS Lambda/Untitled 2.png]]

        - network is created along with lambda functions
        - If same subnet and security group are used, 1 ENI is only needed. ⇒ scalable
- **Security**

    [[AWS Lambda/Untitled 3.png]]

    - execution role needs to be provided with trust policy, assumed by lambda
    - temporary credential is created for Lambda function to interact with other resources
    - Lambda also have resource policy controlling what services and accounts can invoke it
- **Logging**
    - via Cloudwatch, cloudwatch logs & X-ray
    - logs from lambda executions - cloudwatchlogs recording metrics (success/ failure, retries, latency…)
    - integrated with X-ray fro distributed tracing
    - Cloudwatch logs requires permission via execution role
- **Invocation**
    1. **Synchronous Invocation**
    - client wait data to be return

    [[AWS Lambda/Untitled 4.png]]

    1. **Asynchronous Invocation**
    - not waiting, but order sent out and done
    - lambda function responsible for retries (configurable)
    - need to be Idempotent (no matter how many time the function has run, result is the same like run once)
        - not additive/ subtractive, to achieve a state

    [[AWS Lambda/Untitled 5.png]]

    1. **Event source mapping**

    [[AWS Lambda/Untitled 6.png]]

    - Kinesis data sent out data in batch to event source mapping
    - Execution role is needed even Lamda doesn’t recieve data directly from Kinesis

- **Version**
    - a version is the code + configuration of lambda function
    - immutable & has its own ARN
    - $Latest points at latest version
    - can use Aliases point at a version, which can be changed

- **Starting time**
    - 1st time ⇒ cool start is needed
    - invoke again ⇒ warm start
    - **Provisioned concurrency** ⇒ create and keep X context warm and ready to use
    - temp space is to pre-download things, eg database connection. But have to maintain clean

[[AWS Lambda/Untitled 7.png]]
