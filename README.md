## deploy

export ANSIBLE_HOST_KEY_CHECKING=False

ansible-inventory -i data.gcp.yml --host instance-1 | jq '.networkInterfaces[0].accessConfigs[0].natIP'