# Synology DSM NAS Decoder.
Synology DiskStation Manager NAS and Active Backup For Business decoder and rules for Wazuh SIEM.

The ruleset contains several comments describing optional rules and how to change the current ones to your liking.

The decoder and ruleset have been tested on **Wazuh 4.7.4**.

## Installation

### Wazuh

1. Enable syslog collection via the `remote` module in `/var/ossec/etc/ossec.conf`. Example:
```xml
<remote>
  <connection>syslog</connection>
  <port>514</port>
  <protocol>udp</protocol>
  <allowed-ips>*Synology DSM IP*</allowed-ips>
  <local_ip>*Local Wazuh IP*</local_ip>
</remote>
```
2. Import `synology-dsm-decoder.xml` to `/var/ossec/etc/decoders/` **OR** create a file and copy the contents using the manager.
3. Import `synology-dsm-rules.xml` to `/var/ossec/etc/rules/` **OR** create a file and copy the contents using the manager.
4. Restart Wazuh Manager.

### Synology DSM
1. Install the **Log Center** package via the **Package Center**. 
3. Under **Log Sending**, set the destination IP and Ports to what you configured in Wazuh. Make sure to use the same protocol.
4. Set the standard to `BSD(RFC 3164)`. (This is done by default)
5. OPTIONAL: More verbose logs: Access the following: **Control Panel** -> **File Service** -> **Enable Transfer Log**. Click on **Log Settings** and choose what you want to log.

More info:
* [Log Center documentation](https://kb.synology.com/en-id/DSM/help/DSM/LogCenter/logcenter_desc?version=7)
* [Sending Syslogs via Log Center](https://kb.synology.com/en-id/DSM/help/DSM/LogCenter/logcenter_desc?version=7)

## Useful documentation

* [Wazuh Regex docs](https://documentation.wazuh.com/current/user-manual/ruleset/ruleset-xml-syntax/regex.html)
* [Wazuh Custom Decoders](https://documentation.wazuh.com/current/user-manual/ruleset/ruleset-xml-syntax/decoders.html)
* [Wazuh Custom Rules](https://documentation.wazuh.com/current/user-manual/ruleset/index.html)
