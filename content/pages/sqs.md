---
title: "Amazon SQS"
template: "page"
socialImage: "/media/profile.jpg"
---

## Start Well - Amazon SQS

A collection of useful information for developers, ops and builders.

### Serverless Ticklist

![tick](/static/media/icons8-tick-box-48.png) No servers to maintain
![tick](/static/media/icons8-tick-box-48.png) Scales with usage
![tick](/static/media/icons8-tick-box-48.png) No cost for idle
![tick](/static/media/icons8-tick-box-48.png) High availability and fault tolerant

### Scaling



### Monitoring

Top of my list of metrics to monitor are:

ApproximateAgeOfOldestMessage - If this value is increasing then you are falling behind in processing.

### Defaults to change

SQS visibility timeout (30s) - This means if you have a failure for whatever reason. The next retry won't happen for up
to 30s.

### Cost Optimization

When integrated with AWS Lambda reduce the number of invokes you make by consuming messages in batches.
