## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://drive.google.com/file/d/1yTiZINjQapQHTutJSVuUJNE9dBSwcV1-/view?usp=sharingThese files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - install-elk.yml

- ---
  ![image-20211212143539368](C:\Users\terre\AppData\Roaming\Typora\typora-user-images\image-20211212143539368.png)

![image-20211212143836201](C:\Users\terre\AppData\Roaming\Typora\typora-user-images\image-20211212143836201.png)

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- A load balancer distributes traffic from clients across multiple servers without the clients having to understand how many servers are in use and configured. The load balancer sits between the clients and the servers it can enhance the user experience by providing additional security.Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.

- Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- _Metricbeat record and takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash._

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       | Function   | IP Address | Operating System |
| ---------- | ---------- | ---------- | ---------------- |
| Jump Box   | Gateway    | 10.0.0.4   | Linux            |
| Web 1      | Webserver  | 10.0.0.5   | Linux            |
| Web 2      | Webserver  | 10.0.0.6   | Linux            |
| Elk-Server | Monitoring | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- http://40.83.38.103/5061 Kibana Port

Machines within the network can only be accessed by _____.
- http://40.83.38.103:5601

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
| -------- | ------------------- | -------------------- |
| Jump Box | Yes                 | 20.124.253.63        |
| Web 1    | no                  | 10.0.0.5             |
| Web 2    | no                  | 10.0.0.6             |
| Elk      | no                  | 10.1.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? Ansible automation helps considerably with the representation of Infrastructure as Code (IAC). IAC involves provisioning and management of computing infrastructure and related configuration through machine-processable definition files_

The playbook implements the following tasks:
- Install docker.io
- Install pip3
- Install Docker python module
- Increase virtual memory
- Download and launch a docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](C:\Users\terre\OneDrive\Pictures\Screenshots\2021-12-09 (10).png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:-Private IPs of Web-1 and Web-2
| Name | IP Addresses |
| ---- | ------------ |
| Web1 | 10.0.0.5     |
| Web2 | 10.0.0.6     |

_

We have installed the following Beats on these machines:
- _Microbeats_

These Beats allow us to collect the following information from each machine:
- The_Filebeat  collects data about the file system
- The Metricbeat  collects machine metrics, such as uptime

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- make sure your azure is started

- open git bash

-  ssh -i ~/.ssh/id_rsa_jumpbox RedAdmin@20.124.253.63

- start your docker container "sudo docker start kind_chebyshev "

- after start use '' sudo docker attach kind_chebyshev" note: you should now have "Root@''

- now use "cd /etc/ansible/"  

- to create a playbook lets create a file by "touch filebeat-config.yml  "

- now we will use "nano filebeat-config.yml"  filebeat-playbook.yml  

  ![image-20211212135130387](C:\Users\terre\AppData\Roaming\Typora\typora-user-images\image-20211212135130387.png)

  

- save and exit out of nano by "ctrl x" press "y" for yes then press enter

- next we will set up the playbook start by making a file "touch filebeat-playbook.yml"

- use nano filebeat-playbook.yml use resource file to copy your play book to minimize errors

-  ![image-20211212141509155](C:\Users\terre\AppData\Roaming\Typora\typora-user-images\image-20211212141509155.png)

- save and exit out of nano by "ctrl x" press "y" for yes then press enter

- now we can can run filebeat-playbook.yml by using "ansible-playbook filebeat-playbook.yml"

- ![image-20211212142348093](C:\Users\terre\AppData\Roaming\Typora\typora-user-images\image-20211212142348093.png)

