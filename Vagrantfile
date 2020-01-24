
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.provider :virtualbox do |vb, override|
    vb.name = "vmtask3"
    vb.memory = 2048
    vb.cpus = 2
    dskFormat = "vdi"
    dskCount = 4
    (1..dskCount).each do |i|
    
      disk = "./dsk" + "#{i}" + "." + dskFormat
      if !File.exist?(disk)
        vb.customize [ "createhd", "--filename", disk, "--variant", "Fixed", "--size", 350 ]
        vb.customize [ "storageattach", "vmtask3" ,'--storagectl', 'SATAController', '--port', i, '--device', 0, '--type', 'hdd', '--medium', disk]
      end
    end

  end
  config.vm.provision :shell, :path => "provision.sh", run: "always"
end
