MySQL
=========

Ansible role for MySQL cluster installation & configuration.


Requirements
------------

 - Ansible community.mysql module

Name of master in inventory file:

inventory_hostname == "db01"

Name of slave in inventory file:

inventory_hostname == "db02"


Role Variables
--------------

| Name | Description | Type | Default Value|
|------|-------------|------|---------|
| ***defaults/main.yml*** |
| arch | architecture  | string | linux-amd64 |
| cnf_path | path to config files | string | /etc |
| tmp_path | temporary path  | string | /tmp |
| bin_path | path to binary  | string | /usr/local/bin |
| script | script gets temporary root password | string | {{ tmp_path }}/script.sh |
| root_password | mysql root password | string | CHANGEME |
| node_exporter_version | prometheus node exporter version | string | 1.3.1 |
| node_exporter_archive | downloaded archive | string | {{ tmp_path }}/node_exporter-{{ node_exporter_version }}.{{ arch }}.tar.gz |
| node_exporter_path_tmp | temporary path | string | {{ tmp_path }}/node_exporter-{{ node_exporter_version }}.{{ arch }} |
| systemd_path | systemd unit file path | string | /etc/systemd/system |
| ***vars/yum.yml*** |
| md5 | md5 check sum string | string | 62f64deae31dcc2399a0ebe05366498f |
| repo_url | mysql repository url | string | https://dev.mysql.com/get/mysql80-community-release-el7-6.noarch.rpm |
| rpm_path | path to repositories directory | string | /tmp/mysql80-community-release-el7-6.noarch.rpm |
| gpg_url | gpg key url | string | https://repo.mysql.com/RPM-GPG-KEY-mysql-2022 |
| ***vars/mysql_master.yml, vars/mysql_slave.yml*** | 
| log_path | mysql log path | string | /var/log/mysql |
| user | mysql user | string | mysql |
| replica_user | mysql replication user | string | CHANGEME |
| replica_pass | mysql replication user password | string | CHANGEME |
| replica_host | mysql ip address slave host | string | CHANGEME |
| primary_host | mysql ip address master host | string | CHANGEME |
| ***vars/mysql_wordpress.yml*** |
| db_name | wordpress database name | string | CHANGEME |
| db_username | wordpress database username | string | CHANGEME |
| db_password | wordpress database password | string | CHANGEME |
| db_host | webserver ip address | string | CHANGEME |
| ***vars/mysqld_exporter.yml*** |
| mysqld_exporter_version | mysqld exporter version | string | 0.14.0 |
| mysqld_exporter_archive | downloaded archive | string | {{ tmp_path }}/mysqld_exporter-{{ mysqld_exporter_version }}.{{ arch }}.tar.gz |
| mysqld_exporter_path_tmp | temporary path | string | {{ tmp_path }}/mysqld_exporter-{{ mysqld_exporter_version }}.{{ arch }} |
| mysql_user | mysql user for mysqld exporter | string | CHANGEME |
| mysql_pass | mysql password for mysqld exporter user | string | CHANGEME |
| ***vars/mysql_grafana.yml***|
| grafana_user | database user for grafana wordpress stats | string | CHANGEME |
| grafana_pass | database user password | string | CHANGEME |
| remote_host | ip address of remote grafana host | string | CHANGEME |


Example Playbook
----------------

An example of using role:

```yaml
- name: MySQL Provisioning
  hosts: mysql
  roles:
    - Mysql-role
```


License
-------

BSD-3-Clause


Author Information
------------------

Borodatko
