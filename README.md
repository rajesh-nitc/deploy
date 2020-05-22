## deploy

### prerequisite

```
pip3 install ansible
pip3 install requests google-auth
```
### get dynamic inventory from cloud
```
ansible-inventory -i data.gcp.yml --output dynamic-ini --list
```
### build inventory file for dev
```
echo "[dev]" > dev/ini
cat dynamic-ini | jq -r '.gcp_env_dev.hosts[]' >> dev/ini
```
### run playbook
```
ansible-playbook -i dev/ini playbook.yml
```
