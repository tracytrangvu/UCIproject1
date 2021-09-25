## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

- [AWS Cloud Security Project drawio](https://user-images.githubusercontent.com/85351681/134754291-cc572da6-e664-46fd-bc02-31336756e98a.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

- [Filebeat-playbook.yml](Filebeat-playbook.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible/redundant/reliable, in addition to restricting access to the network.
-What aspect of security do load balancers protect? What is the advantage of a jump box? Load balancers protects the system from DDos attacks by shifting attack traffic. The advantage of a jump box is to give access to the user from a single node that can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- What does Filebeat watch for? Filebeat is lighweight shipper for forwarding and centralizing log data and monitors the log files or locations that you specify.
- _TODO: What does Metricbeat record? Metricbeat records the metrics and statistics from the operation system and from services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address    | Operating System |
|----------|----------|---------------|------------------|
| Jump Box | Gateway  | 172.31.5.179  | Linux/Ubuntu     |
| Web1     | Server   | 172.31.39.169 | Linux/Ubuntu     |
| Web2     | Server   | 172.31.12.230 | Linux/Ubuntu     |
| Web3     | Server   | 172.31.26.135 | Linux/Ubuntu     |
| ELK      | Server   | 172.31.9.167  | Linux/Ubuntu     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 3.128.95.201

Machines within the network can only be accessed by Jumpbox.
- Which machine did you allow to access your ELK VM? Jumpbox What was its IP address? 172.31.5.179 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 172.31.5.179         |
| VM1      | No                  | 172.31.5.179         |
| VM2      | No                  | 172.31.5.179         |
| VM3      | No                  | 172.31.5.179         |
|ELK Server| No                  | 172.31.5.179         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? The advantage is that you can put commands into multiple servers from a single playbook

The playbook implements the following tasks:
- The steps of the ELK installation
- Install: docker.io
- Install: python3-pip
- Install: docker
- Command: sysctl -w vm.max_map_count=262144
- Launch docker container: ELK

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your diagram](dockerps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring
- 172.31.39.162
- 172.31.12.230
- 172.31.26.135

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed in Web1, Web2 and Web3

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk_install.ymlfile to /etc/ansible.
- Update the hosts file to include...
- ![TODO: Update the path with the name of your diagram](elk_picture.png)

- Run the playbook, and navigate to http://[your_elk_server_ip]:5601/app/kibana to check that the installation worked as expected.

_Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? /etc/ansible/filebeat-playbook.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- _Which URL do you navigate to in order to check that the ELK server is running?
http://[your_elk_server_ip]:5601/app/kibana
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc
- cd /etc/ansible
- nano elk-install.yml
- run the playbook: ansible-playbook -i hosts apache-playbook.yml
- check http://[your_elk_server_ip]:5601/app/kibana

