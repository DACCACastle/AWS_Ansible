# AWS_Ansible

  
Ansible 설치
- sudo -y install python-pip
- sudo yum -y install python-pip
- sudo pip install --upgrade pip
- sudo pip install boto
- sudo amazon-linux-extras install ansible2
- sudo mkdir -p AWS_Ansible/group_vars/all/

사용 할 Playbook 생성
- sudo touch AWS_Ansible/playbook.yml

접근할 호스트를 인벤토리 형식으로 정의 ( 키는 AWS 키 사용 )
- vi /etc/ansible/hosts
- [Production]
slave1 ansible_host=등록할 호스트 ansible_user=ec2-user ansible_ssh_private_key_file=본인 키 경로
slave2 ansible_host=등록할 호스트 ansible_user=ec2-user ansible_ssh_private_key_file=본인 키 경로
- ansible all -m ping

Playbook 실행 비밀번호 지정
- ansible-vault create group_vars/all/pass.yml
- sudo ansible-vault edit group_vars/all/pass.yml
- ansible-playbook --ask-vault-pass playbook.yml 

실행 할 점검 쉘 스크립트 가져오기, 
- sudo wget https://app-data-44677.s3.ap-northeast-2.amazonaws.com/shell.sh
- ansible-playbook --ask-vault-pass playbook.yml 

![image](https://user-images.githubusercontent.com/77655831/136126185-2b640606-2472-4c76-a18a-5b67c5ba050d.png)

