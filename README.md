# molecule-minc-toolkit-demo

## Requirements
* Python
* Docker
* VirtualBox
* Vagrant
* pip

## Setup
Install `virtualenv`:
```pip install virtualenv
```

Create the virtual environment:
```
virtualenv .virtualenvs/molecule
```

Activate the virtual environment:
```
source ~/.virtualenvs/molecule/bin/activate
```

After activating the virtual environment, install the following Python packages:
```
pip install ansible molecule docker-py python-vagrant
``` 

## Usage
List all available instances:
```
molecule list
```
```
--> Validating schema /home/john/ansible-devel/roles/molecule-minc-toolkit-demo/molecule/vagrant/molecule.yml.
Validation completed successfully.
--> Validating schema /home/john/ansible-devel/roles/molecule-minc-toolkit-demo/molecule/default/molecule.yml.
Validation completed successfully.
Instance Name    Driver Name    Provisioner Name    Scenario Name    Created    Converged
---------------  -------------  ------------------  ---------------  ---------  -----------
ubuntu-vagrant   vagrant        ansible             vagrant          false      false
ubuntu-docker    docker         ansible             default          false      false
```

Create an instance:
```
molecule create
```
This will create an instance using the default driver, Docker.

Or create an instance using Vagrant:
```
molecule create --scenario-name vagrant
```

Run the `minc-toolkit` Ansible role on the Docker instance:
```
molecule converge
```

Or run the `minc-toolkit` Ansible role on the Vagrant instance:
```
molecule converge --scenario-name vagrant
```

Log in to the Docker instance:
```
molecule login
```

Or log in to the Vagrant instance:
```
molecule login --scenario-name vagrant
```

Destroy the instances:
```
molecule destroy
molecule destroy --scenario-name vagrant
```
