# dcos-fluent-bit-demo

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
dcos node --json | generate-ansible-config
cd ansible

# Start sending data to elastic from each node
ansible-playbook -i inventory send-to-elastic.yaml
```

