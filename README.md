registry_container
==================

Launch a container registry with TLS and Authentication using a container

Requirements
------------

- Ansible

Role Variables
--------------

- `registry_enable_ssl` - Flag to enable ssl generation. Default: True
- `registry_enable_auth` - Flag to enable basic auth. Default: True
- `registry_manage_service` - Flag to enable systemd management. Default: True
- `registry_container_engine` - Container engine to use. Currently only podman
  is supported. Default: podman
- `registry_container_name` - Name to use for the container instance.
  Default: container-registry
- `registry_container_image` - Container image to use when launching the
  registry. Default: docker.io/library/registry:2
- `registry_path` - Path to store the container data on the host.
  Default: /opt/registry
- `registry_auth_dir` - Path to store the container auth information on the
  host. Default: "{{ registry_path }}/auth"
- `registry_auth_filename` - Filename to store the auth information in.
  Default: "htpasswd"
- `registry_auth_username` - Username to create for auth. Default: admin
- `registry_auth_password` - Password for the user to create. Default: foobar
- `registry_auth_realm` - Basic auth realm name. Default: Registry Realm
- `registry_cert_dir` - Path to store the certificate information in on the
  host. Default: "{{ registry_path }}/certs"
- `registry_cert_filename` - Filename for the certificate. Default: "domain.crt"
- `registry_cert_csr_filename` - Filename for the csr file. Default: "domain.csr"
- `registry_cert_key_filename` - Filename for the key file. Default: "domain.key"
- `registry_data_dir` - Path to store the registry images data.
  Default: "{{ registry_path }}/images"
- `registry_hostname` - Hostname to use when generating a certificate file.
  Default: "{{ ansible_hostname }}"
- `registry_listen_address` - IP to expose the port on via publish.
  Default: 0.0.0.0
- `registry_port` - Port to expose via publish. Default: 9999
- `registry_systemd_service_name` - name of the systemd service that is created.
  Default: "{{ registry_container_name }}-container"
- `registry_systemd_service_file` - Location of the systemd service file.
  Default: "/etc/systemd/system/{{ registry_systemd_service_name }}.service"

Dependencies
------------

N/A

Example Playbook
----------------

```yaml
- hosts: servers
  tasks:
     - include_role:
         name: registry_container
```

License
-------

Apache-2.0

Author Information
------------------

- Alex Schultz <aschultz@next-development.com>
