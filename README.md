# Project5
Configuring Linux Web Servers

## Access

### IP address

52.37.71.55

### Port Number for ssh

2200

### URL

http://52.37.71.55

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

## Third Party Resources

newcoder.io/scrape/part-3/