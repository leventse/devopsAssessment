login: sudo -i

## 1 Installing Vagrant  
 prereq:  
  - sudo apt install virtualbox  
 install:  
  - sudo apt update  
  - curl -O https://releases.hashicorp.com/vagrant/2.2.6/vagrant_kubectl create namespace jenkins2.2.6_x86_64.deb  
  - sudo apt install ./vagrant_2.2.6_x86_64.deb/home/stikuser/k8s_ubuntu/  
## 2 Install git  
  - apt-get install git -y  
## 3 Install cluster  
  - git clone https://exxsyseng@bitbucket.org/exxsyseng/k8s_ubuntu.git      # Ubuntu k8s Cluster  
  - cd /home/stikuser/k8s_ubuntu/  
  - vagrant up  
  - vagrant status  
  - vagrant ssh kmaster   #login cluster  
## 4 Install Jenkins  
  - kubectl create namespace jenkins  
  - mkdir /home/vagrant/k8sfiles  
  - touch /home/vagrant/k8sfiles/jenkins-deployment.yaml  
  - nano /home/vagrant/k8sfiles/jenkins-deployment.yaml  
  - kubectl create -f /home/vagrant/k8sfiles/jenkins-deployment.yaml --namespace jenkins  
  - touch /home/vagrant/k8sfiles/jenkins-service.yaml  
  - nano /home/vagrant/k8sfiles/jenkins-service.yaml  
  - kubectl create -f /home/vagrant/k8sfiles/jenkins-service.yaml --namespace jenkins 
  - kubectl exec -n jenkins -it <Jenkins_pod> -- /bin/bash  
    - cat /var/jenkins_home/secrets/initialAdminPassword
  
  ## 4 Install Nexus  
  - mkdir /tmp/volume-local  
  - chmod -R 777 /tmp/volume-local  
  - kubectl create namespace nexus  
  - kubectl create namespace devops-tools  
  
  - touch /home/vagrant/k8sfiles/nexusPersistentVolume  
  - nano /home/vagrant/k8sfiles/nexusPersistentVolume  
  - kubectl create -f /home/vagrant/k8sfiles/nexusPersistentVolume  
  
  - touch /home/vagrant/k8sfiles/nexusPersistentVolumeClaim  
  - nano /home/vagrant/k8sfiles/nexusPersistentVolumeClaim  
  - kubectl create -f /home/vagrant/k8sfiles/nexusPersistentVolumeClaim  
  
  - touch /home/vagrant/k8sfiles/nexusDeployment  
  - nano /home/vagrant/k8sfiles/nexusDeployment  
  - kubectl create -f /home/vagrant/k8sfiles/nexusDeployment --namespace nexus  
  
  - touch /home/vagrant/k8sfiles/nexusService  
  - nano /home/vagrant/k8sfiles/nexusService  
  - kubectl create -f /home/vagrant/k8sfiles/nexusService  
  
