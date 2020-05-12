# ELK-PROJECT
This is my first ELK Project
Juris Magararu                                                    ## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: https://drive.google.com/file/d/1ZeB0lRpGWsbKC0wV7tu7O0p5l_qfCIwl/view?usp=sharing

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. 
Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: ansible-playbook playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable and redundant, in addition to restricting denial of service to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
Load balancers protect in case one of the VMs goes down. The advantage of a jump box is to allow us to perform automated tasks instead of setting up each VM one by one.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system users.
- _TODO: What does Filebeat watch for?_
Filebeat checks logs and centralizes it into one format for you to look at. 
- _TODO: What does Metricbeat record?_
Metricbeat collects machine metrics such as uptime.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function                | IP Address   | Operating System |
|---------- |-------------------------|--------------|------------------|
| REDTEAMVM | Gateway                 | 10.0.0.4     | Linux            |
| DVWA      | Web Application         | 10.0.0.7     | Linux            |
| DVWA2     | Web Application         | 10.0.0.8     | Linux            |
| ELK SERVER| Security Web Application| 168.61.37.145| Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ELK machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 40.78.17.241

Machines within the network can only be accessed by RedTeamVM - Jump box.
- _TODO: Which machine did you allow to access your ELK VM?     MY NETWORK
         What was its IP address?                               108.41.112.223

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| REDTEAMVM| Yes                 | 168.62.31.141        |
| DVWA     | No                  | 10.0.0.7             |
| DVWA2    | No                  | 10.0.0.8             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_ 

Ansible is fast and performs all functions over ssh  and doesn't require agent installation. 
The main advantage is Ansible can be run from the command line without the use of configuration files for simple tasks.

The playbook implements the following tasks:
- _TODO:In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- 	  

	 Create a new VM. 
	 Deploy a new VM into the network. 
	 This VM will host the ELK server.
	 Download and configure the container. 
	 Download and configure the elk-docker container onto this new VM.
	 Launch and expose the container. 
         Launch the elk-docker container to start the ELK server.
         Implement identity and access management. 
	 Configure your preexisting security group so you can connect to ELK via HTTP, and view it through the browser.


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

TODO: https://drive.google.com/file/d/1JZ8p_bIzdHvQ7UIAMrB8fAYIrDD2pqhV/view?usp=sharing



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
         10.0.0.7
         10.0.0.8

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
	 Filebeat
         Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Debian file to playbook.yml
- Update the host file to include the elk server IP, DVWA & DVWA2 Private IPs
- Run the playbook, and navigate to curl localhost/setup.php to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? filebeat-playbook.yml & metricbeat-playbook.yml 
Where do you copy it?_ etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? HOST File 
How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ filebeat.yml
- _Which URL do you navigate to in order to check that the ELK server is running? elkserverIP:5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

nano +1106 filebeat.yml
nano +1806 filebeat.yml
nano +62 metricbeat.yml
nano +96 metricbeat.yml

ansible-playbook filebeat.yml
ansible-playbook filebeat-playbook.yml
ansible-playbook metricbeat.yml
ansible-playbook metricbeat-playbook.yml
