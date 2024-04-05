**Useful links**

https://j2live.ttl255.com/

**Procedures/Commands**

- Files end with ``.j2`` file extension
- With the default syntax, control structures appear inside {% ... %} blocks
```jinja
{% if condition %} 
      do_some_thing 
{% elif condition2 %} 
      do_another_thing 
{% else %}
       do_something_else 
{% endif %}
```
- A macro is defined inside a ``{% macro … %} … {% endmacro %}`` block and has a name and can take zero or more arguments. Code within a macro does not inherit the namespace of the block calling the macro, so all arguments must be explicitly passed in
- Can build ``for`` loops:
```jinja
{% for interface in interfaces %}
interface {{ interface.name }} {{ interface.state }}
!
{% endfor %}
```
- You can also filter loop items:
```jinja
{% for interface in interfaces %}
interface {{ interface.name }} 
  {{ 'no shutdown' if interface.state == 'enabled' else 'shutdown' }}
!
{% endfor %}
```
- Can cycle among a list each time through a loop by using the ``loop.cycle`` helper:
```jinja
{% for row in rows %}
    <li class="{{ loop.cycle('odd', 'even') }}">{{ row }}</li>
{% endfor %}
```
![jinja_helpers](uploads/5c87579c6ba3b7069e0d8e1391881e9e/jinja_helpers.png)
- Data can be manipulated through small functions and methods, such as:
  - ``{{ my_word | lower }}``
  - ``{{ answers | replace('no', 'yes') }}``
  - ``{{ answers | replace('no', 'yes') | lower }}``
- Basic template delimiters are below:
  - ``{% ... %}`` for Statements
  - ``{{...}}`` for Expressions to print to the template output
  - ``{#...#}`` for Comments not included in output
  - ``#...##`` for Line statements
- Data, Template, Output Relationship shown below:
```jinja
#DATA
hostname: lab8-red-router
name_servers_pri : 1.1.1.1
name_servers_sec :  8.8.8.8

#TEMPLATE
hostname {{ hostname }}
no ip domain lookup
ip domain name local.lab
ip name-server {{ name_servers_pri }}
ip name-server {{ name_servers_sec }}

#OUTPUT
hostname lab8-red-router 
no ip domain lookup 
ip domain name lab8-local
ip name-server 1.1.1.1 
ip name-server 8.8.8.8 
```
- Variables can be modified by filters, separated using the ``|`` symbol, such as ``vlans | map(attribute="name") | list``

![jinja_filters](uploads/91d971e0332a67a20a2799844776b8c1/jinja_filters.png)

- Use ``|default('...')`` at the end of a variable in the template to set a value if none provided
```jinja
{% for interface in interfaces %}
interface {{ interface.name }}
  {{ 'no shutdown' if interface.state == 'enabled' else 'shutdown' }}
  description {{ interface.description | default('no_description') }}
!
{% endfor %}
```
- To set up a basic dhcp template use:
```jinja
{% for address in dhcp.excluded %}
ip dhcp excluded-address {{ address }}
{% endfor %}
!
{% for pool in dhcp.pools %}
ip dhcp pool {{ pool.name | upper }}
  network {{ pool.network }}
  default-router {{ pool.default_router }}
{% endfor %}
```
- To check for a state parameter:
```jinja
{% for vlan in vlans %}
{% if vlan.state == "present" %}
vlan {{ vlan.id }}
{% if vlan.get('name') %}
  name {{ vlan.name }}
{% endif %}
{% elif vlan.state == "absent" %}
no vlan {{ vlan.id }}
{% endif %}
{% endfor %}
```