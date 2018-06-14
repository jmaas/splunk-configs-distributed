Universal Forwarder
===================

See the [Forwarder Manual](http://docs.splunk.com/Documentation/Forwarder/7.1.1/Forwarder/Configuretheuniversalforwarder)

Extract
-------

Setup automatic start at boot, run as `root`:
```
./splunk enable boot-start -user splunk
```

Setup deployment server:
```
./splunk set deploy-poll <host name or ip address>:<management port>
```

Setup receiving indexer:
```
./splunk add forward-server <host name or ip address>:<listening port>
```

Add input monitor:
```
./splunk add monitor /var/log/syslog
```
