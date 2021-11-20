## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![/Users/adolphomacias/Downloads/README/Images/Diagram.png](Images/Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: elk-server-playbook.yml_

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly effective, in addition to restricting unauthorized traffic to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? Load Balancer protect unwanted and unauthorized traffic from reaching the application. The advantage of a jumpbox is they add a security layer to the web servers from being exposed to the public._

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the config files and system files.
- _TODO: What does Filebeat watch for?_ Filebeat watches for log files and also log events.
- _TODO: What does Metricbeat record?_ Metricbeat records metrics from the ongoing servere.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web 1    | Webserver| 10.0.0.5   | Linux            |
| Web 2    | Webserver| 10.0.0.6   | Linux            |
| ELK-VM   | Webserver| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 99.77.92.176_

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ My personal Laptop and the IP is 99.77.92.176

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | yes                 | 10.0.0.5 10.0.0.6    |
| Web-1/2  | No                  | 99.77.92.176         |
| ELK-VM   | Yes(http)           | 99.77.92.176         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_ It allows changes to be made within any of the VMs associated with it.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker.io
- Install python3-pip
- Install Docker Python module
- Download and launch Docker web container
- Download and Launch a docker web container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![/Users/adolphomacias/Downloads/README/Images/docker ps.png](Images/docker ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
10.0.0.4, 10.0.0.5, 10.0.0.6, 

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
We have succesfully installed Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
The kind of data filebeat collects and minitors is log files and log events, an example can be when it inputs and harvestes. Metricbeat looks for file systems that have been manipulated.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to files.
- Update the host file to include...
- Run the playbook, and navigate to Jumpbox-Vm to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ elk-server-playbook.yml copy it fo files directory to run it.
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ elk-server-playbook.yml and you use the IP of the server.
- _Which URL do you navigate to in order to check that the ELK server is running?
http://[ELK-VM IP]:5601/app/kibana
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
ansible-playbook elk-server-playbook.yml
