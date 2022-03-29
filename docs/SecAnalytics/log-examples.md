# Examples of logs

This page provides few examples of various log types and content within those logs  

## User Authentication Logs

Authentication logs have various categories, such as users logging into web apps, databases, etc. or applications logging into web services. Following shows few examples of what good logs should look like.  

### Failed Authentication

Below is a sample log from loyalty login service.  

```log
May 19 04:00:07 10.186.108.76 {"timeStamp":"2021-05-19T11:00:00.961Z","application":"aa-ct-loyalty-login-service-prod","requestType":"refresh_token","status":"FAILED","clientId":"mobile","advantageNumber":"ABC123","context":{"Device-Id":"7110BE37-1FBD-4F86-A8DF-xxxxxxxxxx","User-Agent":"iPhone/2021.05 iPhone12,1|14.5.1|414|896|2.00|AmericanAirlines","X-Cid":"","True-Client-IP":"111.111.111.111","X-Clientid":"mobile"},"errorDescription":"Refresh token expired"}
```

This shows all four components we normally need for effective security analytics.  

1. `who` is the actor?
    - This explains various aspects of user or account entities, such as account number, username, user-agent, ip address, etc.  
    - IP Address must be true client IP for us to make any effective analytics  
        - "True-Client-IP":"111.111.111.111"  
        - "advantageNumber":"ABC123"  
        - "User-Agent":"iPhone/2021.05 iPhone12,1|14.5.1|414|896|2.00|AmericanAirlines"  

2. `what` action is being performed and result of that action  
    - Action in this log is implicit - user is trying to log into the service or refreshing the existing session. It may also mean that user is not actively performing these action, however the auth token expired and as a result, user was logged out.  
        - "requestType":"refresh_token"  
        - "errorDescription":"Refresh token expired"  

3. `when` did the action take place?  
    - This timestamp should be in UTC. If it's in any other timezone, CIRE engineer will review with you during integration process so that we can configure analytics tool accordingly.  
        - "timeStamp":"2021-05-19T11:00:00.961Z"

4. `where` was the action performed?  
    - This is normally application ID or any other application specific information  
        - "application":"aa-ct-loyalty-login-service-prod"  

!!! Note
    Applications can also send various application attributes, such as Archer ID or short name, DR category, and Regulatory compliance (e.g. PCI, PII, SOX, etc.). In future, we'll have more thorough guidelines and standard templates that application team can use.  

### More examples coming...

