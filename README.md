# ELK_Monitoring_Stack

The files in this repository were used to configure the network depicted below:

![Network Diagram](https://github.com/ljponche/ELK_Monitoring_Stack/blob/master/Images/ELK_Monitoring_Stack_Network_Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat.yml file may be used to install only certain pieces of it, such as Filebeat.

YAML File
[filebeat.yml](https://github.com/ljponche/ELK_Monitoring_Stack/blob/master/YAML_files/filebeat.yml)

This document contains the following details:

* Description of the Topology
* Access Policies
* ELK Configuration
  * Beats in Use
  * Machines Being Monitored
* How to Use the Ansible Build


**Description of the Topology**
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.

By routing HTTP traffic through a load balancer, this will help to migitaging DDoS attacks. And by restricting access to the network to a single JumpBox VM, we can more easily monitor connections to our internal network web VMs.  Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the VM metrics and system files.

The configuration details of each machine may be found below:

| Name                 | Function     | IP Address | Operating System     |
|----------------------|--------------|------------|----------------------|
| Jump-Box-Provisioner | Gateway      | 10.0.0.5   | Linux (ubuntu 18.04) |
| Web-1                | Web server   | 10.0.0.6   | Linux (ubuntu 18.04) |
| Web-2                | Web server   | 10.0.0.7   | Linux (ubuntu 18.04) |
| Web-3                | Web server   | 10.0.0.8   | Linux (ubuntu 18.04) |
| ELK-VM               | Monitoring   | 10.1.0.4   | Linux (ubuntu 18.04) |


Access Policies

A summary of the access policies in place can be found in the table below.

**NSG_1**
| Priority | Name                                    | Port | Protocol | Source            | Destination    | Action |
|----------|-----------------------------------------|------|----------|-------------------|----------------|--------|
| 400      | Allow_HTTP_To_LB_From_Home              | 80   | Any      | 69.222.176.125/32 | VirtualNetwork | Allow  |
| 425      | Allow_SSH_From_Home_To_JumpBox          | 22   | TCP      | 69.222.176.125/32 | 10.0.0.5       | Allow  |
| 450      | Allow_SSH_From_JumpBox_To_VNET_Machines | 22   | TCP      | 10.0.0.5/32       | VirtualNetwork | Allow  |
| 65500    | DenyAllInBound                          | Any  | Any      | Any               | Any            | Deny   |

**ELK-VM-nsg**
| Priority | Name                | Port | Protocol | Source            | Destination    | Action |
|----------|---------------------|------|----------|-------------------|----------------|--------|
| 270      | Allow_SSH_To_ELK_VM | 5601 | TCP      | 69.222.176.125/32 | VirtualNetwork | Allow  |
| 65500    | DenyAllInbound      | Any  | Any      | Any               | Any            | Deny   |


Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

TODO: What is the main advantage of automating configuration with Ansible?

The playbook implements the following tasks:

TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
...
...

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.
Note: The following image link needs to be updated. Replace docker_ps_output.png with the name of your screenshot image file.


Target Machines & Beats
This ELK server is configured to monitor the following machines:

TODO: List the IP addresses of the machines you are monitoring

We have installed the following Beats on these machines:

TODO: Specify which Beats you successfully installed

These Beats allow us to collect the following information from each machine:

TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., Winlogbeat collects Windows logs, which we use to track user logon events, etc.


Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:

Copy the _____ file to _____.
Update the _____ file to include...
Run the playbook, and navigate to ____ to check that the installation worked as expected.

TODO: Answer the following questions to fill in the blanks:

Which file is the playbook? Where do you copy it?
Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
_Which URL do you navigate to in order to check that the ELK server is running?
