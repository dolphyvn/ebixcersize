# ebixcersize
Simple monitoring solution using Docker host with Prometheus, Grafana and NodeExporter.

# Requirements:
If you want to use docker-compose, you will need to have docker and docker-compose installed on your OS
If you want to use vagrant. Please install vagrant docker-compose plugin. You can install by run ```vagrant plugin install vagrant-docker-compose```

# Install and Run
#### Clone repo:
```
git clone https://github.com/dolphyvn/ebixcersize.git
cd ebiexcersie
```

There are three options for you to run


#### Run using vagrant ( with docker ):
```
vagrant up nodeexporter prometheus grafana --no-parallel
```

#### Run using vagrant ( with virtualbox ):
```
cd vagrant
vagrant up
```
#### Run using docker-compose:
```
docker-compose up -d
```

Wait till everything finished. You can browsing http://localhost:3000 with provided user/pass to access to grafana