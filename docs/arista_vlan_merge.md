# Arista VLAN merge using eos_vlans

This documentation is to support the `arista_vlan_merge.yml` Ansible Playbook. The `arista_vlan_merge.yml` Ansible Playbook can be found in the `playbooks` directory of this Ansible Collection.

## Execute the Ansible Playbook

Use the `ansible-playbook` command to execute the playbook:

```
ansible-playbook arista_vlan_merge.yml
```

## Verifying Ansible Playbook

The show vlan output on a greenfield Arista switch will look like this:

```
rtr2#show vlan
VLAN  Name                             Status    Ports
----- -------------------------------- --------- -------------------------------
1     default                          active
20    desktops                         active
30    servers                          active
40    printers                         active
50    DMZ                              active
```

while the running configuration will look this:

```
rtr2#show running-config | s vlan
vlan 20
   name desktops
!
vlan 30
   name servers
!
vlan 40
   name printers
!
vlan 50
   name DMZ
```
