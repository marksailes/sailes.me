---
title: AWS Messaging
date: "2020-08-18T23:46:37.121Z"
template: "post"
draft: false
slug: "aws-messaging-is-hard"
category: "Serverless Messaging"
tags:
  - "AWS"
  - "Messaging"
description: "How to choose an AWS messaging service"
socialImage: "/media/image-2.jpg"
---

At AWS I work as a specialist solutions architect for serverless. I work with a dizzying mix of customers at all levels 
of cloud experience. I also work with a lot of other AWS SAs to help them understand the differences between different 
services and in my case especially serverless ones.

A topic of conversation which often comes up with customers and other SAs is how to choose which messaging service for 
an asynchronous workload. A couple of years ago this topic would have been a simpler. Before the 
release of Amazon Managed Streaming for Apache Kafka (Amazon MSK), Amazon MQ for Apache ActiveMQ and Amazon EventBridge
there wasn't so much cross over between the messaging services. Now the ven diagram is slightly more complex.

So where to start?

*Personally I start by asking: Will there be multiple consumers.*

To expand on this further I mean will there be multiple separate system which want to consume this data. This is 
important in order to differentiate between (SQS, Amazon MQ) and (Kinesis, MSK, SNS and EventBridge).

Although the programming model is sightly different SQS and Amazon MQ are both designed for messages to be removed once
they have been processed. This obviously makes it impossible to have more than one system processing the events.

This might be a topic for another post, but this doesn't exclude either of these services from being highly scalable.
However let's address that another time.

If the use case is single consumer, then how do we choose between SQS and Amazon MQ? 

SQS is a true serverless service. You only pay for what you use, SQS scales transparently, has high availability and 
fault tolerance built in and to top it off there are no servers to manage. Amazon MQ is server based, and you will have 
to choose a cluster design which gives you the availability and fault tolerance your system requires. If your cluser isn't
receiving messages you will still be charged at the full rate. 







