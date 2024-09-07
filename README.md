# Argon Testnet Deployment
This is a public repository to demonstrate how the Argon testnet is deployed. The deployment is done using Ansible. 
You'll find custom roles built for the various parts of the Argon network. Prometheus metrics are generated and exported 
for each role, but there isn't currently an included prometheus server to collect the metrics. 

## Directory Structure:

- `inventory/testnet` - Contains the inventory files for the testnet deployment.
- `roles` - Contains the custom roles for the Argon network.
- `./` - Contains the playbooks for deploying the network.

> NOTE: You likely only want to deploy a bitcoin node and miner(s), so you would modify inventory/testnet/hosts.yml to only include host information for those two items.

## Playbooks:
- `full_network.yml` - Deploys the full network.
- `debug.yml` - Gathers logs from network hosts
- `journalctl_vacuum.yml` - Cleans up journalctl logs on network hosts
- `key_rotation.yml` - Rotates mining keys for the Argon node and miners
- `purge.yml` - Purges data from the miners and notary (if applicable)
- `restart_services.yml` - Restarts services on the network hosts (defaults to argon-nodes)

## Installation
1. Clone the repository
2. Install ansible: https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html
3. Install pipenv: https://pypi.org/project/pipenv/
4. pipenv install
5. pipenv shell
6. ansible-galaxy install -r requirements.yml
7. You need to create your own version of `inventory/testnet/group_vars/all/vault.yml` with the following content (or whichever parts you want to deploy yourself):
    ```yaml
    vault_oracle_bls_api_key: "your_api_key"
    vault_prometheus_nginx_password: "password"
    vault_argon_node_p2p_private_key_archive_node: "generate with `argon-node key generate-node-key`"
    vault_argon_node_p2p_private_key_miner_node_1: "generate with `argon-node key generate-node-key`"
    vault_argon_node_p2p_private_key_miner_node_2: "generate with `argon-node key generate-node-key`"
    vault_bitcoin_rpc_password: "your password"
    ```
   You can create a new vault config file with `ansible-vault create inventory/testnet/group_vars/all/vault.yml`
8. Modify or replace inventory/testnet/hosts.yml with your own inventory ips, rpc urls and information.
9. Run a playbook like `ansible-playbook -i inventory/testnet full_network.yml`
