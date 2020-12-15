ocp46_etcd_backup
=========

OCP ETCD Backup role performs a ETCD cluster data backup in an OpenShift 4.6 environment.

Role Variables
--------------

As is generally known, Ansible variables could be defined in different files. The following subsections include default variables and required variables which have to be defined in order to perform an ETCD cluster data backup.

### Required Vars

The following required variables have to be defined when role is triggered.

|Variable|Comment|Type|
|---|---|---|
|`backup_dst_path`|Destination ETCD backup folder path in client instance where the backup will be stored|String|


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
##
# Example:
# $ ansible-playbook -i inventory ocp46-backup-etcd.yml
# $ ansible-playbook -i inventory ocp46-backup-etcd.yml --extra-vars="backup_dst_path=/tmp"
##

- hosts: masters
  gather_facts: false
  environment:
    http_proxy: "{{ http_proxy }}"
    https_proxy: "{{ https_proxy }}"
  tasks:
    - name: Perform ETCD 4.6 Backup
      import_role:
        name: ocp46_etcd_backup
      vars:
        backup_dst_path: "~/Downloads"
      run_once: true
```

License
-------

MIT

Author Information
------------------

- Lucian Maly [@Red Hat](https://github.com/redhatofficial)
