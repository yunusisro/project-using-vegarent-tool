# project-using-vegarent-tool
Vagrant Multi-VM Environment
This Vagrant configuration file sets up a multi-VM development environment with five virtual machines, each provisioned for a specific service (Database, Memcache, RabbitMQ, Tomcat, and Nginx). Each VM has a CentOS Stream 9 or Ubuntu base image, configured with dedicated memory, private IP addresses, and provisioned via shell scripts for automatic setup.

Requirements
Vagrant >= 2.2.15

VirtualBox >= 6.1

vagrant-hostmanager plugin

Install the hostmanager plugin with:

bash
Copy code
vagrant plugin install vagrant-hostmanager
VM Overview
VM Name	Service	IP Address	Memory	OS	Provision Script
db01	MySQL	192.168.56.15	600 MB	CentOS Stream 9	mysql.sh
mc01	Memcache	192.168.56.14	600 MB	CentOS Stream 9	memcache.sh
rmq01	RabbitMQ	192.168.56.16	600 MB	CentOS Stream 9	rabbitmq.sh
app01	Tomcat	192.168.56.12	800 MB	CentOS Stream 9	tomcat.sh
web01	Nginx	192.168.56.11	800 MB	Ubuntu Jammy	nginx.sh
Configuration Highlights
Host Management: The hostmanager plugin manages the /etc/hosts file, ensuring that each VM hostname resolves correctly.
Network: Each VM uses a private network with assigned static IPs.
Memory Allocation: Configured based on each VM's requirements, varying between 600-800 MB.
Usage
Clone the repository and navigate to the directory:

bash
Copy code
git clone <repository-url>
cd <repository-directory>
Bring up the VMs:

bash
Copy code
vagrant up
SSH into a specific VM (e.g., db01):

bash
Copy code
vagrant ssh db01
To halt all VMs:

bash
Copy code
vagrant halt
To destroy all VMs (optional):

bash
Copy code
vagrant destroy -f
Provisioning
Each VM is provisioned using a shell script:

MySQL (db01): Provisions a MySQL server for database operations.
Memcache (mc01): Sets up a Memcache server for caching.
RabbitMQ (rmq01): Installs and configures RabbitMQ for messaging.
Tomcat (app01): Deploys Tomcat for web applications.
Nginx (web01): Installs Nginx as a web server.
These scripts are located in the same directory as the Vagrantfile.

Notes
GUI Mode: The web01 VM is set up with a GUI mode enabled in VirtualBox.
Public Network: Uncomment the public_network line in the configuration for web01 if external network access is needed.
This configuration offers a complete, isolated environment ideal for testing and developing distributed applications across different services.






