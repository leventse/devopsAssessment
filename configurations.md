1 Installing Vagrant
 prereq: 
  sudo apt install virtualbox
 install:
  sudo apt update
  curl -O https://releases.hashicorp.com/vagrant/2.2.6/vagrant_2.2.6_x86_64.deb
  sudo apt install ./vagrant_2.2.6_x86_64.deb/home/stikuser/k8s_ubuntu/
2 Install git
  apt-get install git -y
3 Install cluster
  git clone https://exxsyseng@bitbucket.org/exxsyseng/k8s_ubuntu.git      # Ubuntu k8s Cluster
  cd /home/stikuser/k8s_ubuntu/
  vagrant up
  vagrant status
  vagrant ssh kmaster   #login cluster
  
