# Hello and welcome to maeltht tutorial

In this demo, we are setting up Ansible Server and several target Servers to deploy a web application in a containerized environment.

The goal is to have 1 container running as our Ansible Server and a totall of 6 containers (target Servers) hosting our  web application.

This is a great hand on practice for basic concept of Docker, Ansible, Web Servers. 

# Prerequesites

          Make sure you have Docker install.
          you can follow this link to install Docker for your Operating system https://docs.docker.com/engine/install/ubuntu/

# Demo Step
    - Step 1
        
       $ docker pull xmaeltht/ubuntu-ansible
       $ docker run -itd xmaeltht/ubuntu-ansible            # Running this 7 times will provide you with 7 container pick one and used it as your ansible server.
       $ docker exec -it <your ansible containerID/name> bash      # will take you inside the container and from this container run the following commands
       $ apt update && apt install git -y
      
        
    - Step 2

       $ ansible --version                    # will provide you the ansible version running 
       $ vim /etc/ansible/ansible.cfg         # enable host key checking by removing the (#) sign in front of the ligne #host_key_checking = False
       $ git clone https://github.com/maeltht/ansible-container-demo.git
       $ cp /ansible-container-demo/hosts /etc/ansible/hosts
       $ vim /etc/ansible/hosts # Make sure the inventry file has the correct IP address of each of your containers, edit the inventry file according to all the                                    container ip address running and remember to NOT include the Ansible container, just the 6 target containers.
      

    - Step 3
        
        # At this point run the ansible ping command on all host to check the connectivity.
        
       $ cd /ansible-container-demo/ 
       $ ansible all -m ping               # Once you are able to verify the connectivity go ahaed and run your playbook.yml        
       $ ansible-playbook playbook.yml
        

        
```
        Note: if having and issue 

            # run this command to fix the issue

                ansible all -a "service mysql start"
```
    - Step 4
        
        # Check the browser on port 8080 from any of the container ip adress 

            localhost:8080      or      containerIP:8080


        
