# Arista VLAN replace using eos_vlans

This documentation is to support the `arista_vlan_replace.yml` Ansible Playbook. The `arista_vlan_replace.yml` Ansible Playbook can be found in the `playbooks` directory of this Ansible Collection

## Execute the Ansible Playbook

Use the `ansible-playbook` command to execute the playbook:

```
ansible-playbook arista_vlan_replace.yml
```

##  Explanation of replaced versus merge

Why would I use this versus a merge?  The major difference between a merge and a replace is that a merge just makes sure the commands are present that are represented within your data model whereas the replaced parameter will make your resource match the data model.  Let's look at the eos_vlans module to see what it considers as part of the *vlans* resource.

There are three parameters currently for the vlans resource:
name
state (active or suspend)
vlan_id (range between 1-4094)

So let's look at an example

<table>
<tr>
<td>
Data model
</td>
<td>
Existing Arista Configuration
</td>
</tr>
<tr>
<td>

```yaml
- name: desktops
 vlan_id: 200
```
</td>
<td>

```
vlan 200
   state suspend
!
```
</td>
</tr>
</table>

This is how merged will compare to replace

<table>
<tr>
<td>
merged
</td>
<td>
replaced
</td>
</tr>
<tr>
<td>

```
vlan 200
   name desktops
   state suspend
!
```
</td>
<td>

```
vlan 20,200
   name desktops
!
```
</td>
</tr>
</table>

The replaced conforms the VLAN resource to the data model whereas the merged just makes the data model configuration exists on the box.  To think of this another way, the replace parameter is aware of commands that shouldn’t be there as well as what should.
