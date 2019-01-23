servers=[
{
  :hostname => "opsschool-v",
  :ip => "192.168.100.20",
  :box => "ubuntu/trusty32",
  :ram => 1024,
  :cpu => 1,
  :provisions => ["download-percona.sh"]
}
]
Vagrant.configure(2) do |config|
  servers.each do |machine|
    config.vm.define machine[:hostname] do |node|
        machine [:provisions].each do |script|
	   node.vm.provision :shell, :path => script
        end
      node.vm.box = machine[:box]
      node.vm.hostname = machine[:hostname]
      node.vm.network "private_network", ip: machine[:ip]
      node.vm.provider "virtualbox" do |vb|
        vb.memory = machine[:ram]
        vb.cpus = machine[:cpu]
      end
    end
  end
end
