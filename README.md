# check_fortios
nagios check for Fortinet FortiOS version

# Requirements
perl, SNMP enabled on Fortinet devices

# Configuration

Add a section similar to the following to the services.cfg file on the nagios server.

```
define service{
        use                             generic-service
        host_name                       forti1,forti2,forti3
        service_description             FortiOS
        check_command                   check_fortios!public
        }
```

Add a section similar to the following to the commands.cfg file on the nagios server.
```
# parameters are -H hostname -C snmp_community
define command{
        command_name    check_fortios
        command_line    $USER1$/check_fortios -H $HOSTADDRESS$ -c $ARG1$
        }
```


# Output

```
FortiOS WARN FortiOS 6.4 reached EOL 2024-09-30, please upgrade to a supported version.  FortiGate-100F v6.4.15,build2095,240129 (GA.M) |
FortiOS WARN FortiOS 7.2.6 is vulnerable to CVE-2024-23113, please update.  https://www.fortiguard.com/psirt/FG-IR-24-029  FortiWiFi-40F v7.2.6,build1639,240313 (GA.M) |
FortiOS OK FortiWiFi-40F v7.2.8,build1639,240313 (GA.M) |
```
