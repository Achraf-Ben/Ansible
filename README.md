# Ansible
Ansible Playbooks and Templates

# wordpress-ansible-0.3

The variables you can change in the wordpress.yml playbook:
    vars:
    username: username
    userpass: user password
    hostname: hostname.com
    website_name: hostname.com
    public_key: path/to/public/key.pub
    wp_mysql_db: database server (localhost or a remote server)
    wp_mysql_user: database username

All roles and tasks you can find in the wordpress-ansible-0.3 playbook:

    - bootstrap
        -roles/bootstrap/tasks
        Executing ping command, Hold on...
        Checking Network Connection
        Executing apt-get update command
        Executing apt-get dist-upgrade command
        Setup FQDN
        Setup Timezone to UTC
        Setup UMASK
        Installing NTP Service

    - security
        -roles/tasks/ssh
        Ensure sudo group is present
        Ensure sudo group has sudo privileges
        Ensure passwordless sudo for user ansible
        Generating Random Password for {{ username }}, Hold on...
        Create default user
        Add authorized_keys
        Ensure authorized_keys permissions are 0644
        Disable root login
        Disable password authentication
        Ensure sshd_config permissions are 0600

        -roles/security/tasks/fail2ban.yml
        Installing Fail2ban
        Copying Fail2ban Configuration File

        -roles/security/tasks/uwfirewall.yml
        Enable firewall
        Allow HTTP (port 80)
        Allow HTTPS (port 443)
        Allow SSH (port 22)

    - appserver
        Update apt cache
        Install required software
            - python3-simplejson
            - apache2
            - mysql-server
            - php
            - libapache2-mod-php
            - php-mcrypt
            - python-mysqldb
        Install php extensions
            - php-mysql
            - php-cli
            - php-curl
            - php-gd
            - php-xml
            - php-mbstring
            - php-fpm
        Install required software packages
            - bc
            - tar
            - sudo
            - wget
            - curl
            - git
            - htop
            - coreutils
            - libssl-dev
            - lsb-release
            - python3-dev
            - python3-pip
            - ca-certificates
            - apt-transport-https
            - python-software-properties
            - software-properties-common
            - libmysqlclient-dev
        Installing PIP software, Hold on...
        Installing passlib software, Hold on...
        Installing MySQL-python software, Hold on...

    - wordpress
        Download WordPress
        Extract WordPress
        Update default Apache site
        Copy sample config file
        Generating Random Password for {{ wp_mysql_user }}
        Update WordPress config file

    To do:
    - mysql
    - letsencrypt