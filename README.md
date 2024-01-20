# Anisble playbook docker registry

The Ansible playbook installs and configures docker registry with native basic authentication and secures it using TLS.

## Parameters

* `{{ htpasswd_file }}` - local path of the authentication file
* `{{ tls_certificate_file }}` - local path of the ssl certificate file
* `{{ tls_key_file }}` -local path of the ssl key file

## Example of an inventory file

`hosts` file:

```ini
[all]
10.5.0.221 htpasswd_file=/home/test/htpasswd tls_certificate_file=/home/test/repocert.pem  tls_key_file=/home/test/repokey.pem
```

## Install docker registry

```shell
$ ansible-playbook -i hosts docker-registry.yml
```

The ansible playbook:
* creates `/opt/docker-registry/` directory
* uploads htpasswd file to `/opt/docker-registry/auth/htpasswd`
* uploads ssl certificate to `/opt/docker-registry/certs/domain.crt`
* uploads ssl key to `/opt/docker-registry/certs/domain.key`
* creates `/opt/docker-registry/registry/` directory to store registry data
* starts docker registry
 