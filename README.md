# AWS_Ansible

  
Ansible 설치
sudo -y install python-pip
sudo yum -y install python-pip
sudo pip install --upgrade pip
sudo pip install boto
sudo amazon-linux-extras install ansible2
sudo mkdir -p AWS_Ansible/group_vars/all/

사용 할 Playbook 생성
sudo touch AWS_Ansible/playbook.yml

접근할 호스트를 인벤토리 형식으로 정의 ( 키는 AWS 키 사용 )
vi /etc/ansible/hosts
[Production]


ansible all -m ping
ansible-playbook --ask-vault-pass playbook.yml 
접근 
ansible-vault create group_vars/all/pass.yml
   12  sudo ansible-vault create group_vars/all/pass.yml
   13  sudo ansible-vault edit group_vars/all/pass.yml
   35  sudo wget https://app-data-44677.s3.ap-northeast-2.amazonaws.com/shell.sh
  186  ansible-playbook --ask-vault-pass playbook.yml 
