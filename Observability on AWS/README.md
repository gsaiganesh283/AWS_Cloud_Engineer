# Observability On AWS

## Observability: Monitoring and Logging
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
##### Collect
Collect meterics and logs from all you AWS resources, applications, and services that run on AWS and on permise servers.
##### Monitor
Visualize applications and infrastructure with cloudwatch dashboards. Correlate logs and metrics side by side to troubleshoot and set alerts with cloudwatch Alarms.
##### Act
Automate response to operational changes with Amazon cloudwatch events and AWS application Auto scaling. You can also use AWS Lambda functions or AWS systems manager Automation documents to respond to events or alarms.
##### Analyze
You can use cloudwatch logs insights to gather metrics for log analytics.

For exxample, you can have up to 1-second meterics, extented data retentaion of 15 months, and real-time analysis with Amazon CloudWatch metric Math.

![image](https://github.com/user-attachments/assets/5ac451cd-f201-4711-aef7-bf589b674a28)


### CloudWatch Agent Workflow
CloudWatch agent collects and sends information to collect logs and metrics.

![image](https://github.com/user-attachments/assets/180376ee-970a-4018-a998-7668b0df4e11)

#### ECS Instance with CloudWatch agent
CloudWatch agent can collect log files specified as an individual file or a group of files.

It sends them to log stream that uses instance ID as the default name. The log stream is in a log group that you configure.
#### CloudWatch Logs
Metrics are collected using data from the operating system. They are also optionally collected from procstal, collect and StatsD.
#### CloudWatch Meterics
The metrics are sent to a cloudwatch metrics namespace named CW agent by default. You can configure dimensions to organize and aggregate your metrics.
### CloudWatch agent on Containers
If you plan to deploy the cloudwatch agent on containers you can use.
#### The setup process for containers
For Amazon Elastic Containers Service (**ECS**), deploy the cloudwatch agent as a daemon task. For Amazon Elastic Kubernetes Service (**EKS**) or Kubernetes, deploy the agents as a daemon set.

![image](https://github.com/user-attachments/assets/1a44584c-92d9-42c7-9f93-a02ebbe1944b)

## CloudWatch Concepts
### Metrics
Metrics are data about the performance of your systems. By default, many services provide free metrics for resources, such as EC2 instances, Amazon Elastic Block Store (**EBS**) volumes and Amazon RDS DB instances. You can turn on detailed monitoring for some resources, such as EC2 instances, or publish application metrics. In addition, CloudWatch can load all the metrics in your account, both AWS resource metrics and application metrics you provide, for search, graphing, and alarms.

![image](https://github.com/user-attachments/assets/ea5309eb-4460-4c66-a377-3ab05bce34e3)

### Metric namespace
A namespace is a container for cloudwatch metrics. Metrics in different namespaces are isolated, so metrics from other applications are not mistakenly aggregated into the same statistics. **There is no default namespace.**

- **A namespace is a container for cloudwatch metrics.**
- **Metrics in different namespace are isolated from each other.**
- **The default namespace for metrics collected by cloudwatch agent is CW agent.**

### Metric Dimension
Metrics are uniquely defined by a name, a namespace, and zero or more dimensions. Each data point in metric has a time stamp and a unit of measure.

- A dimension is a name-value pair that is part of the identity of a metric.
- You can assign up to 30 dimensions to a metric.
- Each matric has specific characteristics that describe it.
### Metric retention
You can publish and store custom metrics as low as a 1-second resolution.
- Data points with a period of **lower tha 60 seconds** are available for **3 hours.**
- Data points with a period of **1 minute** are available for **15 days.**
- Data points with a period of **5 minutes** are available for **63 days.**
- Data points with a period of **1 hour** are available for **455 days (15 months).**

![image](https://github.com/user-attachments/assets/1a4fddcb-c761-449b-b79a-a138f591e37c)

Data points that are initially published within a shorter period are aggregated together for long-term storage. For example, if you collect data using a period of 1 minute, the data remains available for 15 days with a 1-minute resolution. After 15 days, the data is still available, but it is aggregated and only retrievable with a resolution of 5 minutes. After 63 days, the data is further aggregated and available with a resolution of 1 hour.

### Metrics Filters
You can use a metric filter to extract metric observations from ingested events and transfrom them into data points in a cloudwatch metrics. Metric filters are assigned to log groups and all filters assigned to a log group are applied to therir log.

In the following example, we search for status codes beginning with the number 2, so we can count successful page loads. We can achieve this more efficiently because the logs are structured using JSON, and we can define the field's name in the filter pattern.

![image](https://github.com/user-attachments/assets/7755fe74-6dfd-4bd4-938a-c6835586c02b)

### Percentile
A percentile indicates the relative standing of a value in a dataset.

For example, the ninety-fifth percentile means 95 percent of the data is lower than this value, and 5 percent is higher. **Percentiles help you understand the distribution of your metric data.**

![image](https://github.com/user-attachments/assets/e5271bf8-1f07-4006-baae-c35cc2ae90f9)

### Log Events
A log event is a **record of some activity recorded by the application or resource being monitored.** The log event record that CW logs understands containers two properties. The timestamp when the event occured and the raw event message. Event message must be UTF-8 encoded.

![image](https://github.com/user-attachments/assets/7ad72768-18c0-4fca-bffa-bb06103a3050)

### Log Stream
A log stream is a sequence of log events that share the same source. More specifially, a log stream is **generally intended to represent the sequence of events coming from the application instance or resource being monitored.**
### Log Group
A log group defines groups of logs streams that share the same retentationmonitoring and acess control settings.
### Rentention Setting
By default, log are kept indenfinitely and never expire. You can adjust the retentation policy for each log group, keeping the indefinity retentation or choosing a rentation period between 1 day and 10 years.
- You can use retention settings to specify how long you want to keep log events.
- Expired log events get deleted automatically.
- By default, logs are kept indefinitly and never expire.
