# tedge-benchmark

## Plugin summary

Benchmarking script which is run periodically using a systemd timer.

**Technical summary**

The following details the technical aspects of the plugin to get an idea what systems it supports.

|||
|--|--|
|**Languages**|`python3`|
|**CPU Architectures**|`all/noarch`. Not CPU specific|
|**Supported init systems**|`systemd`|
|**Required Dependencies**|python3-paho-mqtt|
|**Optional Dependencies (feature specific)**|-|

### How to do I get it?

The following linux package formats are provided on the releases page and also in the [tedge-community](https://cloudsmith.io/~thinedge/repos/community/packages/) repository:

|Operating System|Repository link|
|--|--|
|Debian/Raspbian (deb)|[![Latest version of 'tedge-benchmark' @ Cloudsmith](https://api-prd.cloudsmith.io/v1/badges/version/thinedge/community/deb/tedge-benchmark/latest/a=all;d=any-distro%252Fany-version;t=binary/?render=true&show_latest=true)](https://cloudsmith.io/~thinedge/repos/community/packages/detail/deb/tedge-benchmark/latest/a=all;d=any-distro%252Fany-version;t=binary/)|
|Alpine Linux (apk)|[![Latest version of 'tedge-benchmark' @ Cloudsmith](https://api-prd.cloudsmith.io/v1/badges/version/thinedge/community/alpine/tedge-benchmark/latest/a=noarch;d=alpine%252Fany-version/?render=true&show_latest=true)](https://cloudsmith.io/~thinedge/repos/community/packages/detail/alpine/tedge-benchmark/latest/a=noarch;d=alpine%252Fany-version/)|
|RHEL/CentOS/Fedora (rpm)|[![Latest version of 'tedge-benchmark' @ Cloudsmith](https://api-prd.cloudsmith.io/v1/badges/version/thinedge/community/rpm/tedge-benchmark/latest/a=noarch;d=any-distro%252Fany-version;t=binary/?render=true&show_latest=true)](https://cloudsmith.io/~thinedge/repos/community/packages/detail/rpm/tedge-benchmark/latest/a=noarch;d=any-distro%252Fany-version;t=binary/)|

### What will be deployed to the device?

* The following service will be installed
    * `tedge-benchmark` (service and timer) (triggered every hour on the hour)
    * `tedge-benchmark.py` script which is called from the service, however it can also be called manually for adhoc usage

## Plugin Dependencies

The following packages are required to use the plugin:

* tedge


### Check the timer status

You can check on the status of the timer by running:

```sh
systemctl status tedge-benchmark.timer
```

**Output**

```sh
● tedge-benchmark.timer - thin-edge.io benchmark runner
     Loaded: loaded (/etc/systemd/system/tedge-benchmark.timer; enabled; preset: enabled)
     Active: active (waiting) since Wed 2023-12-06 21:54:28 CET; 48s ago
    Trigger: Wed 2023-12-06 22:00:00 CET; 4min 42s left
   Triggers: ● tedge-benchmark.service

Dec 06 21:54:28 rackfslot1 systemd[1]: Started tedge-benchmark.timer - thin-edge.io benchmark runner.
```

### Check log output

Check the results of the benchmark using:

```sh
tail -f /var/log/tedge-benchmark.log
```
