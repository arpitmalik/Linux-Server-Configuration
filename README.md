# Linux-Server-Configuration
Final project of Udacity's Full Stack Web Developer NanoDegree

## About This Project 
You will take a baseline installation of a Linux server and prepare it to host your web applications.You will learn how to access, secure, and perform the initial configuration of a bare-bones Linux server. You will then learn how to install and configure a web and database server and actually host a web application.

## Server Details 
<ul>
<li> Public IP Address : http://13.126.72.40/</li>
<li> SSH Port : 2200 </li>
</ul>

## Create new instance on Lightsail

Start a new Ubuntu Linux server instance on Amazon Lightsail. To get started with lightsail follow the following instructions :
<ul>
<li> First, log in to Lightsail. If you don't already have an Amazon Web Services account, you'll be prompted to create one.</li>
<li> Once you're logged in, Lightsail will give you a friendly message with a robot on it, prompting you to create an instance. A Lightsail instance is a Linux server running on a virtual machine inside an Amazon datacenter. </li>
<li> Choose an instance type.For this project, you'll want a plain Ubuntu Linux image.</li>
<li> Choose your instance plan. The instance plan controls how powerful of a server you get.</li>
<li> Give your instance a hostname. Your instance's name will be visible to you and to the project reviewer. </li>
<li> Wait for it to start up.</li>
<li> Once your instance has started up, you can log into it with SSH from your browser. </li>
</ul>


## Server Security

<ul>
<li>Update all currently installed packages using <code>sudo apt-get update</code> command.</li>

<li>Upgrade all packages<code>sudo apt-get upgrade</code>.</li>

<li>Change SSH port from 22 to 2200. First add custom port 2200 on Lightsail. Login with port 22 using the command <code>ssh ubuntu@public_ip -i private key -p 22</code> , Run <code>sudo nano /etc/ssh/sshd_config</code>.Change the port from 22 to 2200. Once you're done restart sshd : <code>sudo service sshd restart</code>.</li>

<li> Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123)
<ol>
<li>To allow port 2200,<code>sudo ufw allow 2200/tcp</code>.</li>
<li>To allow port 80,<code>sudo ufw allow 80/tcp</code>.</li>
<li>To allow port 123,<code>sudo ufw allow 123/tcp</code>.</li>
<li>To enable firewall,<code>sudo ufw enable</code>.</li>
<li>To check status of firewall,<code>sudo ufw status</code>.</li>
</ol>
</li>
</ul>


## User named Grader
<ul>
<li> Create a new user account named grader using: <code>sudo adduser grader</code>.</li>
<li>  Give sudo permission to grader using <code>sudo usermod -aG sudo grader</code></li>
<li> Setup an SSH key for grader using the following instructions:
<ol>
<li> Switch to user grader using the command: <code> su grader </code></li>
<li> Now create a .ssh directory using <code>mkdir ~/.ssh</code> </li>
<li> Now copwy the key into a new folder run <code> sudo cp /home/ubuntu/.ssh/authorized_keys ~/.ssh/ </code> </li>
<li> Change the ownership rights using <code>sudo chown grader:grader /home/grader/.ssh/authorized_keys</code></li>
<li> For additional security run <code> sudo chmod 700 /home/grader/.ssh </code> . </li>
</ol></ul>


## Set standard timezone 
<ul>
<li> Run <code> sudo timedatectl set-timezone UTC </code> to Configure the local timezone to UTC.</li>
</ul>


## Additional Software requirements
<ul>
<li>Install Apache using <code>sudo apt-get install apache2</code></li>
<li>Install the libapache2-mod-wsgi package: <code> sudo apt-get install libapache2-mod-wsgi </code></li>
<li> Install and configure PostgreSQL using command <code> sudo apt-get install postgresql </code></li>
<li>Install python-pip using <code>sudo apt-get install python-pip</code></li>
<li> Install other dependancies like flask, bleach, oauth2client, psycopg2, sqlalchemy and requests using <code>sudo pip install flask bleach oauth2client psycopg2 sqlalchemy requests</code> command. </li>
<li> Install git using <code> sudo apt-get install git </code>
<li> Create a new database user named xyz using postgresql that has limited permissions to your catalog application database. </li>
</ul>

### Deploy the Item Catalog project.
<ul>
<li> Clone and setup your Item Catalog project from the Github repository you created earlier in this Nanodegree program.</li>
<li>  Set it up in your server so that it functions correctly when visiting your server’s IP address in a browser. Make sure that your .git directory is not publicly accessible via a browser! </li>
</ul>


## LICENSE

The content of this program is licensed under a <a href="https://creativecommons.org/licenses/by/2.0/">Creative Common Attribution</a>.
