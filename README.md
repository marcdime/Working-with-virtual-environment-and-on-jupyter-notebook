# Working-with-virtual-environment-and-on-jupyter-notebook 

Ubuntu 18.04, venv, pew or conda


## An new instance EC2

- We create an AMI t2.micro Ubuntu 18.04 having following features
  - Public IP : enable
  - Inbound security group : open port 8888 (TCP) for jupyter notebook, port 22 for SSH

## Taking control of the instance by SSH

- Open server-client Putty or whatever that works : username for Ubuntu server is *"ubuntu"* (for ami linux *"ec2-user"*) 
- Always update the system first using :

```
ubuntu@ip-$ sudo apt-get update  
```
*(for linux : $ sudo yum -y update)*

- Check if python or pip (packages manager) exist :

```
ubuntu@ip-$ python --version 
```

- If not, let's install python, pip :

```
ubuntu@ip-$ sudo apt-get install python3      *# python version 3*
```
```
ubuntu@ip-$ python3 --version 
```
> Python 3.6.9

then 
```
ubuntu@ip-$ sudo apt-get install python3-pip    # pip3 is installed with python3
```
```
ubuntu@ip-$ pip3 --version 
```
> pip 9.0.1 from /usr/lib/python3/dist-packages (python 3.6)


