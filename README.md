# ELKSTACK-PROJECT
SMU Cyber Security Project 1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

<img width="960" alt="2021-09-17" src="https://user-images.githubusercontent.com/90877028/133735036-8cec5440-0781-4f92-ae67-8229a30f9013.png">


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  
  
 - **[elk-playbook.yml](https://github.com/Jellomeanie/ELKSTACK-PROJECT/blob/main/Ansible/elk-playbook.yml)**         
 
  

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
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Webserver| 10.0.0.5   | Linux            |
| Web-2    | Webserver| 10.0.0.6   | Linux            |
| ELK     | Monitoring| 10.0.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
<Home_Network_IP>

Machines within the network can only be accessed by Jump Box.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |     yes             | <Home_Network_IP>    |
|  Web-1   |     no              | 10.0.0.4             |
|  Web-2   |     no              | 10.0.0.4             |
|  ELK     |     no              | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| Name     | IP Addresses |
|----------|--------------|
| Web-1    |   10.0.0.5   | 
| Web-2    |   10.0.0.6   |

We have installed the following Beats on these machines:
- **[metricbeat](https://github.com/Jellomeanie/ELKSTACK-PROJECT/blob/main/Ansible/metricbeat-playbook.yml)**
- **[filebeat](https://github.com/Jellomeanie/ELKSTACK-PROJECT/blob/main/Ansible/filebeat-playbook.yml)**

These Beats allow us to collect the following information from each machine:
Filebeat allows us to forward and centralize log data. The info is forwarded to elasticsearch/logstash thus providing a GUI for easier monitoring.
Metricbeat provides a way to give info such as metrics from the OS and from services running on a server. It also collects this data and sends it to elasticsearch/logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the **[elk-playbook.yml](https://github.com/Jellomeanie/ELKSTACK-PROJECT/blob/main/Ansible/elk-playbook.yml)** file to /etc/ansible/.
- Update the host file to include web-servers and elk
- Run the playbook, and navigate to http://<ELK-Public_IP>:5601/app/kibana to check that the installation worked as expected.
