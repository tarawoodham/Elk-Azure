## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted in Images/network\_architecture.png.

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

See file Images/Filebeat_playbook.yml to see the playbook file that was used to install Filebeat and Launch Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D\*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly efficient and available, in addition to restricting unauthorized access to the network.
Load balancers add additional layers of security without changes to the application and can reduce the load on your web servers to optimize traffic for better user experience. Load balancers can also accommodate for failed components to maintain server use. Advantages to a jump box include monitoring and logging on a single box, preventing other VMs from being exposed to the public, and helps improve security.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log data and system metrics.
Filebeat is a logging agent that watches for log files and forwards them to elasticsearch. Metric beat records metric and statistical data form the operating system.

The configuration details of each machine may be found below.

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| Web-1    | VM         | 10.0.0.5   | Linux            |
| Web-2    | Gateway    | 10.0.0.6   | Linux            |
| ELK      | Monitoring | 10.1.0.4   | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet.
Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 52.128.53.61

Machines within the network can only be accessed by SSH from the JumpBox.
The IP address of the JumpBox was 23.96.4.226

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 52.128.53.61         |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because this allowed for future networks to be built in a similar fashion with more automation.

The playbook implements the following tasks:

- Install docker.io
- Install pip3
- Install Docker python module
- Increase virtual memory
- Download and launch a docker ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

See Images/docker\_ps\_output.png for confirmation that the ELK container is running.

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-Web-1 10.0.0.5
-Web-2 10.0.0.6

We have installed the following Beats on these machines:
-Filebeat
-Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat- Log files, their locations, and events
Metricbeat- system metrics and services running on the operating system

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the Install\_elk.yml file to /etc/ansible.
- Update the /etc/ansible/hots file to include the [elk] group and the Virtual Machine in the elk group.
- Run the playbook, and navigate to the load balancer IP (52.149.144.159) to check that the installation worked as expected. See image Images/dvwa\_success.png for confirmation.
