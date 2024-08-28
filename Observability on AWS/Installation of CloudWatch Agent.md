# Install and start the CloudWatch agent

1. Create a State Manager association that downloads and installs the CloudWatch agent to targets you choose during configuration.
2. Target instances by their tags. For example, you can choose instances manually, choose a resource group, or choose all instances as your target.
3. Download and installation the AmazonCloudWatchAgent package. Use a Systems Manager automation document called AWS-Configure AWS Package.
4. Track installation progress and review the compliance status of your targets. Any instances that do successfully install the CloudWatch agent report as noncompliant.

![image](https://github.com/user-attachments/assets/bbc17c57-e29d-42ed-9ed9-26d54b6093b2)


**Step-1:** State Manager association

**Step-2:** Target Instances

**Step-3:** AWS-Configure AWS Package

**Step-4:** Report Compliance

## Installation of the CloudWatch agent demonstration 
https://github.com/user-attachments/assets/4bee1fa1-b9c8-460b-998e-45d8f60fdb7c
