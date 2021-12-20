# Cybersecurity## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK network diagram](Diagram/Project.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  
This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
Load Balancers protect the organisations from DoS(Denial of service) attacks

 Ristricting  access to the network is done Via Jump Box. A jump box is a secure computer that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers . It sits in front of other machines that are not exposed to the public internet.It controls access to the other machines by allowing connections from specific IP addresses and forwarding to those machines. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system resources.
-  What does Filebeat watch for? Filebeat is a special purpose data collections modules or agents which allows us to collect log files of machines we are interested in and sends that log data to Logstash and Elasticsearch for indexing 
-  What does Metricbeat record?  Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and sends them to the  Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    |  Server  | 10.0.0.5   | Linux            |
| Web-2    | Server   | 10.0.0.6   | Linux            |
| Elk      | Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-  99.235.119.208

Machines within the network can only be accessed by machines within the network.
- Jump Box w/Ansible container is allowed to access ELK VM. It Private IP address is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 99.235.119.208       |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| Elk      | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- It eliminates human error and  ensure that our provisioning scripts run identically everywhere they use them. 

The playbook implements the following tasks:
- Install Docker Engine
- Install Python Software
- Configure the VM to use more memory
- Download and launch docker elk container image
- Configure the container for port mapping

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/elk_docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 : 10.0.0.5
- Web-2 : 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Metricbeat collect metric data from the target servers for e.g operating system metrics such as CPU or memory or data related to services running on the server
- Filebeat collects log files from the targer servers which can be used for security and surveillance.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the YAML file to /etc/ansible.
- Update the /etc/ansible/hosts file to include IP adresses of the host machines where the playbook file runs
- Run the playbook, and navigate to http://[VM Public IP]:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

To run Ansible playbook run the command : ansible-playbook (name of playbook).yml

To update the files run the command : nano ansible.cfg  AND nano hosts



# Linux Commands used in ELK Project
### Installing and using Docker
#### Open the terminal and SSH into jump box
- Run <font face="Brush script M1">ssh username@jump_box_ip</font>
#### Update Images
- Run <font face="Brush script M1">apt -get update</font>
#### Install Docker
- Run <font face="Brush script M1">sudo apt install docker.io</font>
#### Check istallation is successfull
- Run <font face="Brush script M1">which docker</font>

        /usr/bin/docker
#### Check the docker service is running
- Run <font face="Brush script M1">sudo systemctl status docker</font>
![Docker status image](Images/Docker_status.jpg)
#### If Docker service not running
- Run <font face="Brush script M1">sudo systemctl start docker</font>
#### Image format in [hub.docker.com](https://hub.docker.com/)
- [image_maker]/[image_name]
#### To download image
- Run <font face="Brush script M1">sudo docker pull cyberxsecurity/ansible</font>
#### To Launch a container and connect to its command line
- Run <font face="Brush script M1">sudo docker run -ti cyberxsecurity/ansible:latest bash</font>
#### To list all containers created on the system
- Run <font face="Brush script M1">sudo docker container list -a</font>
![Container list image](Images/container_list1.jpg)
#### To start the container
- Run <font face="Brush script M1">sudo docker start container_name</font>
#### List all running containers
- Run <font face="Brush script M1">sudo docker ps</font>
![Container list image](Images/docker_ps.jpg)
#### To activate a shell in your container
- Run <font face="Brush script M1">sudo docker attach container_name</font>
![Container list image](Images/attach_container.jpg)
#### To check Ansible is installed and running
- Run <font face="Brush script M1">ansible</font>
![Container list image](Images/ansible.jpg)
#### To generate SSH keys inside ansible container
- Run  <font face="Brush script M1">ssh-keygen</font>
#### Copy the public key created in .ssh directory
- Run <font face="Brush script M1">ls -a</font>
- Run <font face="Brush script M1">cd .ssh</font>
- Run <font face="Brush script M1">cat id_rsa.pub</font>
![Container list image](Images/public_key.jpg)
