## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
![Network Map](/Images/Map.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - ansible-playbook docker_elk.yml

    \- name: Install / Configure Docker Repository

     hosts: elkservers

     become: true

     tasks:

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
-  What aspect of security do load balancers protect? What is the advantage of a jump box?
- *The off-loading function of a **load balancer** defends an organization against distributed denial-of-service (DDoS) attacks. It **does** this by shifting attack traffic from the corporate server to a public cloud provider.* 
- *A jump box limits the entry point flow of the network to a single node.*  A *jump box* is a secure computer that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- What does Filebeat watch for?
- **Filebeat** monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or **Logstash** for indexing
-  What does Metricbeat record?
- Metricbeat records system and service metrics from a host device.

The configuration details of each machine may be found below.


| Name      | Function       | IP Address | Operating System |
| --------- | -------------- | ---------- | ---------------- |
| Jump Box  | Gateway        | 10.0.0.1   | Linux            |
| Web 1     | DVWA Webserver | 10.0.0.5   | Linux            |
| Web 2     | DVWA Webserver | 10.0.0.6   | Linux            |
| Higharden | ELK Server     | 10.0.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Only from address 75.105.116.27 as that is my home IP address on port 22

Machines within the network can only be accessed by _____.
- JumpBox Provisioner IP 10.0.0.1

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
| -------- | ------------------- | -------------------- |
| Jump Box | No                  | 75.105.116.27        |
| Web 1    | No                  | 10.0.0.4             |
| Web 2    | No                  | 10.0.0.4             |
| Elk-VM   | No                  | 10.1.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-  What is the main advantage of automating configuration with Ansible?
- *It provides a stable environment for the development and operations team, The primary benefit of Ansible is it allows IT administrators to automate away the drudgery from their daily tasks. That frees them to focus on efforts that help deliver more value to the business by spending time on more important tasks.*

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install docker.io
- Install pip3, an installer for python3.
- Install docker python module.
- Increase virtual memory
- Download and launch a docker elk container image: sebp/elk: 761



The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Successful ELK instance](Images/Welcome.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-  List the IP addresses of the machines you are monitoring
- 10.0.0.5 and 10.0.0.6 Web 1 and 2

We have installed the following Beats on these machines:
-  Specify which Beats you successfully installed
- Fliebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
-  In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
- Filebeat is used for monitoring log files, forwarding and centralizing log data to Elasticsearch or Logstash for indexing. Metricbeat provides information on and analyzes system CPU usge and uptime. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

 Answer the following questions to fill in the blanks:
- _Which file is the playbook? Where do you copy it?_
- The playbook file is fliebeat-configuration.yml.  It was copied to the Elk-VM from 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- The hosts file would be updated to determine what machine it is to be run on.  
- _Which URL do you navigate to in order to check that the ELK server is running?
- 104.214.75.168:5601/app/Kibana#/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
