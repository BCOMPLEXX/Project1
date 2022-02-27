## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://drive.google.com/drive/folders/1NUGp-J6qxbQM84Sux2qksKS3FDvrsuHY?usp=sharing

  - pentest-yml.png
  - install-elk-yml.png
  - flebeat-playbook-yml.png
  - meatricbeat-playbook-yml.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - pentest.yml
  - install-elk.yml
  - filebeat-playbook.yml
  - metricbeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly avaiability, in addition to restricting access to the network.
What aspect of security do load balancers protect?
- Load balancers protect the system from DDoS attacks by shifting traffic. 

What is the advantage of a jump box?_
The advantage of a jump box is to give secure access to such resources via SSH and Private Pre-Shared key... 


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
What does Filebeat watch for?
- Filebeat forwards and centralizes log data. Filebeat monitors the log files or locations that you specify collects log events and forwards them either to Elasticsearch or Logstash for indexing.

What does Metricbeat record?
- Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as: Apache.


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address  | Operating System |
|----------|----------|-------------|------------------|
| Jump Box | Gateway  | 10.1.0.4    | Linux            |
| ELK      | Gateway  | 52.161.71.66| Linux            |
| Web-1    | LBalancer| FTE-IP      | Linux            |
| Web-2    | LBalancer| FTE-IP      | Linux            |
| Web-3    | LBalancer| FTE-IP      | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
    - 73.6.79.130

Machines within the network can only be accessed by Jumpbox via SSH & Private Pre-Shared Key.
- Which machine did you allow to access your ELK VM? Jumpbox

What was its IP address?
    - 104.208.34.251 (Jumbbox Public)

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |        Yes          |    73.6.79.130       |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible?
- Configuration management, single source for application deployment

The playbook implements the following tasks:

    - ansible-playbook pentest.yml
    - ansible-playbook install-elk.yml
    - ansible-playbook filebeat-playbook.yml
    - ansible-playbook metricbeat-playbook.yml



In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

1.  Check for the presence of docker (Install/Update)
2.  Check for the presence of python3-pip (Install/Update)
3.  Install Docker module
4.  Increase virtual memory
5.  Download and launch docker elk container


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://drive.google.com/drive/folders/1NUGp-J6qxbQM84Sux2qksKS3FDvrsuHY?usp=sharing

- docker_ps_output.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

    - 10.1.0.5
    - 10.1.0.6
    - 10.1.0.7


We have installed the following Beats on these machines:
- Webservers

These Beats allow us to collect the following information from each machine:
- Machine health, performance, system logs and events etc.  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat file to file-conifg.yml.
- Update the filebeat.yml file to include...
- Run the playbook, and navigate to http://13.77.220.158:5601/app/kibana#/home to check that the installation worked as expected.  (Screenshot)


    - https://files.slack.com/files-pri/T02JQ7HRJNQ-F033WR7CBRQ/welcome-to-kibana.png

: Answer the following questions to fill in the blanks:_
- Which file is the playbook? Ansible-playbook files   
- Where do you copy it? Root folder of ansible 
- Which file do you update to make Ansible run the playbook on a specific machine? Hosts configuration file

How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- HostName in Host configuration file

Which URL do you navigate to in order to check that the ELK server is running?
- SSH aszureuser@10.0.0.8 (Web-1)
- http://13.77.220.158:5601

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._


