# Ansible Role: Container Registry Self-Signed Cert Transfer

Installs self-signed certs for access to a self-hosted container registry.

## Requirements

None.

## Role Variables

Usable variables are listed below, defaults are found in `defaults/main.yml`:

    cert_remote_host: registry.gitlab.example.com

The hostname of the container registry or other SSL host.

    cert_remote_port: 5000

The SSL port of the container regsitry or other SSL host.

    system_cert_location: "/etc/pki/ca-trust/source/anchors/"
    system_cert_filename: "{{ cert_remote_host }}.crt"
    docker_cert_location: "/etc/docker/certs.d/{{ cert_remote_host }}/"
    docker_cert_filename: "ca.crt"

Only need to change the previous 4 variables if your path is different.

## Dependencies

None

## Example Playbook

- hosts: OSEv3
  roles:
     - role: snelson_redhat.ocp_certs.self_signed
       vars:
         - cert_remote_host: "registry.gitlab.example.com"
         - cert_remote_port: 5000

## License

MIT / BSD

## Author Information

This role was created in 2019 by [Sean Nelson](mailto:snelson@redhat.com).
