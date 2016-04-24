
### DC/OS

<!-- .slide: data-background="img/background-orange-orig.jpg" -->

<img src="./img/dcos.png" />

---

<!-- .slide: data-background="img/background-title-orig.jpg" -->

### Architecture

<img src="./img/Enterprise-Architecture-Diagram.png"/>

---

### Network Security

<img src="./img/security-zones-ce.jpg" style="height:600px"/>

---

### DC/OS Installation

<!-- .slide: data-background="img/background-green-orig.jpg" -->

<img src="./img/dcos_installation.png"/>

---

### SMACK Installation (1)

<!-- .slide: data-background="img/background-green-orig.jpg" -->

```bash
dcos package install --yes cassandra
dcos package install --yes kafka
dcos package install --yes spark
dcos kafka topic add killrweather.raw
dcos package install --yes zeppelin
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
