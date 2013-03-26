Vagrant::Config.run do |config|

  config.vm.box = "precise32"

  config.vm.forward_port 80, 4567

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "vagrantchef/cookbooks"
    chef.add_recipe("apt")
    chef.add_recipe("mysql::server")
    chef.add_recipe("php")
    chef.add_recipe "php::module_mysql"
    chef.add_recipe('php-fpm')
    chef.add_recipe("nginx")
    chef.add_recipe("varnish")
    chef.add_recipe("git")
    chef.add_recipe('zsh')

    chef.json = {
      :mysql => {
        :server_root_password => "",
        :server_repl_password => "",
        :server_debian_password => ""
      },
      :varnish => {
        :listen_port => 80,
      },
      :nginx => {
        :listen_port => 8080,
      }
    }

  end

end
