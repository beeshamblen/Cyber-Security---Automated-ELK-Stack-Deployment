## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
- [Azure Network Diagram](Diagrams/Azure_Network_Diagram.jpg)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the elk_playbook file may be used to install only certain pieces of it, such as Filebeat.

  - [ELK_Playbook](Ansible/ELK_Playbook.yml)
  
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

*`Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network. Load balancers protect availability for web servers; To further assist in securing the virtual network, jump boxes are used. Jump boxes allow a single access point. `*


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system metrics.
- *Filebeat looks through system logs for system level changes.*
- *Metricbeat records metrics and statistic.*


The configuration details of each machine may be found below.

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| Web1     | Web Server | 10.0.0.6   | Linux            |
| Web2     | Web Server | 10.0.0.5   | Linux            |
| ELK      | ELK Stack  | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

***184.179.6.147***

Machines within the network can only be accessed by Jump Box:

***10.0.0.4***

A summary of the access policies in place can be found in the table below.

| Names    | Publicly Accessible | Allow IP Addresses   |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 184.179.6.147        |
| Web1     | No                  | 10.0.0.4             |
| Web2     | No                  | 10.0.0.4             |
| ELK      | Yes                 | 184.179.147 10.0.0.4 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because 
***`Less user interaction per machine; More efficiency and ease of deployment. `***

The playbook implements the following tasks:
- Initializes the playbook name, the host and the user. 
- Installs Docker, Python and pip module
- Set memory configuration
- Installs Elk docker container module
- Starts services, if they have yet to be started.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[Docker_ps_Output](Images/Docker_ps_Output.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

 - ***10.0.0.6***
 - ***10.0.0.5***

***Filebeat*** and ***Metricbeat*** has been installed on these machines.

These Beats allow us to collect the following information from each machine:

 - ***Filebeat collects file system logs and will display activity such as
   file changes.***
 - ***Metricbeat collects metrics from your system ie cpu and memory usage.***

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- `Copy the Elk playbook YAML file to /etc/ansible/.`
- `Update the hosts file to include the webservers and ELK server IP addresses.
Set the webserver ip addresses under the '[webservers]' group. `
- `Set the elk server ip address under the '[elk]' group. `
- `Run the playbook, and navigate to http://40.86.94.85:5601/app/kibana#/dashboard to check that the installation worked as expected.`








