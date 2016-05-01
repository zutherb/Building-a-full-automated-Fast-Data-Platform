
### DC/OS

<!-- .slide: data-background="img/background-orange-orig.jpg" -->

<img src="./img/dcos.png" />

---

<!-- .slide: data-background="img/background-title-orig.jpg" -->

### DC/OS Architecture

<img src="./img/dcos_architecture.svg" style="background-color: white"/>

---

### DC/OS Network Security

<img src="./img/dcos_network_security.svg" style="height:600px"/>

---

### DC/OS Installation

<!-- .slide: data-background="img/background-title-orig.jpg" -->

<img src="./img/dcos_installation.png"/>

---

### Command Line Interface 

<!-- .slide: data-background="background-title-orig.jpg" -->

```bash
$ dcos
Command line utility for the Mesosphere Datacenter Operating
System (DC/OS). The Mesosphere DC/OS is a distributed operating
system built around Apache Mesos. This utility provides tools
for easy management of a DC/OS installation.

Available DC/OS commands:

    config          Get and set DC/OS CLI configuration properties
    help            Display command line usage information
    marathon        Deploy and manage applications on the DC/OS
    node            Manage DC/OS nodes
    package         Install and manage DC/OS packages
    service         Manage DC/OS services
    task            Manage DC/OS tasks

Get detailed command description with 'dcos <command> --help'.
```

---

### SMACK Installation (1)

<!-- .slide: data-background="img/background-title-orig.jpg" -->

```bash
dcos package install --yes cassandra
dcos package install --yes kafka
dcos package install --yes spark
dcos kafka topic add killrweather.raw
```

---

### SMACK Installation (2)

<!-- .slide: data-background="img/background-title-orig.jpg" -->

```bash
cat > /opt/smack/conf/killrweather_ingest.json << EOF
{
    "id": "/ingest",
    "container": {
        "type": "DOCKER",
        "docker": {
            "image": "zutherb/mesos-killrweather-app",
            "network": "HOST",
            "forcePullImage": true
        }
    },
    "cmd": "./ingest.sh -Dcassandra.connection.host=cassandra-dcos-node.cassandra.dcos.mesos -Dkafka.hosts.0=broker-0.kafka.mesos:1025 -Dkafka.zookeeper.connection=leader.mesos"
}
EOF
dcos marathon app add /opt/smack/conf/killrweather_ingest.json
```
