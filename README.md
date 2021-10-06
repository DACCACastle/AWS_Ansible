# AWS_Ansible

  
-- play book
---
- hosts: production
  remote_user: ec2-user
  become: true
  tasks:
    - name: Delete the log
      file:
       state: absent
       path: "/home/ec2-user/LogCheck_{{ ansible_fqdn }}.txt"
    - name: Send the script
      copy:
       src: /home/ec2-user/environment/shell.sh
       dest: /home/ec2-user
       mode: 0777
    - name: Transfers the script
      command: sh /home/ec2-user/shell.sh
    - name: Log file Get
      fetch:
       src: "/home/ec2-user/LogCheck_{{ ansible_fqdn }}.txt"
       dest: /home/ec2-user/environment/AWS_Ansible/Ansible_Log/
       flat: yes
