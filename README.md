# ebixcersize

Simple monitoring solution using Docker host with Prometheus, Grafana and NodeExporter.

# Requirements:

If you want to use docker-compose, you will need to have docker and docker-compose installed on your OS

If you want to use vagrant. Please install vagrant docker-compose plugin. You can install by run

```vagrant plugin install vagrant-docker-compose```

# Install and Run

### Clone repo:
```
git clone https://github.com/dolphyvn/ebixcersize.git
cd ebiexcersie
```

There are three options for you to run

#### Run using docker-compose:

This will start three containers using docker-compose on the machine you running 
```
export ADMIN_USER=admin ADMIN_PASSWORD=ebiadmin docker-compose up -d
```

#### Run using vagrant  docker:

This will start three containers using vagrant with docker on the machine you running

```
vagrant up nodeexporter prometheus grafana --no-parallel
```

#### Run using vagrant ( with virtualbox ):

This will start a vm and install docker to run the docker-compose on it.

```
cd vagrant
vagrant up
```

Wait till everything finished. You can browsing http://localhost:3000 with provided user/pass to access to grafana ( by default user is admin and pass is ebiadmin )
