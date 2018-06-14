Monitoring Console
==================

See [Monitoring Splunk Enterprise](http://docs.splunk.com/Documentation/Splunk/7.1.1/DMC/Monitoringoverview)

Extract
-------

- Forward internal logs to the indexers, [read here](http://docs.splunk.com/Documentation/Splunk/7.1.1/DistSearch/Forwardsearchheaddata)

```
# Turn off indexing on the search head
[indexAndForward]
index = false
 
[tcpout]
defaultGroup = my_search_peers 
forwardedindex.filter.disable = true  
indexAndForward = false 
 
[tcpout:my_search_peers]
server=10.10.10.1:9997,10.10.10.2:9997,10.10.10.3:9997
```

- Setup search peers for all monitored instances, [read here](http://docs.splunk.com/Documentation/Splunk/7.1.1/DMC/Addinstancesassearchpeers)
- Configure MC in distributed mode, [read here](http://docs.splunk.com/Documentation/Splunk/7.1.1/DMC/Configureindistributedmode)
- Setup platform alerts like [this](http://docs.splunk.com/Documentation/Splunk/7.1.1/DMC/Platformalerts)
- Health checks, [read here](http://docs.splunk.com/Documentation/Splunk/7.1.1/DMC/Customizehealthcheck)
