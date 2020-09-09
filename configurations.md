1 Installing Vagrant  
 prereq:  
  sudo apt install virtualbox  
 install:  
  sudo apt update  
  curl -O https://releases.hashicorp.com/vagrant/2.2.6/vagrant_kubectl create namespace jenkins2.2.6_x86_64.deb  
  sudo apt install ./vagrant_2.2.6_x86_64.deb/home/stikuser/k8s_ubuntu/  
2 Install git  
  apt-get install git -y  
3 Install cluster  
  git clone https://exxsyseng@bitbucket.org/exxsyseng/k8s_ubuntu.git      # Ubuntu k8s Cluster  
  cd /home/stikuser/k8s_ubuntu/  
  vagrant up  
  vagrant status  
  vagrant ssh kmaster   #login cluster  
4 Install Jenkins  
  kubectl create namespace jenkins  
  mkdir /home/vagrant/k8sfiles  
  touch /home/vagrant/k8sfiles/jenkins-deployment.yaml  
  nano /home/vagrant/k8sfiles/jenkins-deployment.yaml  
  kubectl create -f /home/vagrant/k8sfiles/jenkins-deployment.yaml --namespace jenkins  
  touch /home/vagrant/k8sfiles/jenkins-service.yaml  
  nano /home/vagrant/k8sfiles/jenkins-service.yaml  
  kubectl create -f /home/vagrant/k8sfiles/jenkins-service.yaml --namespace jenkins  
  
  
  
