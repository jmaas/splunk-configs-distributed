
This repository contains several basic configuration files required
by recent Splunk versions for EL7 (RHEL/CentOS/etc).

I've created this repository to provide a simple baseline as a preparation
for the Splunk Certified Architect 1 exam.


Install:
- copy `systemd/disable-thp.service` over to `/etc/systemd/system/`
- copy `systemd/splunkd.service` over to `/etc/systemd/system/`
- copy `splunk/etc/splunk-launch.conf` over to `/opt/splunk/etc/`
- make sure you don't `enable boot-start`, just to be sure: `rm -f /etc/init.d/splunk`
- reload systemd unit files from disk: `systemctl daemon-reload`
- enable the disable-thp service: `systemctl enable disable-thp.service`
- enable the splunkd service: `systemctl enable splunkd.service`

Verify that THP is disabled:
```
[splunk@splunk-mgt ~]$ cat /sys/kernel/mm/transparent_hugepage/defrag
always madvise [never]
[splunk@splunk-mgt ~]$ cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]
```

Verify that Splunk is not complaining about ulimits:
```
[splunk@splunk-mgt ~]$ grep limit /opt/splunk/var/log/splunk/splunkd.log | tail -n 12
06-05-2018 19:44:01.122 +0200 INFO  ulimit - Limit: virtual address space size: unlimited
06-05-2018 19:44:01.122 +0200 INFO  ulimit - Limit: data segment size: unlimited
06-05-2018 19:44:01.122 +0200 INFO  ulimit - Limit: resident memory size: unlimited
06-05-2018 19:44:01.122 +0200 INFO  ulimit - Limit: stack size: 8388608 bytes [hard maximum: unlimited]
06-05-2018 19:44:01.122 +0200 INFO  ulimit - Limit: core file size: 0 bytes [hard maximum: unlimited]
06-05-2018 19:44:01.122 +0200 WARN  ulimit - Core file generation disabled.
06-05-2018 19:44:01.122 +0200 INFO  ulimit - Limit: data file size: unlimited
06-05-2018 19:44:01.122 +0200 INFO  ulimit - Limit: open files: 64000 files
06-05-2018 19:44:01.122 +0200 INFO  ulimit - Limit: user processes: 16000 processes
06-05-2018 19:44:01.122 +0200 INFO  ulimit - Limit: cpu time: unlimited
06-05-2018 19:44:01.122 +0200 INFO  ulimit - Linux transparent hugepage support, enabled="never" defrag="never"
06-05-2018 19:44:01.122 +0200 INFO  ulimit - Linux vm.overcommit setting, value="0"
```

Deployment apps:
- `cfg_indexers`: deployment client, license master, inputs, volumes and indexes 
- `cfg_search-heads`: deployment client, license master, outputs, distsearch
- `cfg_license-server`: deployment client, outputs
- `cfg_monitoring-console`: deployment client, license master, outputs
- `cfg_deployment-server`: license master, outputs

Configuration specifications & examples:
- `configs/*.spec`
- `configs/*.example`

