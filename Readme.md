# Hello and welcome to my little demo tutorial

Thi is just to help few to have a basic understating of ansible regarding the env they are in.
A lot of you might be using windows and as of today ansible is still not supported on windows OS but with WSL you can have and env runing ansible
   Therefore this little demo is to help you witha quick start using container instead of VM


This is not a perfect Readme but I will update it as time goes on. 

# Prerequesites

        - make sure you have a container runtime running

# Demo Step
    - Step 1
        
        Docker pull xmaeltht/ubuntu-ansible
        Docker run -itd xmaeltht/ubuntu-ansible # Run this 7 times will provide you with 7 container pick one and used it as your ansible server.
        Docker exec -it <your ansible containerID/name>     # will take you inside the container and from this container run ```git clone https://github.com/maeltht/ansible-container-demo.git```
        
    - Step 2

        ansible --version  # will provide you the ansible version running 
        vim /etc/ansible/host   # Edit the inventry file according to all the container ip address running in your environment used the hosts file in the code repo as template

    - Step 3

        # At this point run the ansible ping command on all host to check the connectivity.

                ansible all -m ping

        # Once you are able to verify the connectivity go ahaed and run your playbook.yml

                ansible-playbook playbook.yml
```
        Note: if having and issue 

            # run this command to fix the issue

                ansible all -a "service mysql start"
```
    - Step 4
        
        # Check the browser on port 8080 from any of the container ip adress 

            localhost:8080      or      containerIP:8080


        