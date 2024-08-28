![image](https://github.com/user-attachments/assets/43b9cefa-2bf1-4ff1-b49a-b6f8949d71e4)# AWS Observability - Altering and Insights
## Introduction to CloudWatch Logs and Contributor Insights
Amazon CloudWatch gives a unified view of operational health and visibility of your AWS resources. You can monitor applications, optimize resource utilization, and respond to performance changes.

The amount of information you can monitor can be overwhelming, and digging through log files on your own can be time-consuming. Amazon CloudWatch Logs Insights can help you automate all the work of analyzing and observing your applications, services, and logs.


![image](https://github.com/user-attachments/assets/0ae31bc7-cfdd-42c7-bbb4-4d4ebae56e8f)

The Logs Insights visualization shows the total number of exceptions occurring in each 4-minute period over a period of 14 minutes. This graph can be added to a dashboard and used to identify unexpected exceptions.

### Demonstration on using Amazon CloudWatch Logs Insights

https://github.com/user-attachments/assets/09090474-5083-4d28-bbb1-b452fac97421

## Contributor Insights

Contributor Insights analyzes time-series data to help you understand who or what is impacting your system. It analyzes application performance by pinpointing outliers, finding the heaviest traffic patterns, and ranking the top system processes. With Contributor Insights, you can more quickly isolate, diagnose, and remediate issues during operational events.

Some examples of how to use Contributor Insights in your environment include the following:
- Finding bad hosts

- Identifying the heaviest network users

- Finding the URLs that generate the most errors

### Rules
Rules define the log fields that you want to use to define contributors, such as IP address. You can filter log data to find and analyze the behavior of individual contributors.

You can build your rules from scratch or use sample rules through the AWS Management Console.


The following example identifies the partition keys of the most accessed items in an Amazon DynamoDB table. 

![image](https://github.com/user-attachments/assets/067edab7-c2b8-44b4-b670-8e125b11c71e)

Data and graph of top 10 of 99 unique contributors. The most-used partition key is clearly defined by a bar graph that has a sum of points of over 17.5k versus 3.2k or lower.

### Demonstration about how to use Contributor Insights

https://github.com/user-attachments/assets/b4c27281-3702-4a2d-b946-a8ad951519ee

## Working with Dashboards

CloudWatch dashboards are customizable home pages in the CloudWatch console. You can use dashboards to monitor your resources in a single view, even those spread across different AWS Regions.

You can use CloudWatch dashboards to create customized views of the metrics and alarms for your AWS resources.

### Dashboard options

![image](https://github.com/user-attachments/assets/2df83fa9-f949-4fc5-a801-36f854455687)

1. **Operational Playbook**
   You can use an operational playbook that provides guidance for team members during operational events about how to respond to specific incidents.
2. **Single View**
   You can use a single view for selected metrics and alarams to help you assess the health of your resources and applications across one or more regions. You can select the color for each metric on each graph to track the same matric across multiple graphs.
3. **Customized Dashboards**
   Customized dashboards display graphs and other widgets from multiple AWS accounts and regions.
4. **Common View**
   Common view proivides critical resource and application measurments that team members can share for more efficient communication flow during operational events.

The following images show example graphs collecting metrics on EC2 instances. You can add these tracked metrics to your dashboard, making metric tracking convenient for you.

![image](https://github.com/user-attachments/assets/46c1a18b-301f-4949-a42e-51480b1af7d0)

You can add a graph like this to your CloudWatch dashboard. This graph shows the percentage of used memory on EC2 instances.

![image](https://github.com/user-attachments/assets/231457e6-9ea8-458f-b960-6ec574187e6d)

You can add a graph like this to your CloudWatch dashboard. This graph shows the CPU utilization on EC2 instances.

![image](https://github.com/user-attachments/assets/01b0842a-0b92-4415-9f71-d2ab5e83810b)

You can add a graph like this to your CloudWatch dashboard. This graph shows the disk input/output (I/O) times on EC2 instances.

![image](https://github.com/user-attachments/assets/35582899-725b-404c-8688-9ddec8d83b7e)

You can add a graph like this to your CloudWatch dashboard. This graph shows the number of established TCP connections on EC2 instances.

#### Demonstration on how to create and use CloudWatch dashboards

https://github.com/user-attachments/assets/36df882e-1fa1-4c86-8213-c2089f2f6021

## Introduction to Anomaly Detection
When you activate anomaly detection for a metric, CloudWatch applies statistical and machine-learning algorithms. 

### CloudWatch algorithms perform the following functions:

- Analyze system and application metrics continuously.

- Determine normal baselines.

- Surface anomalies with minimal user intervention.
  
- Account for seasonality and trend changes in metrics.

The algorithms generate an anomaly detection model. The model generates a range of expected values that represent normal metric behavior.

The anomaly detection model created by CloudWatch **compares metrics to past data**. 

The model assesses trends and patterns of the metric and can **train on up to two weeks of data**.

After CloudWatch creates a model, anomaly detection **continually evaluates** it and makes adjustments to ensure accuracy. 

This includes **retraining the model** to adjust if metric values evolve or encounter sudden changes. Over time, the algorithms can also include **predictors to improve models** for seasonal or sparse metrics.

Without anomaly detection, you need to specify **static thresholds** for your metrics to create alarms.

Static thresholds can make it difficult to surface issues, especially if your metrics are seasonal, spike, or bottom out.

You can have long-term trends that grow or shrink. You will need to continuously adjust your thresholds if you have a growing business and use static thresholds to track metrics. 

Anomaly detection can consider this trend, **eliminating the need to make adjustments**. 

Anomaly detection is useful when you cannot **determine baselines** for your metrics in advance.

For example, even if you are unsure what to expect from a metric, anomaly detection can analyze patterns over time and provide the necessary data.

#### Demonstration on using anomaly detection

https://github.com/user-attachments/assets/46dc6f03-3833-4202-a96f-06cdea392fc5

## Using Alarms and Alerts
### CloudWatch alarms
#### Metrics Alaram
A metric alarm watches a single CloudWatch metric. The alarm performs one or more actions based on the value of the metric or math expression relative to a threshold.

Actions can include the following:

- Sending a notification to an Amazon Simple Notification Service (Amazon SNS) topic

- Performing an Amazon Elastic Compute Cloud (Amazon EC2) action

- Performing an Amazon EC2 Auto Scaling action

- Creating an incident in AWS Systems Manager

- Initiating a Systems Manager automation document or Lambda function to automatically remediate the issue

**Use metric alarms for the result of a math expression.**

#### Composite Alarams
Composite alarms include a rule expression that considers the alarm states of other alarms you create. Composite alarms only go into the ALARM state if they meet all conditions of the rule. For example, alarms specified in a composite alarm's rule expression can include metric alarms and other composite alarms.

**Use composite alarms to reduce alarm noise.**

You can add alarms to dashboards to **monitor and receive alerts** about your AWS resources and applications across multiple Regions.

### Configuring CloudWatch alarms

When you create an alarm, you specify three settings that make it possible for CloudWatch to evaluate when to change the alarm state.

#### Period
A period is the **length of time** it takes to evaluate the metric or an expression used to create each individual data point for an alarm. A period is expressed in seconds. If you choose 1 minute as the period, the alarm evaluates the metric **once per minute**.

#### Evaluation Periods
Evaluation Periods are the **number of the most recent periods**, or data points, to evaluate when determining alarm state.

#### Datapoints to Alarm

Datapoints to Alarm refers to the **number of data points within the Evaluation Periods** that must be breached to cause the alarm to go to the ALARM state. 

The breaching data points **don't need to be consecutive**, but they must all be within the last number of data points equal to the Evaluation Period.

#### It is crucial to choose your CloudWatch alarm configurations carefully. You might not want to alert on an individual error if retries are in place.

## Introduction to CloudTrail
CloudTrail is an AWS service that helps you activate operational and risk auditing, governance, and compliance of your AWS account. Actions taken by a user, role, or AWS service are recorded as events in CloudTrail. Events include actions taken in the AWS Management Console, AWS Command Line Interface (AWS CLI), and AWS SDKs and APIs.

#### Visibility into your AWS account activity is key to security and operational best practices. 

#### In the context of observability, you can configure CloudTrail with CloudWatch Logs to monitor your trail logs and receive notifications when specific activity occurs.

#### Use cases

CloudTrail can audit activity, identify security incidents, and troubleshoot operational issues.

You can use CloudWatch features, such as anomaly detection, CloudWatch Logs Insights, or Contributor Insights, to gain additional insights into your application.

#### Sending CloudTrail logs to CloudWatch Logs can help you correlate application events with AWS API activities. 
For example, an access denied error in CloudTrail can correlate with application errors due to a configuration or application change. This correlation makes understanding the root cause of the error more straightforward. For example, you can see exactly where access was denied and make the necessary changes to your application or configuration to fix the issue.

#### Demonstration on using CloudWatch to analyze CloudTrail data
https://github.com/user-attachments/assets/7dd5cca4-9be3-43c7-bba4-8700e1b8f94b






