```
# Example that prints the loopback address and gateway for each host
- debug:
    msg: "System {{ inventory_hostname }} has uuid {{ ansible_product_uuid }}"

- debug:
    msg: "System {{ inventory_hostname }} has gateway {{ ansible_default_ipv4.gateway }}"
  when: ansible_default_ipv4.gateway is defined

- shell: /usr/bin/uptime
  register: result

- debug:
    var: result
    verbosity: 2

- name: Display all variables/facts known for a host
  debug:
    var: hostvars[inventory_hostname]
    verbosity: 4
```