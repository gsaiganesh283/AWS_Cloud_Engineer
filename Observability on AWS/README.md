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

## AWS Systems Manager State Manager
State Manager, a capability of AWS Systems Manager State Manager, is a secure and scalable configuration management service. It automates the process of keeping your Amazon EC2 and hybrid infrastructure in a state you define. 

You can define configuration policies for your servers through the AWS Management Console or use existing scripts, AWS Tools for PowerShell, or Ansible playbooks directly from GitHub or Amazon Simple Storage Service (Amazon S3) buckets. 

With Systems Manager, you can control configuration details, such as server configurations, antivirus definitions, firewall settings, and more. 

Systems Manager automatically applies your configurations across your instances at a defined time and frequency. 

You can query Systems Manager at any time to view the status of your instance configurations, giving you on-demand visibility into your compliance status.

### What is AWS Systems Manager?
AWS Systems Manager is the operations hub for your AWS applications and resources and a secure end-to-end management solution for hybrid and multicloud environments that enables secure operations at scale.

#### How Systems Manager works

- **Access Systems Manager** – Use one of the available options for accessing Systems Manager.
- **Choose a Systems Manager capability** – Determine which capability can help you perform the action you want to perform on your resources. The diagram shows only a few of the capabilities that IT administrators and DevOps personnel use to manage their applications and resources.
- **Verification and processing** – Systems Manager verifies that your user, group, or role has the required AWS Identity and Access Management (IAM) permissions to perform the action you specified. If the target of your action is a managed node, the Systems Manager Agent (SSM Agent) running on the node performs the action. For other types of resources, Systems Manager performs the specified action or communicates with other AWS services to perform the action on behalf of Systems Manager.
- **Reporting** – Systems Manager, SSM Agent, and other AWS services that performed an action on behalf of Systems Manager report status. Systems Manager can send status details to other AWS services, if configured.
- **Systems Manager operations management capabilities** – If enabled, Systems Manager operations management capabilities such as Explorer, OpsCenter, and Incident Manager aggregate operations data or create artifacts in response to events or errors with your resources. These artifacts include operational work items (OpsItems) and incidents. Systems Manager operations management capabilities provide operational insight into your applications and resources and automated remediation solutions to help troubleshoot problems.

![image](https://github.com/user-attachments/assets/c12e73ba-7c9b-4f57-b1ca-460ae9de28da)
### Systems Manager capabilities
Systems Manager groups capabilities into the following categories. Choose the tabs under each category to learn more about each capability.
#### Application management
Application Manager helps DevOps engineers investigate and remediate issues with their AWS resources in the context of their applications and clusters. In Application Manager, an application is a logical group of AWS resources that you want to operate as a unit. This logical group can represent different versions of an application, ownership boundaries for operators, or developer environments, to name a few. Application Manager support for container clusters includes both Amazon Elastic Kubernetes Service (Amazon EKS) and Amazon Elastic Container Service (Amazon ECS) clusters. Application Manager aggregates operations information from multiple AWS services and Systems Manager capabilities to a single AWS Management Console.

AppConfig helps you create, manage, and deploy application configurations and feature flags. AppConfig supports controlled deployments to applications of any size. You can use AppConfig with applications hosted on Amazon EC2 instances, AWS Lambda containers, mobile applications, or edge devices. To prevent errors when deploying application configurations, AppConfig includes validators. A validator provides a syntactic or semantic check to verify that the configuration you want to deploy works as intended. During a configuration deployment, AppConfig monitors the application to verify that the deployment is successful. If the system encounters an error or if the deployment invokes an alarm, AppConfig rolls back the change to minimize impact for your application users.

Parameter Store provides secure, hierarchical storage for configuration data and secrets management. You can store data such as passwords, database strings, Amazon Elastic Compute Cloud (Amazon EC2) instance IDs and Amazon Machine Image (AMI) IDs, and license codes as parameter values. You can store values as plain text or encrypted data. You can then reference values by using the unique name you specified when you created the parameter.

#### Change management

Change Manager is an enterprise change management framework for requesting, approving, implementing, and reporting on operational changes to your application configuration and infrastructure. From a single delegated administrator account, if you use AWS Organizations, you can manage changes across multiple AWS accounts in multiple AWS Regions. Alternatively, using a local account, you can manage changes for a single AWS account. Use Change Manager for managing changes to both AWS resources and on-premises resources.

Use Automation to automate common maintenance and deployment tasks. You can use Automation to create and update Amazon Machine Images (AMIs), apply driver and agent updates, reset passwords on Windows Server instance, reset SSH keys on Linux instances, and apply OS patches or application updates.

Change Calendar helps you set up date and time ranges when actions you specify (for example, in Systems Manager Automation runbooks) can or can't be performed in your AWS account. In Change Calendar, these ranges are called events. When you create a Change Calendar entry, you're creating a Systems Manager document of the type ChangeCalendar. In Change Calendar, the document stores iCalendar 2.0 data in plaintext format. Events that you add to the Change Calendar entry become part of the document. You can add events manually in the Change Calendar interface or import events from a supported third-party calendar using an .ics file.

Use Maintenance Windows to set up recurring schedules for managed instances to run administrative tasks such as installing patches and updates without interrupting business-critical operations.

#### Node management
A managed node is any machine configured for use with Systems Manager in hybrid and multicloud environments.

Use Compliance to scan your fleet of managed nodes for patch compliance and configuration inconsistencies. You can collect and aggregate data from multiple AWS accounts and AWS Regions, and then drill down into specific resources that aren’t compliant. By default, Compliance displays compliance data about Patch Manager patching and State Manager associations. You can also customize the service and create your own compliance types based on your IT or business requirements.

Fleet Manager is a unified user interface (UI) experience that helps you remotely manage your nodes. With Fleet Manager, you can view the health and performance status of your entire fleet from one console. You can also gather data from individual devices and instances to perform common troubleshooting and management tasks from the console. This includes viewing directory and file contents, Windows registry management, operating system user management, and more.

Inventory automates the process of collecting software inventory from your managed nodes. You can use Inventory to gather metadata about applications, files, components, patches, and more.

Use Session Manager to manage your edge devices and Amazon Elastic Compute Cloud (Amazon EC2) instances through an interactive one-click browser-based shell or through the AWS CLI. Session Manager provides secure and auditable edge device and instance management without needing to open inbound ports, maintain bastion hosts, or manage SSH keys. Session Manager also allows you to comply with corporate policies that require controlled access to edge devices and instances, strict security practices, and fully auditable logs with edge device and instance access details, while still providing end users with simple one-click cross-platform access to your edge devices and EC2 instances. To use Session Manager, you must enable the advanced-instances tier. For more information, see Turning on the advanced-instances tier.

Use Run Command to remotely and securely manage the configuration of your managed nodes at scale. Use Run Command to perform on-demand changes such as updating applications or running Linux shell scripts and Windows PowerShell commands on a target set of dozens or hundreds of managed nodes.

#### Operations management

Incident Manager is an incident management console that helps users mitigate and recover from incidents affecting their AWS hosted applications.

Incident Manager increases incident resolution by notifying responders of impact, highlighting relevant troubleshooting data, and providing collaboration tools to get services back up and running. Incident Manager also automates response plans and allows responder team escalation.

Explorer is a customizable operations dashboard that reports information about your AWS resources. Explorer displays an aggregated view of operations data (OpsData) for your AWS accounts and across AWS Regions. In Explorer, OpsData includes metadata about your Amazon EC2 instances, patch compliance details, and operational work items (OpsItems). Explorer provides context about how OpsItems are distributed across your business units or applications, how they trend over time, and how they vary by category. You can group and filter information in Explorer to focus on items that are relevant to you and that require action. When you identify high priority issues, you can use OpsCenter, a capability of Systems Manager, to run Automation runbooks and resolve those issues.

OpsCenter provides a central location where operations engineers and IT professionals can view, investigate, and resolve operational work items (OpsItems) related to AWS resources. OpsCenter is designed to reduce mean time to resolution for issues impacting AWS resources. This Systems Manager capability aggregates and standardizes OpsItems across services while providing contextual investigation data about each OpsItem, related OpsItems, and related resources. OpsCenter also provides Systems Manager Automation runbooks that you can use to resolve issues. You can specify searchable, custom data for each OpsItem. You can also view automatically generated summary reports about OpsItems by status and source.

Amazon CloudWatch Dashboards are customizable pages in the CloudWatch console that you can use to monitor your resources in a single view, even those resources that are spread across different regions. You can use CloudWatch dashboards to create customized views of the metrics and alarms for your AWS resources.

### Accessing Systems Manager

#### Systems Manager console
The [Systems Manager console](https://console.aws.amazon.com/systems-manager/) is a browser-based interface to access and use Systems Manager.
#### AWS IoT Greengrass V2 console
You can view and manage edge devices that are configured for AWS IoT Greengrass in the [Greengrass console](https://console.aws.amazon.com/iot).
#### AWS command line tools
By using the AWS command line tools, you can issue commands at your system's command line to perform Systems Manager and other AWS tasks. The tools are supported on Linux, macOS, and Windows. Using the AWS Command Line Interface (AWS CLI) can be faster and more convenient than using the console. The command line tools also are useful if you want to build scripts that perform AWS tasks.

AWS provides two sets of command line tools: the [AWS Command Line Interface](https://aws.amazon.com/cli/) and the [AWS Tools for Windows PowerShell](https://aws.amazon.com/powershell/). For information about installing and using the AWS CLI, see the [AWS Command Line Interface User Guide](https://docs.aws.amazon.com/cli/latest/userguide/). For information about installing and using the Tools for Windows PowerShell, see the [AWS Tools for Windows PowerShell User Guide](https://docs.aws.amazon.com/powershell/latest/userguide/).

#### AWS SDKs
AWS provides software development kits (SDKs) that consist of libraries and sample code for various programming languages and platforms (for example, [Java](https://aws.amazon.com/sdk-for-java/), [Python](https://aws.amazon.com/sdk-for-python/), [Ruby](https://aws.amazon.com/sdk-for-ruby/), [.NET](https://aws.amazon.com/sdk-for-net/), [iOS and Android](https://aws.amazon.com/mobile/resources/), and [others](https://aws.amazon.com/tools/#sdk). The SDKs provide a convenient way to grant programmatic access to Systems Manager. For information about the AWS SDKs, including how to download and install them, see [Tools for Amazon Web Services](https://aws.amazon.com/tools/#sdk).

#### Systems Manager service name history

AWS Systems Manager (Systems Manager) was formerly known as "Amazon Simple Systems Manager (SSM)" and "Amazon EC2 Systems Manager (SSM)". The original abbreviated name of the service, "SSM", is still reflected in various AWS resources, including a few other service consoles. Some examples:

- **Systems Manager Agent:** SSM Agent

- **Systems Manager parameters:** SSM parameters

- **Systems Manager service endpoints:** ssm.region.amazonaws.com

- **AWS CloudFormation resource types:** AWS::SSM::Document

- **AWS Config rule identifier:** EC2_INSTANCE_MANAGED_BY_SSM

- **AWS Command Line Interface (AWS CLI) commands:** aws ssm describe-patch-baselines

- **AWS Identity and Access Management (IAM) managed policy names:** AmazonSSMReadOnlyAccess

- **Systems Manager resource ARNs:** arn:aws:ssm:region:account-id:patchbaseline/pb-07d8884178EXAMPLE

### What is AWS State Manager?
State Manager, a capability of AWS Systems Manager, is a secure and scalable configuration management service that automates the process of keeping your managed nodes and other AWS resources in a state that you define. To get started with State Manager, open the [Systems Manager console](https://console.aws.amazon.com/systems-manager/state-manager). In the navigation pane, choose State Manager.

#### How can State Manager benefit my organization?

By using pre-configured Systems Manager documents (SSM documents), State Manager offers the following benefits for managing your nodes:

- Bootstrap nodes with specific software at start-up.

- Download and update agents on a defined schedule, including the SSM Agent.

- Configure network settings.

- Join nodes to a Microsoft Active Directory domain.

- Run scripts on Linux, macOS, and Windows managed nodes throughout their lifecycle.

To manage configuration drift across other AWS resources, you can use Automation, a capability of Systems Manager, with State Manager to perform the following types of tasks:

- Attach a Systems Manager role to Amazon Elastic Compute Cloud (Amazon EC2) instances to make them managed nodes.

- Enforce desired ingress and egress rules for a security group.

- Create or delete Amazon DynamoDB backups.

- Create or delete Amazon Elastic Block Store (Amazon EBS) snapshots.

- Turn off read and write permissions on Amazon Simple Storage Service (Amazon S3) buckets.

- Start, restart, or stop managed nodes and Amazon Relational Database Service (Amazon RDS) instances.

- Apply patches to Linux, macOS, and Window AMIs.

#### Who should use State Manager?

State Manager is appropriate for any AWS customer that wants to improve the management and governance of their AWS resources and reduce configuration drift.

#### What are the features of State Manager?

- **State Manager associations**
A State Manager association is a configuration that you assign to your AWS resources. The configuration defines the state that you want to maintain on your resources. For example, an association can specify that antivirus software must be installed and running on a managed node, or that certain ports must be closed.

An association specifies a schedule for when to apply the configuration and the targets for the association. For example, an association for antivirus software might run once a day on all managed nodes in an AWS account. If the software isn't installed on a node, then the association could instruct State Manager to install it. If the software is installed, but the service isn't running, then the association could instruct State Manager to start the service.

- **Flexible scheduling options**
State Manager offers the following options for scheduling when an association runs:

  - **Immediate or delayed processing**

    When you create an association, by default, the system immediately runs it on the specified resources. After the initial run, the association runs in       intervals according to the schedule that you defined.

    You can instruct State Manager not to run an association immediately by using the** Apply association only at the next specified Cron interval** option 
    in the console or the ApplyOnlyAtCronInterval parameter from the command line.

    - **Cron and rate expressions**

    When you create an association, you specify a schedule for when State Manager applies the configuration. State Manager supports most standard cron and      rate expressions for scheduling when an association runs. State Manager also supports cron expressions that include a day of the week and the number        sign (#) to designate the nth day of a month to run an association and the (L) sign to indicate the last X day of the month.

    To further control when an association runs, for example if you want to run an association two days after patch Tuesday, you can specify an offset. An      offset defines how many days to wait after the scheduled day to run an association.
- **Multiple targeting options**
An association also specifies the targets for the association. State Manager supports targeting AWS resources by using tags, AWS Resource Groups, individual node IDs, or all managed nodes in the current AWS Region and AWS account.
- **Amazon S3 support**
Store the command output from association runs in an Amazon S3 bucket of your choice.
- **EventBridge support**
This Systems Manager capability is supported as both an event type and a target type in Amazon EventBridge rules.

#### How do I get started with State Manager?

|Task|For More Information|
|---|---|
|Set up Systems Manager|[Setting up AWS Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-setting-up.html)|
|Learn more about State Manager|[About State Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/state-manager-about.html)|
|Create and assign a State Manager association to your nodes|[Working with associations in Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/state-manager-associations.html)|



