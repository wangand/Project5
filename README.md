# Project5
Configuring Linux Web Servers

## Access

### IP address

52.37.231.200

### Port Number for ssh

2200

### URL

http://52.37.231.200/

### Password

kylm@KarhuZx3

## Installed Software and Configuration Summary

Checked for updates with sudo apt-get update

Upgraded with sudo apt-get upgrade

Added user: grader

Gave grader sudo access

Added a authorized key for grader

Configured UFW to block all incoming by default

Configured UFW to allow all outgoing by default

Configured UFW to allow ports: 2200/tcp, web, and ntp

Enabled UFW

Installed Apache2

Installed PostgreSQL

Added catalog user in PostgreSQL

Allowed local password authentication for psql in pg_hba.config file

Made sure no remote addresses in pg_hba.conf file

Installed Git

Installed pip

Installed Flask

Installed SQLAlchemy

Installed Flask-Session

Added catalog project to /var/www/html via git

Modified database_setup to use psql

Added cache directory to store session data

## Third Party Resources

newcoder.io/scrape/part-3/

## Notes

Cache directory appears to require rwx access for all users to function correctly. I did try to change permissions to rw- and r-x for all users but sessions seem to work incorrectly unless the cache directory has rwx access for all users.

## Detailed installation log

```
ssh -i ~/.ssh/udacity_key.rsa root@52.37.231.200
sudo apt-get update
sudo apt-get upgrade

sudo adduser grader

ssh-keygen
mkdir .ssh
touch .ssh/authorized_keys
chmod 700 .ssh
chmod 644 .ssh/authorized_keys

sudo vim /etc/ssh/sshd_config
sudo service ssh restart

sudo ufw status
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 2200/tcp
sudo ufw allow www
sudo ufw allow ntp
sudo ufw enable

sudo apt-get install apache2
sudo apt-get install libapache2-mod-wsgi
sudo apt-get install postgresql
sudo apt-get install python-pip
sudo pip install httplib2
sudo pip install --upgrade google-api-python-client
sudo apt-get install python-psycopg2
sudo pip install Flask
sudo pip install sqlalchemy 
sudo pip install Flask-Session

sudo vim /etc/postgresql/9.3/main/pg_hba.conf
sudo service postgresql restart
sudo -u postgres psql
CREATE USER catalog;
ALTER USER catalog PASSWORD 'password';
CREATE DATABASE catalog;

sudo vim /etc/apache2/sites-enabled/000-default.conf
WSGIPythonPath
WSGIScriptAlias / /var/www/html/myapp.wsgi
```