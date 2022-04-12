# Cybersecurtity-Credentials
This is a repository that contains a few scripts and diagrams that I completed while attending the University of Utah Cybersecurity bootcamp.

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/Computaholic0101/Cybersecurtity-Credentials/blob/main/Diagrams/Cloud%20Archetecture.jpg

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the png file may be used to install only
certain pieces of it, such as Filebeat.

  - https://github.com/Computaholic0101/Cybersecurtity-Credentials/tree/main/Ansible/yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting risk to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web1     | Operation| 10.0.0.6   | Linux            |
| Web2     | Operation| 10.0.0.7   | Linux            |
| ELK-VM   | Security | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the gateway machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
72.193.23.9, 
13.87.188.230

Machines within the network can only be accessed by 72.193.23.9.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.6 10.0.0.7    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it helps considerably with the representation of Infrastructure as Code (IAC).

The playbook implements the following tasks:
- Install Docker
- Install Apache
- Install ELK
- Install and configure filebeat
- Install and configure metricbeat

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/Computaholic0101/Cybersecurtity-Credentials/blob/main/docker%20ps.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
13.87.188.230, 10.0.0.6, 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors log file data in order centralize them and mitigate risks.
- Metricbeat collects metrics of a system that is running on a server. It then outputs these metrics to a specified location, such as Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the yml file to the ansible container.
- Update the config file to include the IP address of the machine you would like for it to run on.
- Use command ansible-playbook playbookname.yml to run the yaml scripts.
- Run the playbook, and navigate to http://(your IP address)/setup/php to check that the installation worked as expected.
