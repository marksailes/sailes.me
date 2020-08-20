---
title: "Start Well - Amazon SQS"
template: "page"
socialImage: "/media/profile.jpg"
---

A collection of useful information for developers, ops, architects and everyone in-between.

## Serverless Ticklist

<ul>
    <li><img src="/media/icons8-tick-box-48.png">No servers to maintain</li>
    <li><img src="/media/icons8-tick-box-48.png">Scales with usage</li>
    <li><img src="/media/icons8-tick-box-48.png">No cost for idle</li>
    <li><img src="/media/icons8-tick-box-48.png">High availability and fault tolerant</li>
</ul>

## Developer Tips

SQS pairs really well with AWS Lambda and saves you the big job of handling the polling of the queue and confirming the 
deletions.

## Scaling

### With AWS Lambda

When used as an event source with AWS Lambda, the Lambda service will scale up the consuming processes as long as there
are messages waiting. These polling processes will automatically invoke your Lambda functions.

This will increase by 60 additional batches per min.

The maximum number of batches for a single event source is 1000

Reference: [Using AWS Lambda with Amazon SQS](https://docs.aws.amazon.com/lambda/latest/dg/with-sqs.html)

## Monitoring

Top of my list of metrics to monitor are:

`ApproximateAgeOfOldestMessage` - If this value is increasing then you are falling behind in processing.

## Defaults to change

SQS visibility timeout (30s) - This means if you have a failure for whatever reason. The next retry won't happen for up
to 30s.

## Cost Optimization

SQS charges per API call, batch API calls are charged at the same rate as standard ones. If you can use 
`SendMessageBatch`, `DeleteMessageBatch`, and `ChangeMessageVisibilityBatch` then you'll reduce costs.

### With AWS Lambda

You can configure the Lambda integration to consume SQS in batches.

### With the SDK

In almost all cases long polling will reduce your costs by making less calls to the `ReceiveMessage` API. The downside is 
that your applicaiton needs to be able to handle the long idle times. This is best handled with a separate thread.
