![image](https://github.com/user-attachments/assets/d5202bae-bfec-4bd2-9464-63525ae66e25)# Observability On AWS

## Onbservability: Monitoring and Logging
A system is observable if its state can be inferred from measurement. It that system can be conrolled and observed, it can be optimizes.

AWS defines observability as **how well you can understand what is happening in a system** , often by instumenting it to collect metrics, logs, or traces.

## CloudWatch
Amazon cloudwatch is a service that monitors applications, responds to performance changes, optimizes resource use, and provides insights into operational health. By collecting data across AWS resources. CloudWatcch gives visiblity into system-wide performance and allows users to set alarms, automatically react to changes, and gain a unifiedd view of operational health.

### Benefits
- visualize and analyze your data with ene-to-end observability.
- Operate efficiently with automation.
- Quickly obtain an integrated view of your AWS or other resources.
- Proactively monitor and get actional insights to enhance and user experiences.

### Use Cases
- **Montior application performance**
- **Perform root cause analysis**
- **Optimize resources proactivily**
- **Test website impacts**
## AWS X-Ray
AWS X-Ray provides a complete view of requests as they travel through your application. It filters visual data across payloads, functions, traces, services, APIs, and more with no-code and low-code motions.
### Benefits
- Easy Tracking
- Improved performance
- Removing obstacle
- Save Time and Money
### How it Works
AWS X-Ray provides a complete view of requests as they travel through your application and filters visual data across payloads, functions, traces, servies, APIs and more with no-code and low-code motions.

![image](https://github.com/user-attachments/assets/98c5afcb-9826-4281-a4e2-798768c719aa)

### Use Cases
- **Analyze and debug applications**
- **Genrate a detailed service map**
- **View performance analytics**
- **Audit your data severly**

## Difference between observability and montoring
One of the most common questions asked by vloudwatch users is the difference between observaility and montoring. **Monitoring** is a subset of observability, and you will often see monitoring, tracing, and logging described as the **three pillars of observability.** However, other tools help you achieve observability, such as code profiles and artifical intelligence for IT operations (AIOPs).

Monitoring can tell us that an application is not woking properly. Tracing can help us get to thr root causes quickly and efficiently and logging can help us dive deeper. Observability can also provide us with information about business outcomes, capacity, service level agreements, performance, and rightsizing.

## Three Pillars of Observability
### CloudWatch Meterics
CloudWatch monitoring helps you track metrics. Metrics are a numeric representation of data measured over intervals of time or time series data. They help identify trends, mathematical modeling and prediction.
### CloudWatch Log
Logs are immutable timestamped records of discrete events that happen over time. They help uncover emergent and unpredictable behaviour.
### AWS X-Ray Traces
Traces represent a series of related distributed events that encode the end-to-end request flow through a distributed systems. They provides visibility, such as latency, into the path traversed by a request and the structure of the request.
## Aamazon Best Practices for Logging
Log the availability and latency of all dependencies. This is particularly helpful when answering questions about **why a request is slow** or **why a request fails**

**Break out dependency meterics per call resource, or status code.**

**Record memory queue depths when acessing them.**

**Add an additional counter for every error reson.**

**Organize errors by category of cause.**

## CloudWatch and the CloudWatch Agent
### How it works
#### Amazon CloudWatch
Amazon cloudwatch gives you complete visibility into you cloud resources and applications. You can collect, monitor, act on, and analyze yor data.
