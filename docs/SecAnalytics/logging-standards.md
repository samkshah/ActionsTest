# AA Security Logging Standards

> 📝 Note: 
    **Cyber Risk and Audit Governance** team maintains logging policy and standards in Archer. Following information is taken from Archer as is. Detailed Security Log Management Standard --> [click here to view in Archer](http://aagrc.aa.com/default.aspx?requestUrl=..%2fGenericContent%2fRecord.aspx%3fid%3d7108301%26moduleId%3d544)

## Purpose  
The Security Log Management Standard identifies requirements for logging security related events, which is a critical data source for the Cyber Incident Response (CIR) Program. The Security Analytics Platform specifically supports the program by providing analysis of events to determine alerts that indicate an incident has occurred.  

## Scope

All IT Information systems that store, process, or transmit American Airlines’ data, owned, managed or administered by American or by a third party on behalf of American Airlines.

## General Requirements

System/Information Owners will coordinate with CIR to design and document appropriate security events and are responsible for ensuring events are delivered to the Security Analytics Platform. To ensure proper configuration, maintenance, and reporting; CIR must understand the following for each log source.

System Owners must notify CIR of any changes to their system which would alter event data.

- The Business or System Owner and the Application Name within that system.
- The technical contact responsible for maintaining the system.
- The hostname, the Grey (or management) IP, and the Color (or servicing) IP.
- The Operating System, DBMS and Application names and versions sending the events and the vendor providing the software (derived from the System Architecture Document).
- The type of events (OS, Application, DB or some combination) and the schema
- The location of the server (most often what data center) the log source(s) reside in.
- All new log sources must be recorded in the Enterprise asset management system.  

## Event Generation

Following are basic guidelines and minimum requirements about what systems should send security events to analytics platform, and provides high level categories of those events.  

### Basic Guidelines

- Logging will be enabled for all American information systems
- Logs will not capture regulated information
- All system clocks and times will be synced to an AA approved time source and will be configured per the below requirements
- Only designated central time server(s) will receive time signals from external sources and time signals from external sources will be based on American approved time sources
- If more than one designated time server is utilized, the time servers will peer with one another to keep accurate time
- Systems will receive time information only from designated central time server(s)
- Any modification of system times/logging settings will be restricted to the system administrator

### Requirements

All of the following systems must send security events to the SA platform

- Vital and Critical DR systems
- All systems that have regulatory requirements to log security events
- Internet facing systems
- Any systems determined by Cybersecurity to have a risk level that requires logging security events.  

Logs will capture the following activities, at a minimum.

>📝 Note:
    Detailed categorizations of below event types are in "log types" documentation here --> [click here](./log-types.md)  

- Successful and unsuccessful authentication attempts to systems or devices
- Actions taken by individuals with root or administrative privileges
- Creation and deletion of new accounts
- Elevation of access rights
- Additions, deletions, and modifications to normal or privileged accounts
- Successful and unsuccessful authentication attempts to access system logs
- Initialization, stopping, or pausing of system logs
- Enabling, disabling, and altering of system logs configuration
- Additions, deletions, and modifications to security/audit log parameters
- Creation and deletion of system-level objects (e.g., database tables, stored procedures, etc
- Unauthorized access or modification to data files, system configurations, and rule sets
- Dropped packets, successful and rejected connections established for firewalls
- Enabling, disabling, and updating protection status for IDS, IPS and anti-virus software
- System shutdown and reboot
- System application errors
- Application shutdown and restart

For each event logged, the following details will be recorded, at a minimum:

- User ID or User account  (If applicable)
- Date and time stamp
- Description of the activity performed
- Event ID or event type
- Reason for logging event (e.g., access failure / success)
- IP address and hostname of the source system
- IP address and hostname of the destination system (where applicable)
- Source and destination ports (where applicable)
- Resource accessed (URL/GET request/actual IP address accessed - as opposed to the address of the server generating the event - where applicable)
- List of commands executed by user or system
- Associated daemon process or operating system service
- Referring page (in case of HTTP access)
- Type of browser used (in case of HTTP access)
- Other information or detail that may help to recreate a sequence of events to provide information for debugging or testing purposes

>⚠ Warning:
    Administrator and operator logs will be enabled for all critical information systems (as defined by the Information Classification Policy), particularly for the information systems involved in processing of PCI and PII data. Information Classification Policy --> [Click here to view in Archer](http://aagrc.aa.com/default.aspx?requestUrl=..%2fGenericContent%2fRecord.aspx%3fid%3d7107158%26moduleId%3d65)
