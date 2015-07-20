# ADD Gemfile /app/Gemfile
#ADD Gemfile.lock /app/Gemfile.lock
#RUN cd /app; bundle install
#ADD . /app
#EXPOSE 4567
#WORKDIR /app
#CMD ["bundle", "exec", "middleman", "server"]
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
    config.vm.box = "ubuntu/trusty64"

    config.vm.provision "shell", inline: <<-SHELL
        apt-get -y update
        echo "[SLATE]: Installing ruby,rubydev, build-essential git"
        apt-get install -yq ruby ruby-dev build-essential git
        echo "[SLATE]: Installing bundler gem"
        gem install bundler
        echo "[SLATE]: Bundle install"
        cd /vagrant
        bundle install
        echo "[SLATE]: UP to here"
		
    SHELL
end

