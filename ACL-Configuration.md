**Procedures/Commands**

- Apply to L3 interfaces (Routed ports/SVI's)
     - Statements are processed sequentially with the last statement being an ``implicit deny`` which will block all traffic that does not have a permit

- Standard ACL's filter based on ``source IP address`` only, extended use ``source/dest ip address, port and protocol type/number``, both can be named

- Extended ACLs are placed as close to the ``source`` of filtered traffic as possible while standard ACL's are placed as close to ``destination ``as possible

- Configuration of standard ACL below:
     - To remove the ACL use ``no access-list <#>``
     - ``remark`` is used to add documentation to it
```
(config)# access-list <#> {deny|permit|remark} source [wildcard] [log]

\\OR\\

(config)# ip access-list standard {<#> | <name>}
(config-std-nalc)# [#] {no <#>|deny|permit|remark} source [wildcard][log]
```

- Extended ACL configuration below:
```
(config)# access-list <#> {deny|permit|remark} protocol source [wildcard] destination [wildcard] [log]

\\OR\\

(config)# ip access-list extended {<#>|<name>} [<#>{no<#>|deny|permit|remark} protocol source [wildcard] [port] destination [wildcard]
```

- Apply an interface to an ACL using ``ip acccess-group`` (use no in front to remove):
```
Router(config)# int gi0/0/0
Router(config)# ip access-group {access-list-number|access-list-name}{in|out}
```

- Secure a VTY port using ``access-clas``:
```
Router(config)# line vty 0 4
Router(config)# access-class {access-list-number}{in|out}
```

**Verification Commands**
- ``show ip interface`` can be filtered down using ``|`` to see assigned ACL's
- ``show run | sec interface`` shows standard running config for interface section only
- ``show ip access-list`` will show all configured ACL's and hit count since reboot or command reset
- ``debug ip packet <name>`` will show packets coming across that match the ACL