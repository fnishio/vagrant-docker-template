VAGRANTFILE_API_VERSION = "2"

Vagrant.configure("2") do |config|

  # mongo conainer
  config.vm.define "mongo" do |v|
    v.vm.provider "docker" do |d|
      d.name = "mongo"
      # if you want to build the image before execution,
      # enable d.build_dir instead of d.name.
      # d.build_dir = "./mongo"
      d.image = "mongo:2.6"
      d.volumes = ["/vagrant-log:/var/log"]
      d.ports = ["27017:27017"]
      d.vagrant_vagrantfile = "./vagrant-docker.proxy"
      d.remains_running = false
#      d.link "mongo:mongo"
      d.cmd = ["--logpath", "/var/log/mongo.log"]
    end
  end

  # node container
  config.vm.define "node" do |v|
    v.vm.provider "docker" do |d|
      d.name = "node"
      d.image = "node:0.10"
      d.volumes = ["/vargrant-app:/usr/src/myapp"]
      d.ports = ["3000:3000"]
      d.vagrant_vargrantfile = "./vagrant-docker.proxy"
      # d.cmd = ["node", "bin/www"]
      d.cmd = ["node"]
    end
  end

end
