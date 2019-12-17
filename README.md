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

## Install jupyter and run jupyter noterbook
In this section we will install jupyter and run jupyter notebook locally on the instance. 

Copy this command line:

```
ubuntu@ip-$ pip3 install jupyter
```

Launch jupyter : 

```
ubuntu@ip-$ jupyter notebook --ip=0.0.0.0
```
option **--ip** is important to get access to the localhost of the instant


We will see the last part of the output : 

>     To access the notebook, open this file in a browser:
>        file:///home/ubuntu/.local/share/jupyter/runtime/nbserver-7752-open.html
>    Or copy and paste one of these URLs:
>        http://localhost:8888/?token=d472052d79ce63cc4631e70b69d758d2c47f72f45c84348a
>     or http://127.0.0.1:8888/?token=d472052d79ce63cc4631e70b69d758d2c47f72f45c84348a

Copy the link https and paste into a browser, then replace *localhost* or *local IP address* by the public IP address of the instance
and jupyter notebook is loaded !

**Some issues can be listed in this step :**
    - Ctrl + C to stop the jupyter notebook (JN) and back to the terminal of ubuntu    
    - When launch again JN, a new port can be attributed (>8888) because the previous one is still working (for some reasons). In this cas, check with command line:
          ```
          ubuntu@ip-$ jupyter notebook list
          ```    
          go to the *runtime* folder:  
          ```
          ubuntu@ip-$ jupyter --paths
          ```
          and delete all files in this folder:
          ```
          ubuntu@ip-$ (sudo) rm -r -f ./* 
          ```
          close the terminal, open it again and launch again JB
          
    - To run the JB in the background at the same time of the terminal, use this command:
    
          ```
          ubuntu@ip-$ nohup jupyter notebook --ip=0.0.0.0
          ```
          then Ctrl+C to exit
    - To create a new kernel and JN environment (in the current (virtual) environment), use these commands:
    
          ```
          ubuntu@ip-$ pip3 install ipykernel
          ```
          ```
          ubuntu@ip-$ python3 -m ipykernel install --user --name=nameof_new_JB_env
          ```
          refresh the browser to have this new JB environement
  
## 



