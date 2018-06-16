Deployment Server
=================

References:
- [Updating Splunk Enterprise Instances](http://docs.splunk.com/Documentation/Splunk/7.1.1/Updating/Aboutdeploymentserver)

Do NOT store configuration in `${SPLUNK_HOME}/etc/system/local`
on deployment clients. System level configurations on clients
cannot be over-ridden with Deployment Server.

Reload deployment server from CLI:
```
[splunk@splunk-mgt bin]$ ./splunk reload deploy-server
Splunk username: admin
Password: 
Reloading serverclass(es).
```

