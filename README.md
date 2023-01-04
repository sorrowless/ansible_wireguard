# sbog/wireguard

Simple role to install wireguard

#### Requirements

Ansible 2.4

#### Role Variables

```yaml
# Configuration & data directory
wireguard_directory: /etc/wireguard
# Real server DNS name
wireguard_server_url: vpn.example.com
# Port to listen
wireguard_server_port: 51820
# Peer names list
wireguard_peers_names: []
# DNS servers for peers
wireguard_peers_dns: [8.8.8.8, 1.1.1.1]
# VPN network
wireguard_internal_subnet: 10.10.105.0/24
# Allowed IP addresses
wireguard_allowed_ips: 0.0.0.0/0
# Whether to log confs
wireguard_log_confs: true
# Docker-related networking settings
wireguard_docker_network_name: prom_network
# Labels assigned to docker container
wireguard_docker_labels: ['wireguard']
```

#### Dependencies

None

#### Example Playbook

```yaml
- name: Install and configure Wireguard
  hosts: wireguard_servers
  remote_user: root
  roles:
    - { role: sorrowless.wireguard, tags: [ 'wireguard', 'vpn' ] }
```

#### License

Apache 2.0

#### Author Information

Stan Bogatkin (https://sbog.org)
