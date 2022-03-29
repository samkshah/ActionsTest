# Log Types and Content

This page provides information about what types of logs should be captured from various systems and applications.  

## Events vs. Alerts

A cybersecurity **event** is an event of interest signifying interaction with our systems, processes, environments, or workflows which can result in positive or negative impact to our organization.

An **alert** is a notification of a malicious cybersecurity event(s), resulting in incident response. **Events** are informative while **Alerts** are actionable. 

Our Security Analytics platform (SA) solution (Securonix) uses various detections and threat models, a sequence of detected activity, to identify policy violations and potential threats. When a violation or potential threat is recognized, the SA platform then ties the event back to the entity from which the violations originated.

## Log Content

At a minimum, logs should contain the following information. Overall content and format may defer for each system, platform, or application.  

1. **Who**: Actor - Who performed the activity, such as user account, service account, email address, full name, user name, or any HR identifiable attribute that helps to understand who performed this activity. Also Unique Device Identifier, Session Identifier, Unique Access Code (UAC), etc. will be required where applicable.​  
2. **What**: Activity - What was the activity and the outcome, such as login attempt with success or failed, protected documents or configurations accessed / deleted / modified / etc.​  
3. **When**: Timestamp - When was the activity performed? This must include date and time.  
4. **Where**: IP address -  Origin and destination address. Where the activity originated from and where it was sent are very important in investigations.

*Additional requirements for PCI / HIPAA applications:*

1. Audit Logs 
     - Access requests on PCI/HIPAA relevant data set
2. Transactional Security Logs
     - Activities performed on PCI/HIPAA data
         - Example: Deletion and updating records

*Following logs are also helpful from business facing applications​:*

   1. ​Audit Logs
     - Activities performed on customer entities 
        - Example: Changes performed by AA res agents to customer bookings​
   2. Transactional Security Logs
     - Customer or employee facing transactional logs 
        - Example: PNR bookings, itinerary related information, boarding pass scanning, customer logins to mobile and web apps, etc.​  

!!! warning "Note"
    Sensitive PCI and PII data such as full payment card numbers, authorization codes, birth dates, etc. must not be logged within security events.  

## Scope and Log Types

### Operating System Security Logs

If applications have 3 tier model, where they have traditional VMs in Data Center(s) or in cloud IaaS environments, following types of audit logs are in scope at a minimum. All these logs must have descriptions, error codes, reason of failures, etc. in as much details as possible.

- Windows / Unix Audit logs​
- Login Success / Failures​
- Privileged Access / Escalation Logs​
- Remote access logs
- Activity logs for privileged users​
- Account level auditing (e.g. Create, Update, Delete) for sensitive accounts​

### Database / Data Lake Security Logs

- Audit Logs:
    - Login Success / Failures​
    - Privileged Access / Escalation Logs​
    - SA accounts access and activity​
    - Access logs for critical tables / columns, example: user accessing “PCI or HIPAA sensitive data” in bulk​
    - Account level auditing (e.g. Create, Update, Delete) for database accounts​  
- Transactional Security Logs:
    - Access to sensitive records, such as employee and customer PII data

### Infrastructure Devices Security Logs

- Audit Logs
    - Access and activity logs for application/platform owners​
- Transactional Security Logs:
    - Traffic passing through network devices, such as traffic that was allowed or denied​

### Cloud Security Logs

  - Cloud Platform Audit Logs
     - All activity performed by developers or application administrators in cloud platform, such as IBM cloud portal or Azure portal​
     - These are CRUD (Create, Read, Update and Delete) records around cloud resources, such as subscriptions, resource groups, virtual machines, keys, global policies, etc.
     - Cloud platform authentication and authorization logs​
     - Privileged escalation at the cloud platform level​
     - Console logins, such as IBM CLI or Azure CLI​
  - Cloud Service Audit Logs
    - These are CRUD records around cloud services, such as functions, key vaults, storage accounts, AKS (Azure Kubernetes Service), IKS (IBM Kubernetes Service), ADX (Azure Data Explorer), etc.
  - SaaS Applications Audit Logs
    - These are CRUD records for applications hosted in external cloud environments, or 3rd party apps, such as o365, Akamai, Outlook, Orion Data lake, etc.

### Application Security Logs

For applications audit logs, following at-a-minimum is in scope. This applies to all applications irrespective of where they are hosted or type of applications.

- Audit Logs:
    - Application critical errors /audit Logs​
    - Login Success / Failures​
    - Privileged Access / Escalations Logs​
    - Activity logs for privileged users​
    - Security alerts / notifications relevant to applications​
    - Account level auditing (e.g. Create, Update, Delete) for sensitive accounts​
    - Application mis-use logs​
- Transactional Security Logs:
    - Application consumer connectivity
         1. Users or applications connecting to web services or other applications 
         2. User's actions within the application