# dcos-fluent-bit-demo

## Prerequisites

 - an ssh key which can access your cluster, as defined in ssh.cfg
 - dcos-cli logged in to your cluster
 - 5-agent Enterprise DC/OS >1.13.0-alpha cluster (this won't work on regualr DC/OS without modification)

## Usage

```bash
# Installation
git clone https://github.com/philipnrmn/dcos-fluent-bit-demo.git
cd dcos-fluent-bit-demo

# Setup
chmod +x ./bin/*
export PATH="$(pwd)/bin:$PATH"

# Make sure you're connected to the right cluster before proceding
dcos cluster list --attached

# Install Elastic and Kibana
strict-install elastic
strict-install kibana 

# Generate ansible configuration for this cluster
generate-ansible-config
cd ansible

# Check that ansible is appropriately configured (eg check SSH key is available)
ansible -i inventory all -m ping
# Start sending data to elastic from each node
ansible-playbook -i inventory send-to-elastic.yaml
```

## Next steps

Open your browser to https://your-cluster-ip/service/kibana/app/kibana (note that the UI link is currently not working).
