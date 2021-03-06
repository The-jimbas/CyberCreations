## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/The-jimbas/CyberCreations/blob/main/Diagrams/Jim%20Baskin%20Azure%20Network.pdf 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/The-jimbas/CyberCreations/blob/main/Ansible/install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in   
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
- A jump box was also employed to limit access to the servers. This provides greater security less complexity compared to allowing access directly to servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the permissions and system files.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | DVWA 1   | 10.0.0.8   | Linux            |
| Web-2    | DVWA 2   | 10.0.0.9   | Linux            |
| ELK      | ELK      | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresse:
- 187.252.193.125

Machines within the network can only be accessed by the Jump Box, 10.0.0.1.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses        |
|----------|---------------------|-----------------------------|
| Jump Box | Yes                 | 187.252.193.125 10.0.0.x    |
| Web-1    | No                  | 10.0.0.x , 10.1.0.4         |
| Web-2    | No                  | 10.0.0.x , 10.1.0.4         |
| ELK      | No                  | 10.0.0.x , 10.1.0.4         |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because 
we have an easy way to rebuild our environment as needed, and quickly build multiple instances of each server.

The playbook implements the following tasks:
- Install Docker on the web VM
- Install Python  
- Install and launch the ELK container
- Enable the Docker servce to start on reboot


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.8, 10.0.0.9

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects and centralizes log data, and Metricbeat forwards and centralizes system monitoring data

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the __filebeat-playbook.yml___ file to __/etc/ansible___.
- Update the __filebeat-playbook.ym___ file to include  hosts: webservers
- Run the playbook, and navigate to __the web servers__ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? filebeat-playbook.yml, metricbeat-playbook.yml    Where do you copy it?   /etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? hosts: webservers
- _Which URL do you navigate to in order to check that the ELK server is running?

_The specific commands the user will need to run to download the playbook, update the files, etc._

Make sure access is granted for Jumpbox to access Web1 and 2.

Jump     10.0.0.4
Web1    10.0.0.8
Web2    10.0.0.9

Then go to ansible container on Jump Box and change hosts and .cfg file for ansible.

Sudo docker container list -a                   shows containers 

Sudo docker start zen_mcnulty

Sudo docker attach zen_mcnulty            ansible container name. Should connect to the container as root with new prompt.

Cd /etc/ansible
ls
              nano my-playbook.yml

   
ansible-playbook my-playbook.yml        to run file


