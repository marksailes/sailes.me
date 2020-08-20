---
title: "Amazon SQS"
template: "page"
socialImage: "/media/profile.jpg"
---

## Start Well - Amazon SQS

A collection of useful information for developers, ops and builders.

### Serverless Ticklist

![tick](media/icons8-tick-box-48.png) No servers to maintain
![tick](media/icons8-tick-box-48.png) Scales with usage
![tick](media/icons8-tick-box-48.png) No cost for idle
![tick](media/icons8-tick-box-48.png) High availability and fault tolerant

### Developer Tips

SQS pairs really well with AWS Lambda and saves you the big job of handling the polling of the queue and confirming the 
deletions.

### Scaling

#### With AWS Lambda
When used as an event source with AWS Lambda, the Lambda service will scale up the consuming processes as long as there
are messages waiting.

This will increase by 60 additional batches per min.

The maximum number of batches for a single event source is 1000

Reference: [Using AWS Lambda with Amazon SQS](https://docs.aws.amazon.com/lambda/latest/dg/with-sqs.html)


### Monitoring

Top of my list of metrics to monitor are:

ApproximateAgeOfOldestMessage - If this value is increasing then you are falling behind in processing.

### Defaults to change

SQS visibility timeout (30s) - This means if you have a failure for whatever reason. The next retry won't happen for up
to 30s.

### Cost Optimization

#### With AWS Lambda

When integrated with AWS Lambda reduce the number of invokes you make by consuming messages in batches.

#### With the SDK

In almost all cases long polling will reduce your costs by making less calls to the ReceiveMessage API. The downside is 
that your applicaiton needs to be able to handle the long idle times. This is best handled with a separate thread.
