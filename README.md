# Provision k3s agent

Provision a host with k3s agent.

This role performs the following steps:

- Installs k3s from the official install script
- Configures `k3s-agent` systemd service

This role is intended for use in prototyping and internal development projects. This role is not intended for production environments, or for any public-facing services.

## Requirements

Provisioning host:

- Ansible 2.15

Remote host:

- Ubuntu 22.04 or 24.04
- EWAOL
- docker or containerd
- git

## Example playbook

```yaml
- hosts: all
  roles:
    - name: xronos_k3s_agent_ansible
      role: xronos_k3s_agent_ansible
      vars:
        k3s_api_endpoint: "127.0.0.1:6443"   # URI:port of your k3s server
        k3s_token: ""   # your secret token here
```

After running, the service `k3s-agent` should be running on the remote host.

## Variables

- `k3s_api_endpoint`: k3s endpoint URI and port, i.e. `127.0.0.1:6443`. Required.
- `k3s_token`: secret token to use for authenticating k3s agent to the k3s control node. Required.
- `k3s_version`: version identifier of k3s to install. Defaults to empty (latest).
