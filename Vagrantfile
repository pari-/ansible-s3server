require 'pathname'

hn = Pathname.new(Dir.pwd).basename.to_s.gsub('_','-');

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = ENV['VAGRANT_CONFIG_VM_BOX'] || 'parallels/debian-8.7'
  config.vm.hostname = hn

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "test.yml"
    ansible.sudo = true
    ansible.galaxy_role_file = "requirements.yml"
#    ansible.tags = "configure"
#    ansible.groups = {
#      "abc" => ['a'],
#    }
  end
end
