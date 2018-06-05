Commands:
```
[splunk@splunk-sh bin]$ ./splunk set deploy-poll splunk-mgt:8089
Splunk username: admin
Password: 
Configuration updated.
[splunk@splunk-sh bin]$ ./splunk restart
<snip>
```

Configs:
```
[splunk@splunk-sh local]$ cat /opt/splunk/etc/system/local/deploymentclient.conf 
[target-broker:deploymentServer]
targetUri = splunk-mgt:8089
```
