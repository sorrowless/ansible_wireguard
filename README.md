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
# Peers list
wireguard_peers: []
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

# Optional hairpin for full-tunnel clients hitting this host's public IP.
# Service DNAT (Docker/Swarm DNS on the same network):
# wireguard_hairpin_address: "203.0.113.10"
# wireguard_hairpin_service_name: "myStack_myService"
# wireguard_hairpin_ports: ["80", "443"]
# wireguard_hairpin_dns_retries: 15
# Host-published ports (sshd): REDIRECT on docker_gwbridge on the Docker host.
# wireguard_hairpin_host_ports: ["909"]
# wireguard_hairpin_bridge_interface: docker_gwbridge
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
