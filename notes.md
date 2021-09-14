# M103 MONGODB BASIC CLUSTER ADMINISTRATION

## CHAPTER 0

### Introduction

- High availability
- Replica set
- Scalability through sharding

## CHAPTER 1

### The Mongod

- Daeamon
- Each server runs a mongod process.

```sh
mongod
```

- default port 27017
- dbpath: /data/db
- bind_ip: localhost by default
- auth: disabled by default

- db.shutDownServer()

To run a local server:

In DATA folder:

```sh
mongod --dbpath mongodb
```

In a new terminal window

```sh
mongosh
```

### QUIZ

The Mongod
Problem:

Which of these are default configurations for mongod?

Check all answers that apply:

- [ ] authentication is enabled
- [X] database files are stored in the directory /data/db/
- [ ] mongod can connect to local and remote clients
- [X] mongod listens on port 27017

### Mongod options

-- port, -- dbpath, --auth, --bind_ip, --logpath, --fork, --replSet (sets replica set name).

### LAB

Answer: mongod --port 27000

### Configuration file

- YAML

An example:

```yaml
storage:
  dbPath: "/data/db"
systemLog:
  path: "/data/log/mongod.log"
  destination: "file"
replication:
  replSetName: M103
net:
  bindIp : "127.0.0.1,192.168.103.100"
tls:
  mode: "requireTLS"
  certificateKeyFile: "/etc/tls/tls.pem"
  CAFile: "/etc/tls/TLSCA.pem"
security:
  keyFile: "/data/keyfile"
processManagement:
  fork: true
```

### QUIZ Configuration file

Right answer:

```yaml
storage:
  dbPath: "/data/db"
systemLog:
  destination: file
  path: "/data/logs"
replication:
  replSetName: "M103"
net:
  bindIp: "127.0.0.1,192.168.103.100"
security:
  keyFile: "/data/keyfile"
processManagement:
  fork: true
```

### Lab configuration file

Answer:

```yaml
net:
   port: 27000
security:
   authorization: "enabled"
```
