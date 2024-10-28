# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.network "forwarded_port", guest: 80, host: 80
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = 4
  end
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update #&& apt-get upgrade -y

    apt-get install -y \
          build-essential \
          curl \
          git \
          wget \
          vim \
          unzip \
          libpq-dev \
          postgresql-client-common \
          python3-pip \
          python3-venv \
          npm \
          nginx

    curl -sL https://deb.nodesource.com/setup_18.x | bash -
    apt-get install -y nodejs

    echo "deb http://apt.postgresql.org/pub/repos/apt focal-pgdg main" > /etc/apt/sources.list.d/pgdg.list
    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
    apt-get update
    apt-get install -y postgresql-16

    apt-get install -y redis-server

    #wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
    #echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | tee /etc/apt/sources.list.d/elastic-8.x.list
    #apt-get update
    #apt-get install -y elasticsearch

    systemctl enable --now postgresql@16-main.service
    systemctl enable --now redis-server.service
    #systemctl enable --now elasticsearch.service

    sudo pip3 install supervisor
    sudo mkdir -p /etc/supervisor/conf.d
    sudo touch /etc/supervisor/supervisord.conf
    echo "[unix_http_server]" >> /etc/supervisor/supervisord.conf
    echo "file=/tmp/supervisor.sock" >> /etc/supervisor/supervisord.conf
    echo "" >> /etc/supervisor/supervisord.conf
    echo "[supervisord]" >> /etc/supervisor/supervisord.conf
    echo "logfile=/var/log/supervisor/supervisord.log" >> /etc/supervisor/supervisord.conf
    echo "pidfile=/tmp/supervisord.pid" >> /etc/supervisor/supervisord.conf
    echo "" >> /etc/supervisor/supervisord.conf
    echo "[rpcinterface:supervisor]" >> /etc/supervisor/supervisord.conf
    echo "supervisor.rpcinterface_factory = supervisor.rpcinterface:make_main_rpcinterface" >> /etc/supervisor/supervisord.conf
    echo "" >> /etc/supervisor/supervisord.conf
    echo "[supervisorctl]" >> /etc/supervisor/supervisord.conf
    echo "serverurl=unix:///tmp/supervisor.sock" >> /etc/supervisor/supervisord.conf
    echo "" >> /etc/supervisor/supervisord.conf
    echo "[include]" >> /etc/supervisor/supervisord.conf
    echo "files = conf.d/*.conf" >> /etc/supervisor/supervisord.conf

    cd /vagrant/src/backend
    # To be continued...

  SHELL
end
