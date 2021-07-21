# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

Vagrant.configure("2") do |config|
  # config.vm.box = "generic/centos8"



  config.vm.define "nodeexporter" do |np|
    np.vm.network :forwarded_port, host: 9100, guest: 9100, auto_correct: true

    np.vm.provider "docker" do |d3|
      d3.image = "prom/node-exporter:v1.1.2"
      # d.ports = ["9100:9100"]
      d3.name = "nodeexporter"
      d3.volumes = ["/proc:/host/proc:ro","/sys:/host/sys:ro","/:/rootfs:ro"]
      d3.cmd = ["--path.procfs=/host/proc","--path.rootfs=/rootfs", "--path.sysfs=/host/sys","--collector.filesystem.ignored-mount-points=^/(sys|proc|dev|host|etc)($$|/)"]
    end

    np.vm.provider "podman" do |pm3|
      pm3.image = "prom/node-exporter:v1.1.2"
      pm3.name = "nodeexporter"
      # pm.ports = ["9100:9100"]
      pm3.volumes = ["/proc:/host/proc:ro","/sys:/host/sys:ro","/:/rootfs:ro"]
      pm3.cmd = ["--path.procfs=/host/proc","--path.rootfs=/rootfs", "--path.sysfs=/host/sys","--collector.filesystem.ignored-mount-points=^/(sys|proc|dev|host|etc)($$|/)"]
    end
  end

  config.vm.define "prometheus" do |prom|
    # prom.vm.network :private_network, type: "dhcp"
    prom.vm.network :forwarded_port, host: 9090, guest: 9090, auto_correct: true
    prom.vm.synced_folder "./provisioning/prometheus/", "/etc/prometheus/"

    prom.vm.provider "docker" do |d1|
      # d.run "prometheus", image: "prom/prometheus:v2.28.1"
      d1.image = "prom/prometheus:v2.28.1"
      d1.name = "prometheus"
      d1.link("nodeexporter:nodeexporter")
    end

    prom.vm.provider "podman" do |pm1|
      pm1.image = "prom/prometheus:v2.28.1"
      pm1.name = "prometheus"
      pm1.link("nodeexporter:nodeexporter")
    end
  end


  config.vm.define "grafana" do |gf|
    # gf.vm.network :private_network, type: "dhcp"
    gf.vm.network :forwarded_port, host: 3000, guest: 3000, auto_correct: true
    gf.vm.synced_folder "./provisioning/", "/etc/grafana/provisioning/"
    # config.vm.provider "docker"

    gf.vm.provider "docker" do |d2|
      d2.image = "grafana/grafana:8.0.6"
      d2.name = "grafana"
      d2.link("prometheus:prometheus")
      # d2.link "prometheus:prometheus"
      # d.ports = ["3000:3000"]
      # d.cmd = ["vertx", "run", "vertx-examples/src/raw/java/httphelloworld/HelloWorldServer.java"]
    end

    gf.vm.provider "podman" do |pm2|
      pm2.image = "grafana/grafana:8.0.6"
      pm2.name = "grafana"
      pm2.link("prometheus:prometheus")
    end
  end

end


