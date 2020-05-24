# Deploy
To deploy on VMs
## Prerequisites
```
pip3 install ansible requests google-auth ansible-lint
```
## Getting Started
Create instances on gcp and attach a label env=dev
### Validate
Validate ansible playbook and roles
```
ansible-lint -v playbook.yml
```
### Get cloud inventory
Get gcp cloud inventory using the ansible plugin
```
ansible-inventory -i data.gcp.yml --output dynamic-ini --list
```
### Create inventory file
Create inventory file for dev environment at run time
```
echo "[dev]" > dev/ini
cat dynamic-ini | jq -r '.gcp_env_dev.hosts[]' >> dev/ini
```
### Run playbook
```
ansible-playbook -i dev/ini playbook.yml
```
