# ansible-examples
Steps to implement Ansible
1. Create 2 servers ansible_server and target_server
   <img width="815" height="187" alt="image" src="https://github.com/user-attachments/assets/d35d1509-0f24-4967-a8fe-625607140a69" />

2. On Ansible Server (Ubuntu Server) :
   Perform following steps:
   a.  sudo apt update -- Update apt package on new machine
   b.  ansible --version - check Ansible if installed
   c.  sudo apt install ansible - Install ansible
   d ansible --version - Check Ansible version
   e. In /.ssh/ create private and public key using ssh-keygen
     Run ssh-keygen command
   f. Check if ssh <target-ip-address> is working or not.
   g. Copy the public key created in step e i.e one with *.pub
   h. Connect to <target-ip-address>  on separate terminal
      h.1 Edit the file using vim authorized_keys and the paste the public key of ansible server
   i. Test if the ansible adhoc command works from the ansible_server using:
       ansible -i inventory all -m "shell" -a "touch demo_instructions.txt"

   Expected Result -  You should find a file created on Target server
3. Next, we shall create a first ansible playbook
   3.a Create and edit using :
      vim first-playbook.yml
   3.b Check the contents of the file shared in the first-playbook.yml file in the github repository.
   3.c Create an inventory file in same location and add the ip address of target server. 
   3.d Run the ansible-playbook command as a dry run to check for errors if any in the syntax :
     ansible-playbook -i inventory first-playbook.yml --check
   3.e If all good, run the ansible-playbook command as below
     ansible-playbook -i inventory first-playbook.yml
   Expected Result -  connect to the target server and check the status of nginx if running
   using
  **   systemctl status nginx**
   O/p : ● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: enabled)
     Active: active (running) since Thu 2026-05-21 06:41:12 UTC; 1min 44s ago
