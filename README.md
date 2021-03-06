Role Name
========

mysql

Role Variables
--------------

```

# Set mysql root password
mysql_root_password:

# Login user for creating mysql users
mysql_login_user: root
# Password for above user
mysql_login_password: "{{mysql_root_password}}"
# Port to login
mysql_login_port: 3306

# MySQL my.cnf location, should be detected automatically based on distro.
mysql_my_cnf: /etc/mysql/my.cnf
# Default collation for mysql dbs, also will set in my.cnf
mysql_collation_default: utf8_unicode_ci
# Default encdoing for mysql dbs
mysql_encoding_default: utf8

# Name of pacakge to install, should be automatically filled based on distro.
# Override in your playbook if you know exactly what package you want. (e.g. mysql-server-5.6)
mysql_server_pkg: mysql-server

# Run the equivalent of mysql_secure_installation.
# Remove anonymous access, remove test db.
mysql_secure_installation: true

# Mysql my.cnf config options
# Address for mysql to bind to
mysql_bind_address: 127.0.0.1
mysql_default_storage_engine: InnoDB
mysql_max_allowed_packet: 16M

```

Example Playbook
-------------------------
### playbook.yml

```

---
- hosts: all
  roles:
   - mysql
  vars:
    mysql_root_password: password1
    mysql_users:
      test1:
        password: test1
        priv: test1.*:ALL
    mysql_dbs:
      test1:
      test2:
        encoding: latin1
        collation: latin1_swedish_ci

```

License
-------

Apache 2.0

Author Information
------------------

Ryan Yates
