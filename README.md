## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessable, in addition to restricting inbound requests to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.
What does Filebeat watch for? - Watches for files changes and logs and can easily forward them.
What does Metricbeat record?  - It records system metrics such as RAM, uptime, and stats.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function     | IP Address                | Operating System |
|----------|--------------|---------------------------|------------------|
| Jump Box | Gateway      | 10.0.0.1                  | Linux            |
| Red-Web1 | webserver    | 10.0.0.5                  | Linux            |
| Red-Web2 | webserver    | 10.0.0.6                  | Linux            |
| ELK-VM   | Kibana       | 20.231.211.112 ; 10.1.0.4 | Linux            |
| LB       | Load Balancer| 13.88.63.3                |    DVWA          |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
69.162.231.82

Machines within the network can only be accessed by the Container within the Jumpbox.
I allowed the Jumpbox to be accessed from my Local Host via SSH - IP: 69.162.231.82 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 69.162.231.82        |
| ELKserver| Yes                 | 69.162.231.82:5601   |
| DVWA1    | No                  | 10.0.0.1-254         |
| DVWA1    | No                  | 10.0.0.1-254         |



### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it can be rinsed
and repeated as many times as you would like on any kind of scale.

What is the main advantage of automating configuration with Ansible?
	
	It makes it very easy to set up on new computers or systems after you have done it once.
Making up scaling a very easy thing to accomplish and on any type of scope, very customizable.

The playbook implements the following tasks:
- Makes sure the configuration and installation of the correct software is automated.
- Makes sure it is ran on boot and not reset or needing to be manually started each time.
- Makes sure there is enough storage for filebeat and metric beat to run properly.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Redweb-1 : 10.0.0.5
Redweb-2 : 10.0.0.6

We have installed the following Beats on these machines:

- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:

Log files and System files which then is read and forwarded.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Updated_[file].yml file to /etc/ansible.
- Update the hosts file to include the ELK server under a new section.
- Run the playbook, and navigate to http://20.231.211.112 to check that the installation worked as expected.
