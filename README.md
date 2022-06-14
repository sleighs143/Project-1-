Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](Diagrams/Final\ FINAL_P1-HW13_Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yaml file may be used to install only certain pieces of it, such as Filebeat.

 Filebeat-playbook
 Filebeat-config
 Install-elk
 Metricbeat-playbook
 Metricbeat-config

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box? Protecting applications from emerging threats. The web applications firewall (WAF) within the load balancer ensures protection of your website from hackers. Load balancers can authenticate user access by requesting a username and password before access is granted to the website.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

What does Filebeat watch for? Filebeat monitors log files or locations specified to collect log events and sends them to Elasticsearch or Logstash for indexing. 
What does Metricbeat record? It collects metrics and statistics sending them to the output you specify.

The configuration details of each machine may be found below.


Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 40.86.xx.xx

Machines within the network can only be accessed by the Jump Box.
- Which machine did you allow to access your ELK VM? What was its IP address? Jump Box 40.86.xx.xx

A summary of the access policies in place can be found in the table below.



Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? Anisble allows one user the ability to deploy the same configuration across multiple devices fast and seamlessly without the risk of human error.

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

- Install docker
-Download ansible
-Configure elk-playbook.yml
-Push the playbook to the machines	
-Ssh into machine and confirm playbooks successful 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.



Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.2.0.5
-10.2.0.6
-10.2.0.7

We have installed the following Beats on these machines:
-Specify which Beats you successfully installed filebeat.

These Beats allow us to collect the following information from each machine:
- Filebeat collects data about the file system like log events, shipping them to the Elasticsearch cluster.
-Metricbeat collects metrics / statistics shipping the information to the output specified such as Logstash / Elasticsearch.

Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the my-playbook.yml file to the jumpbox ansible container.
- Update the host file to include the webserver and elk IP addresses.
- Run the playbook, and navigate to kibana to check that the installation worked as expected.

Answer the following questions to fill in the blanks:
- Which file is the playbook? Where do you copy it? The filebeat-playbook.yml
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? Adding the Elk server’s IP address to the ansible.cfg file.
- Which URL do you navigate to in order to check that the ELK server is running? http://20.5.69.199:5601/app/kibana



As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.

-Nano ansible.cfg
-Add the machines IP and ansible_python_interpreter=/usr/bin/python3 to hosts
-Ctrl x + Y to save and exit file
-In install-elk.yml folder run cp install-elk.yml /etc/ansible
-Nano install-elk.yml /etc/ansible
-Installing elk hosts: name- ( your machine )
-Ctrl x + Y to save and exit file
-Ansible-playbook install-elk.yml
