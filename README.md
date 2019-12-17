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
ubuntu@ip-$ sudo apt-get install python3          # python version 3
```
```
ubuntu@ip-$ python3 --version 
```
> Python 3.6.9

then 
```
ubuntu@ip-$ sudo apt-get install python3-pip      # pip3 is installed with python3
```
```
ubuntu@ip-$ pip3 --version 
```
> pip 9.0.1 from /usr/lib/python3/dist-packages (python 3.6)

## Install jupyter
In this section we will install jupyter and run jupyter notebook locally on the instance. 

Copy this command line:

```
ubuntu@ip-$ pip3 install jupyter
```

Launch jupyter : 

```
ubuntu@ip-$ jupyter notebook --ip=0.0.0.0
```

** option --ip is important to get access to the localhost of the instant **

We will see the last part of the output : 
>     To access the notebook, open this file in a browser:
        file:///home/ubuntu/.local/share/jupyter/runtime/nbserver-7752-open.html
    Or copy and paste one of these URLs:
        http://localhost:8888/?token=d472052d79ce63cc4631e70b69d758d2c47f72f45c84348a
     or http://127.0.0.1:8888/?token=d472052d79ce63cc4631e70b69d758d2c47f72f45c84348a


Copy the link https and paste into a browser, then replace *localhost* or *local ip address* to the public ip address of the instance



