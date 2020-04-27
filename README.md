# Ansible

This project is about **Vagrant** and **Ansible** and some useful playbooks for **Ansible**.

## Getting Started

At first vagrant up two boxes (**Ubuntu 18.04** and **Windows Server 2019**) in **VirtualBox**. Then, install **Ansible** and **PyCharm IDE** in control machine (Ubuntu 18.04) to up and run the projects.

### Prerequisites

* **Vagrant**
* **VirtualBox**
* **Ansible**
* **PyCharm IDE**

## Windows-server
Will apply on the `windows-server` type host.

* Make sure powershell is up to date in windows host. Ansible requires PowerShell version 3.0 and .NET Framework 4.0 or newer to function on older operating systems like Server 2008 and Windows 7.
* Make sure [configureremotingforansible.ps1](https://docs.ansible.com/ansible/latest/user_guide/windows_setup.html) is configured in Windows host.

## Usage

### Define the host

Hosts can be defined inside `/etc/ansible/hosts`, e.g.,
```sh
[local]
localhost
```

Otherwise, you can use the `-i hosts` option to take the local `hosts` file.

### Apply role
Run ansible-playbook with given yaml file name, by default, will apply the
stack on all host.

e.g.,

```sh
$ ansible-playbook ntp.yml
```

If you wanna run at localhost without ssh, then just add `-c local`, e.g.,
```sh
$ ansible-playbook -c local  ntp.yml
```

You can also modify the playbook to change the default role.

For instance.
```sh
- hosts: servers
  roles:
     - { role: win }
```


### Installation

* Download and install **Vagrant** from here: [Vagrant](https://www.vagrantup.com/) 

* Download and install **VirtualBox** from: [VirtualBox](https://www.virtualbox.org/)

* Use the following steps to install **Ansible** in your control machine:

```
sudo apt-get update && sudo apt-get update
sudo apt-get install software-properties-common
sudo apt-add-repositories --yes --update ppa:ansible/ansible
sudo apt-get install ansible
```

* Use the following steps to install **PyCharm IDE** in the control machine:
```
sudo snap install pycharm-community --classic
cd [Location to ./pycharm.sh]
./pycharm.sh
``` 

## Authors

* **Anwar Hossain** - *Initial work* - [cseanwar](https://github.com/cseanwar/ansible)

## Acknowledgments

The project is highly inspired by the [ansible-examples](https://github.com/ansible/ansible-examples).