## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK-REDTEAM DIAGRAM](https://github.com/jennapoitras/Project-1-Final/blob/main/Diagram/Project1-Unit13.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

[install-docker-playbook.txt](https://github.com/jennapoitras/Project-1-Final/blob/main/Ansible/install-docker-playbook.txt)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access and traffic to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?_
Load balancers protect the availability portion of the CIA triad! It does so by balancing traffic equally between devices which makes it so the dockers or machines cannot be overloaded.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jump box and system network.
- What does Filebeat watch for?
Filebeat watches log files or locations that the user specified while collecting log events and then forwards them to either Elasticsearch or Logstash
- What does Metricbeat record?
Metricbeat records metrics and statistics from the system and services that are running on the server, then it forwards them to Elasticsearch or Logstash

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|:----------:|:----------:|:------------:|:------------------:|
| Jump Box   | Gateway    | 10.0.0.4     | Linux            |
| Web-1      |Host for DVWA| 10.0.0.5     | Linux            |
| Web-2      |Host for DVWA| 10.0.0.6     | Linux            |
| Web-3      |Host for DVWA| 10.0.0.7     | Linux            |
| ELK-1      |Security Monitor| 10.1.0.6     | Linux            |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the Admin's IP adress.

Machines within the network can only be accessed by the Jump Box.
- The Jump Box VM is allowed to access the ELK VM, it's IP address is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|:----------:|:---------------------:|:----------------------:|
| Jump Box | Yes                 | Admin's IP Address   |
|    ELK-1 |    Yes              |  Admin's IP Address  |
|   Web-1  |   No                |                      |
|   Web-2  |   No                |                      |
|   Web-3  |   No                |                      |
  

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it saves time and ensures that the all setups were the same and done properly.

The playbook implements the following tasks:
- Configures the VM's max memory
- Installs pip3
- Installs ELK Docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![after docker ps](https://github.com/jennapoitras/Project-1-Final/blob/main/screenie1.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1
- Web-2
- Web-3

We have installed Filebeat on the ELK VM.

These Beats allow us to collect the following information from each machine:
- Filebeat lets us collect log files. This means that we can track things like failed access attempts, users logging in, and service starts and stops. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible/files.
- Update the /etc/ansible/hosts file to include the category that contains the IP address(s) of the VM(s)
- Run the playbook, and navigate to http://ELK_IP/app/kibana to check that the installation worked as expected.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
