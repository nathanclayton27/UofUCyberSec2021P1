## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!(diagrams/dotio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-config.yml
  - filebeat-playbook.yml
  - metricbeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?

	Using a jumpbox makes it so credentials cant be leaked by using a public and private key instead of login details. A load balancer prevents a ddos attack from taking down the servers and distributes load.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the vm's and system logs.
- Filebeat gathers logs and tracks them.
- Metricbeat gathers system metrics like cpu usage.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 137.135.24.25   | Linux            |
| Web1    |  Webserver        |     10.0.0.6       |      Linux            |
| Web2     |    Webserver      |    10.0.0.7        |      Linux            |
| Web3     |   Webserver       |    10.0.0.5        |      Linux            |
|----------|----------|------------|------------------|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 71.198.216.65

Machines within the network can only be accessed by the load balancer.
- The Jump Box is allowed to access the Elk machine. The IP is 137.135.24.25.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | no              | 71.198.216.65    |
|  DVWA        |   yes                  |     any                 |
|   Elk Server       |       no              |     137.135.24.25                 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- This makes creating a new machine as simple as launching a new machine in azure and running the ansible playbooks on that ip. 

The playbook implements the following tasks:
- Install Docker and Python
- Find and install the Docker module you want to deploy
- Check for the correct memory on the container.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!(diagrams/dockerps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5, 10.0.0.6, 10.0.0.7
We have installed the following Beats on these machines:
- Filebeat and Metricbeat

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config file to etc/ansible/files.
- Update the config file to include the elk machine ip
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.
