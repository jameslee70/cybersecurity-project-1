# cybersecurity-project-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!(Images/cloudenvironmentdiagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Azure Cloud Environment file may be used to install only certain pieces of it, such as Filebeat.

  

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting access to the network.
-Load balances protect against DDoS attacks.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the actual machines and system logs.
- Filebeat watches for information about the file system?
-Metricbeat collects metrics from the operating system and ships them to the output that you specify

The configuration details of each machine may be found below.

| Name                 | Function         | IP Address | Operating System |
|----------------------|------------------|------------|------------------|
| Jump-Box-Provisioner | Gateway          | 10.0.0.7   | Linux            |
| Web-1                | DVWA Containers  | 10.0.0.12  | Linux            |
| Web-2                | DVWA Containers  | 10.0.0.13  | Linux            |
| Web-3                | DVWA Containers  | 10.0.0.14  | Linux            |
| ELK                  | Configuration VM | 10.1.0.4   | Linux            |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Machine machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-Home Network IP

Machines within the network can only be accessed by home network IP.

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Address      |
|----------------------|---------------------|-------------------------|
| Jump-Box-Provisioner | Yes                 | 10.0.0.7, home ip       |
| Web-1                | No                  | 10.0.0.7                |
| Web-2                | No                  | 10.0.0.7                |
| Web-3                | No                  | 10.0.0.7                |
| ELK                  | No                  | 10.0.0.7, home ip       |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-You don’t need to install any other software or firewall ports on the client systems you want to automate.

The playbook implements the following tasks:
- Install Docker
- Download Image
- Configure container
- Create playbook to install container with docker and Filebeat and Metricbeat.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.12 - Web-1
- 10.0.0.13 - Web-2
- 10.0.0.14 - Web-3

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat


These Beats allow us to collect the following information from each machine:
- Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat provides a way to provide information such as metrics from the operating system and from services running on a server. Metricbeat collects this data and sends it to Elasticsearch/Logstash

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the roles folder to /etc/ansible/roles.
- Update the hosts file to include webserver IP's and ELKServer IP
- Run the playbook, and navigate to HTTP://<ELKServer_Public_IP>:5601 to check that the installation worked as expected.


- Copy the roles folder (linked above) and files to /etc/ansible/roles
- Update the /etc/ansible/hosts file to include the webservers IP's and ELKServer IP
- Update each configuration file with ELKServer IP


