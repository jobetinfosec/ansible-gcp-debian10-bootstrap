# Initial setup of Debian 10 server on Google Cloud Platform


## Description

Initial setup of Debian 10 server on Google Cloud Platform.

## Tasks

* System update
* Check if reboot is required
* Set no password in sudoers file
* Set timezone
* Install tcpdump and glances
* SSH hardening
* Add aliases to .bashrc file

## Tested on

Debian 10 server


## Requisites

a) Google Cloud Platform account<br />
b) A VPS server with Debian 10 already installed<br />
c) An SSH key pair, with the public key already installed in the remote server<br />



## Instructions

a) On your laptop create a working directory


b) In your working directory open a console window


c) Clone github repository

```
git clone https://github.com/jobetinfosec/ansible-gcp-debian10-bootstrap.git
```


d) Switch to playbook directory

```
cd ansible-gcp-debian10-bootstrap
```


e) Open the hosts file

```
nano hosts
```

f) Replace <TEMPORARY_ITEMS> with your own data:

`<SERVER_IP>`		replace <SERVER_IP> with the actual IP address of your remote server<br />
`<SUDO_USER_NAME>`	replace it with sudo user's name<br />
`<SUDO_USER_PASSWORD>`	replace it with sudo user's password<br />

then save and close the file


g) Open the defaults main.yml file

```
nano roles/basic/defaults/main.yml
```

h) Replace <TEMPORARY_ITEMS> with your own data:

`<USER_NAME>`		replace <USER_NAME> with the name of sudo user<br />
`<PASSWORD_HASH>`	replace it with the hash of sudo user's password (to create a password hash use mkpasswd --method=sha-512 command. If mkpasswd is not installed, install it with apt-get install whois)<br />
`<PUBLIC_KEY_NAME>`	replace it with your public key's name<br />
`<TIMEZONE>`		replace it with your timezone<br />

then save and close the file


i) Check if you are able to ping remote server

```
ansible -m ping all
```

You should receive a SUCCESS message


j) Check if any error shows up

```
ansible-playbook bootstrap.yml --check
```


k) Launch installation

```
ansible-playbook bootstrap.yml
```


## Licence

MIT licence

## Author Information

Created by Roberto Jobet (sysadmin@wpsecurity.press).

Don't hesitate to open an Issue if you find any bug or have suggestions.
