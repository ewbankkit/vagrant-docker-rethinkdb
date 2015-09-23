# vagrant-docker-retthinkdb
Running RethinkDB 2.1.3 in Docker 1.7.1 in a Vagrant Ubuntu 14.04 box.
```
$ vagrant up
$ vagrant ssh
$ vagrant ssh
Welcome to Ubuntu 14.04.2 LTS (GNU/Linux 3.16.0-30-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
vagrant@rethinkdb-in-a-box:~$ cd /vagrant/
vagrant@rethinkdb-in-a-box:/vagrant$ docker-compose up -d
Pulling rethinkdb (rethinkdb:2.1.3)...
2.1.3: Pulling from rethinkdb

```
The RethinkDB web UI is mapped to port 8080 on the host.<br/>
The RethinkDB listening port is mapped to port 28015 on the host.
