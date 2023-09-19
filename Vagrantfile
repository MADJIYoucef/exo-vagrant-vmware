$script = <<-SCRIPT
# Install kind
sudo curl -Lo /tmp/kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
sudo chmod +x /tmp/kind
sudo mv /tmp/kind /usr/local/bin/kind

# Install k9s
sudo curl -Lo /tmp/k9s_Linux_amd64.tar.gz https://github.com/derailed/k9s/releases/download/v0.27.4/k9s_Linux_amd64.tar.gz
sudo tar -xf  /tmp/k9s_Linux_amd64.tar.gz
sudo chmod +x ./k9s
sudo mv ./k9s /usr/local/bin/k9s

# Install kubectx 
sudo snap install kubectx --classic

# Install kubectl
sudo snap install kubectl --classic

# Install helm
sudo curl -fsSL -o /tmp/get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
sudo chmod 700 /tmp/get_helm.sh
sudo /tmp/get_helm.sh

# Install NodeJS
sudo apt update
sudo apt install nodejs -y
sudo apt install npm -y

# Install GItlab-runner
sudo curl -Lo /tmp/gitlab-runner_amd64.deb "https://gitlab-runner-downloads.s3.amazonaws.com/latest/deb/gitlab-runner_amd64.deb"
sudo dpkg -i /tmp/gitlab-runner_amd64.deb

SCRIPT


Vagrant.configure("2") do |config|
    config.vm.box = "hashicorp/bionic64" # You can use a different box if needed
    config.vm.box_version = "1.0.282"
    config.vm.box_download_insecure = true
    config.vm.provider "vmware_desktop" do |vmware|
      vmware.vmx["memsize"] = "2048" # Adjust the memory size as needed
    end
    config.vm.provision :docker
    config.vm.provision "shell" do |s|
        s.inline = $script
    end
    config.vm.provision :docker_compose
end
