# ServerFSND1
Fernando Alarcon's Web server

Ip adress: http://18.217.97.70/
URL: ec2-18-217-97-70.us-east-2.compute.amazonaws.com

#Software installed:

httplib2 
oauth2client 
sqlalchemy 
psycopg2 
sqlaclemy_utils 
requests 
Flask
virtualenv
postgresql
git
apache2
mod_wsgi 

#Grader ssh-key:

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDTeK0fAXh0LMA/GRsz6uwKaqL98t8HCm7WaXVbEXb7DNvLEtdWOSArSmS5bB9m9vLOBA4gtJLooJYqPlz2ab+qq2pAKm4kwxwPgzjDySWRroJjg2P6r/MdpgYovNqtGgfMmXrzJ3KyJRok+/zj82j5LY9aQaSpEHumIBmJspsiVtxGLeBZ1bEzmD2n4+vSN1yCHHRYezsHD/ABmYAjXkP3oe/oLd+TjGv1VVY2j5aIkikYlEgJINQx/cCqRwCeFeC2QCOVAH+E4XCmWIza9F7C7/6G1bqXQrOtkMLv5Br9jSuZFjK7ZUKVe6PKoY/ZZ/ehEeC3CGV377gPKl6JCyCR alarc@DESKTOP-B66OI3S

#Summary of configurations made:

Amazon lightsail Server Instance set-up:

1.Went to Amazon Lightsail website https://signin.aws.amazon.com/signin?redirect_uri=https%3A%2F%2Flightsail.aws.amazon.com%2Fls%2Fwebapp%3Fstate%3DhashArgs%2523%26isauthcode%3Dtrue&client_id=arn%3Aaws%3Aiam%3A%3A015428540659%3Auser%2Fparksidewebapp&forceMobileApp=0 and created an account.

2. I clicked the button "Create Instance"

3. Clicked on account to find key pair.

4. loged in from my local machine with the command: ssh -i ~/.ssh/LightsailDefaultPrivateKey-us-east-2.pem ubuntu@18.217.97.70


Configuring the Server:

1. Added firewall and allowed access from 2200,80 and 123 by running the commands:
sudo ufw 2200
sudo ufw 80
sudo ufw 123


2. Updated the connections in the Amazon Lightsail connections tab for my instance to allow ports 2200 and 80 access otherwise when I attempt to log-in access is denied. 

3. Denied access to port 22 as asked in the specs.

4. updated packages and upgraded packages by running the commands:
sudo apt-get update and sudo apt-get upgrade

# Added new user and gave user sudo privileges

1. Created new user grader with command:
sudo adduser grader
2. Gave said user sudo privileges by using the command cd sudo vim /etc/sudoers.d/grader
3. Added this line to the empty file:
grader ALL=(ALL:ALL) ALL
4.Updated file /etc/hosts to include this line:
127.0.1.1 ip-10-20-37-65
in order to prevent an error message as prescribed by a external source I used in order to set up my project.

#Create keygen pair for grader

1.In my local machine I made the keygen by typing the following command:
ssh-keygen -f ~/.ssh/udacity_key.rsa
2. I then read the contents of the file where the key is located by typing the command:
cat ~/.ssh/udacity_key.rsa.pub
3. In my server I moved to graders folder by typing:
cd /home/grader
4. I then created a .ssh directory by typing:
mkdir .ssh
5. I then created the authorized_keys file by typing:
vim .ssh/authorized_keys
6. I pasted the contents of my udacity_key.rsa.pub file 
7. I changed the .ssh folders permission by typing:
sudo chmod 700 /home/grader/.ssh
8. I changed the authorized_keys permissions by typing:
sudo chmod 644 /home/grader/.ssh/authorized_keys
9.Gave grader owner rights by typing the command:
sudo chown -R grader:grader /home/grader/.ssh

#Logging in to remote server
1.Before attempting to log in I went and changed the port to 2200 in my  /etc/ssh/sshd_config file by typing the command:
sudo vim /etc/ssh/sshd_config and changing port 22 to port 2200
2.I re-started my server instance and was kicked out of the server in my local machine.
3.Logged in to my remote server as grader by typing the command:
ssh -i ~/.ssh/udacity_key.rsa -p 2200 grader@18.217.97.70

#Key-based authentication enforcement
1.I went into my /etc/ssh/sshd_config file by typing the command:
sudo vim /etc/ssh/sshd_config and changing PasswordAuthentication to PasswordAuthentication no

#Disable root ssh login
1.I went into my /etc/ssh/sshd_config file by typing the command:
sudo vim /etc/ssh/sshd_config and changed PermitRootLogin to PermitRootLogin no

#Installing packages I will need
1. Went about installing the following packages:

httplib2 
oauth2client 
sqlalchemy 
psycopg2 
sqlaclemy_utils 
requests 
Flask
virtualenv
postgresql
git
apache2
mod_wsgi 

#Running Apache server to see if things work




