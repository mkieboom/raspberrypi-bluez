###### Introduction
This ansible project downloads, compiles and installs Bluez-5.41 including all pre-requisites on the Raspberry PI. To run, execute the following steps:

###### 1. login as 'pi' user

###### 2. Enable SSH server by launching raspi-config
```
sudo raspi-config
```
Go to menu option "5 - Interfacing Options" and enable "P2 - SSH"

###### 3. Change to root user
```
sudo su -
```

###### 4. Ansible requires SSH keyless to connect to run the script
```
ssh-keygen -t rsa -f /root/.ssh/id_rsa -q -P ""
cat /root/.ssh/id_rsa.pub >> /root/.ssh/authorized_keys
```

###### 5. Install Ansible and Git
```
echo "deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main" >> /etc/apt/sources.list
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
apt-get update
apt-get install -y ansible git
```

###### 6. Clone the Raspberry PI Bluez github project
```
git clone https://github.com/mkieboom/raspberrypi-bluez
cd raspberrypi-bluez
```

###### 7. Run the ansible scripts to install Bluez
```
ansible-playbook -i myhosts/raspberrypi_localhost raspberrypi-deployment.yml
```

###### 8. Reboot the Raspberry PI
```
reboot
```
