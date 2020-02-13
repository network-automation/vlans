# Arista VLAN overridden using eos_vlans

This documentation is to support the `arista_vlan_overridden.yml` Ansible Playbook. The `arista_vlan_overridden.yml` Ansible Playbook can be found in the `playbooks` directory of this Ansible Collection.

## Execute the Ansible Playbook

Use the `ansible-playbook` command to execute the playbook:

```
ansible-playbook arista_vlan_overridden.yml
```

## Overridden versus merge and replaced

The overridden parameter will conform all vlans resources to the data model.  This means it will remove VLANs that are not defined in the data model being sent.
