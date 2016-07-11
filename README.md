# Ansible Apache2 module

Installs Apache, configures basic vhost and enables it.

## Example

```
---

apache2_default_port: 80

apache2_vhost:
  - name: "{{ansible_hostname}}"
    vhost_name: "{{ansible_hostname}}"
    vhost_alias:
      - "{{ansible_fqdn}}"
    document_root: /var/www
    server_admin: "root@{{ansible_hostname}}"
     aliases:
       - /some-dir /opt/some-dir
     directory:
       - path: /opt/some-other-dir
         options: "-Indexes +FollowSymLinks"
         override: "All" # "None" is default
         grant_lines:
           - "Require all granted"
           - "Allow from 127.0"
     location:
       - uri: /blah
         options: "+Indexes -FollowSymLinks"
     error_log: "${APACHE_LOG_DIR}/some-name-error.log"
     access_log: "${APACHE_LOG_DIR}/some-name-access.log combined"
```

## Test

```
$ git clone https://github.com/gstlt/ansible-apache2.git
$ cd ansible-apache2
$ vagrant up
```

