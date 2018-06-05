
Commands:
```
[splunk@splunk-sh ~]$ /opt/splunk/bin/splunk edit licenser-localslave -master_uri https://splunk-mgt:8089
```

Configs:
```
[splunk@splunk-sh ~]$ cat /opt/splunk/etc/system/local/server.conf
[license]
master_uri = https://192.168.122.200:8089
```
