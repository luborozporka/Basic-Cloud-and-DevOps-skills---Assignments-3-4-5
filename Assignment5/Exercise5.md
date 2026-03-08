![Example playbook 1](example-playbook.png)
![Example playbook 2](example-playbook2.png)
![Example playbook 3](example-playbook3.png)
![Updated playbook 4](updated-playbook4.png)

### 3.1 Ansible Play Failure
The play failed because the playbook was targeting specifically web-server1 and web-server2. However, the inventory file in the command (aws_hosts1) does not contain those specific groups. When Ansible checks the inventory and cannot find a match for the requested host, it skips the play entirely.

### 3.2 Benchmark Nginx
Performance does not continuously increase, peaking at 1.58k requests per second with two instances before plateauing. This bottleneck occurs because more replicas are fighting for limited compute resources. Additionally, Docker Swarm's load-balancing overhead also plays a role. In order to achieve more requests per second, scaling the underlying infrastructure by increasing compute power is necessary.

### 3.2 Ansible Play Development
```ansible-playbook -i aws_hosts2 playbook_example2.yml --start-at-task="Start nginx"```

### 3.3 Questions
Ansible can be used during the configuration management and deployment phases. The primary advantage is its architecture, which relies on standard SSH and YAML files. Among the alternatives, we can include Terraform.