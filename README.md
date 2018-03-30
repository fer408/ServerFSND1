# ServerFSND1
Fernando Alarcon's Web server

Ip adress: http://18.217.97.70/
URL: ec2-18-217-97-70.us-east-2.compute.amazonaws.com

# Software installed:

easy_install

pip

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
-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEAxz+vu5tqnmoKmTvr2px9UkPZkxp0DFfexI6uPOiM97PTlfHa
0X70oKCXYILli/pKVjb79d3yx0RzDlQbEdR+Ks3KPIOctE82lCuVvBqjdrnh+GdN
UG0WpjaulISG+YEpf7V0snOPPZXSPNFJYLM+nISjqeS+9ZLVEW70QTZ+erwhM2y8
PmKmkV9fxz28CjbazyGjNQVsiLO4+ws96Dtxqk5poLdQCyaZpKqiAtvfzyvbVlsQ
kFGXhiNCffk7yi5LfTzbF1G2Y98szJI274Y/hQHnjUfPvZ6LzCiX1hU9rqob9Ii+
6SigDHcYcnhzJu3LTzJ8JIMIDu9n7S7nVREVHwIDAQABAoIBAEpJ2Yi2aqtD2E3H
xKlOnX81owKw40HS5VEd7aLyBdU5LBOFCFQB5M2a8rXeOB3XpS299HV4WlOnlspp
22nrc1scPWIQpDWqLyxRj9OBjx7uMW1/fpkVA1PXoYHoY7bVTJa8HhWG9oo8uRVJ
5vTx/881uRvYGMbRBzYny1QhMEksAN5XCBFp/LB8fJbLYTBV4WXeF9hm3JLiFAhV
IbOA+ay2QZ1or6gIhwE1POv5hbvt5BFDg4xAnwjN0Bv0bLWHIAdJUsVGIpsTc5A4
1GmT4eytP87MgwOufLadft5YzCzYzWn3sNdsuUnqv+B4PgybxtJkAncfA0RqK7QP
t6mBRjkCgYEA8XiPHaVnI5b/HyXSWetGiYZmXY8kAnHAguB9eZDiU9TiQ8AzQML8
HE8XzjyL21Axj32kuzkuFi0D2AwRpdKmHkdl3xCKALGjhjl1fTCBU6rnIIJSfWD9
Vtrvt/CJ4GxJxPiC+m20RJm4E63PmwFi0Kvht/TdTluwE6XIXUWJCUMCgYEA0zzE
rja7DrOqmElqNcaRAKr/oCQjo2vWJk+YkXLnyZJ/XpICnlMB7FFJN0/w+a3i3BmB
R+wNxf98KufeFj673PmQLoy6B0F13QlOm/zkV/9z1eNM43k/O/34X99DBvSQyBrH
/5n6WQLKe30cxl5/GAi2JCGNFHdrn7A0rue4aPUCgYBMAPprBmjUVu6uSyVOkDN/
jgIiaK+Y5V0G1MopvWS/pj4hvRlkxPq9nleL3prWyQMQeyeilnjfGgQfuIzFeOw4
k5iJAZeuaDtkQCmu4dmTEDP3k42LUT/sWrUhXGDJdswxZ1cyo90dypSZ/RdfXqxP
qgo98KDHzSw6wu+yC/T6KQKBgC/UJ5hmrg4TIkJfBRxt/HERRtYEuMkM5q1AAoSU
ZuUeNZa9KrichOf0M8bBZAe0lpRNdhdJ3IiDY6L3YzLYO4M6Qqo3lPuFl+FXdSQe
q7k9DwZT9BnhXy7/P1i93ZhakdmtLrGyNJwo5J33YyeLR+2yM0OVETOcIpNCu3sK
3pdtAoGBALQwgpmZflWnsLYqTBEq3foGVYE+ueQhGCyDI9IGiECN+zu52Ia9g0R/
x119SIcwxVUJ8ZNLx0OlX58psifv6CvFYoe0m6PuWvQRH2s461LIm5xlxQTFYB1s
9iv7FOfue6GML35dQ0dMHPJjYWLwALzuPtrrYg4xgTAalEnKoXKz
-----END RSA PRIVATE KEY-----

Summary of configurations made:

#Amazon lightsail Server Instance set-up:

1.Went to Amazon Lightsail website https://signin.aws.amazon.com/signin?redirect_uri=https%3A%2F%2Flightsail.aws.amazon.com%2Fls%2Fwebapp%3Fstate%3DhashArgs%2523%26isauthcode%3Dtrue&client_id=arn%3Aaws%3Aiam%3A%3A015428540659%3Auser%2Fparksidewebapp&forceMobileApp=0 and created an account.

2. I clicked the button "Create Instance"

3. Clicked on account to find key pair.

4. loged in from my local machine with the command: ssh -i ~/.ssh/LightsailDefaultPrivateKey-us-east-2.pem ubuntu@18.217.97.70


#Configuring the Server:

1. Added firewall and allowed access from 2200,80 and 123 by running the commands:

sudo ufw 2200

sudo ufw 80

sudo ufw 123


2. Updated the connections in the Amazon Lightsail connections tab for my instance to allow ports 2200 and 80 access otherwise when I attempt to log-in access is denied. 

3. Denied access to port 22 as asked in the specs.

4. updated packages and upgraded packages by running the commands:
sudo apt-get update and sudo apt-get upgrade

#Added new user and gave user sudo privileges

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

#Logging in to remote server:

1.Before attempting to log in I went and changed the port to 2200 in my  /etc/ssh/sshd_config file by typing the command:
sudo vim /etc/ssh/sshd_config and changing port 22 to port 2200

2.I re-started my server instance and was kicked out of the server in my local machine.

3.Logged in to my remote server as grader by typing the command:
ssh -i ~/.ssh/udacity_key.rsa -p 2200 grader@18.217.97.70

#Key-based authentication enforcement:

1.I went into my /etc/ssh/sshd_config file by typing the command:
sudo vim /etc/ssh/sshd_config and changing PasswordAuthentication to PasswordAuthentication no

#Disable root ssh login:

1.I went into my /etc/ssh/sshd_config file by typing the command:
sudo vim /etc/ssh/sshd_config and changed PermitRootLogin to PermitRootLogin no

#Installing packages I will need:

1. Went about installing the following packages:

easy_install

pip

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

libpq-dev python-dev

postgresql-contrib

#Running Apache server to see if things work:

1.Ran the command:
sudo a2enmod wsgi

2.Ran the command:
sudo service apache2 start

3.Visited servers ip of:
18.217.97.70 to verify it's working

#Download git to server.
1.went into /var/www directory with the command:
cd /var/www

2.made catalog with following command:
sudo mkdir catalog

3.I went into catalog directory with following command:
cd catalog

4.Gave grader owner privileges with the command:
sudo chown -R grader:grader catalog

5. Then I cloned my github repository to a new directory called catalog witht the
following command:
git clone https://github.com/fer408/FSNDServer.git catalog

#Changed time to UTC
1.I change the time on my server by typing the command sudo dpkg-reconfigure tzdata

#Setting up virtualenv and server.
1.I installed virtual machine witht the following commands:

sudo pip install virtualenv

sudo virtualenv venv

source venv/bin/activate

sudo chmod -R 777 venv

2.re-named my project.py file to __init__.py

3.used vim catalog/__init__.py to go into the file and change the lines where client_secrets.json is to 
/var/www/catalog/catalog/client_secrets.json 

4. I then went to the location where 
if __name__ == '__main__':
	app.secret_key=if __name__ == '__main__':
        app.secret_key = ''
        app.debug = True
        app.run(host='0.0.0.0',port=5000)
and changed it to:
if __name__ == '__main__':
        app.secret_key = 'gamers_secret_hoops'
        app.debug = True
        app.run(host='18.217.97.70',port=80)

5. I created a wsgi file for catalog by typing the command:
sudo vim catalog.wsgi

6. I then pasted this code in:
import sys
import logging
logging.basicConfig(stream=sys.stderr)
sys.path.insert(0, "/var/www/catalog/")

from catalog import app as application
application.secret_key = 'supersecretkey'


7.I then configure the virtual host by running the command:

sudo nano /etc/apache2/sites-available/catalog.conf

I pasted this clode inside of the file:
<VirtualHost *:80>
    ServerName [YOUR PUBLIC IP ADDRESS]
    ServerAlias [YOUR AMAZON LIGHTSAIL HOST NAME]
    ServerAdmin admin@35.167.27.204
    WSGIDaemonProcess catalog python-path=/var/www/catalog:/var/www/catalog/venv/lib/python2.7/site-packages
    WSGIProcessGroup catalog
    WSGIScriptAlias / /var/www/catalog/catalog.wsgi
    <Directory /var/www/catalog/catalog/>
        Order allow,deny
        Allow from all
    </Directory>
    Alias /static /var/www/catalog/catalog/static
    <Directory /var/www/catalog/catalog/static/>
        Order allow,deny
        Allow from all
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/error.log
    LogLevel warn
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

8. I changed to postgres user with the command:

sudo su - postgress

9.I then logged in to psql with the command:

psql

10.I ran the following commands to created user and databaser

CREATE USER catalog WITH PASSWORD 'password';

ALTER USER catalog CREATEDB;

CREATE DATABASE catalog WITH OWNER catalog;

\c catalog

REVOKE ALL ON SCHEMA public FROM public;

GRANT ALL ON SCHEMA public TO catalog;

\q

exit

11.Setup the database by typing :

python /var/www/catalog/catalog/database_setup.py

12.Setup the items in the database by running the command :

python /var/www/catalog/catalog/lotsofmenus.py

13.Ran the project by running the command:

python /var/www/catalog/catalog/__init__.py

14.ran command sudo a2ensite catalog to start catalog in Apache as mentioned in the classroom chat with other students 

15.Ran the command sudo service apache2 reload

16. Visited ip of 18.217.97.70

17.Sucess!

A special thanks to the following sources:
https://github.com/rrjoson/udacity-linux-server-configuration/blob/master/README.md
https://github.com/twhetzel/ud299-nd-linux-server-configuration
https://github.com/callforsky/udacity-linux-configuration
https://stackoverflow.com/questions/24001147/python-bind-socket-error-errno-13-permission-denied?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa
https://stackoverflow.com/questions/5439917/flaskr-syntaxerror
