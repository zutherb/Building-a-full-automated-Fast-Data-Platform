<!-- .slide: data-background="img/background-orange-orig.jpg" -->

### Cloud Provisioning

<img src="./img/dcos_installation.png"/>

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Add new Network Security Zone

<img src="./img/dcos_advance_network_security.svg" style="background-color:white;height:600px"/>

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Add ELK

<img src="./img/elk.svg" style="background-color:white;height:600px"/>

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Download Filebeat

```
  - "content": |
      [Unit]
      Description=ELK: Download Filebeat
      After=network-online.target
      Wants=network-online.target
      ConditionPathExists=!/opt/filebeat/filebeat
      [Service]
      Type=oneshot
      StandardOutput=journal+console
      StandardError=journal+console
      ExecStartPre=/usr/bin/curl --fail --retry 20 --continue-at - --location --silent --show-error --verbose --output /tmp/filebeat.tar.xz ${filebeat_download_url}
      ExecStartPre=/usr/bin/mkdir -p /opt/filebeat /tmp/filebeat /etc/filebeat/
      ExecStartPre=/usr/bin/tar -axf /tmp/filebeat.tar.xz -C /tmp/filebeat --strip-components=1
      ExecStart=-/bin/mv /tmp/filebeat/filebeat /opt/filebeat/filebeat
      ExecStartPost=-/usr/bin/rm -rf /tmp/filebeat.tar.xz /tmp/filebeat
    "name": |-
      filebeat-download.service
```

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Start Filebeat

```
  - "command": |-
      start
    "content": |
      [Unit]
      Description=ELK: Filebeat collectes log file and send them to logstash
      Requires=filebeat-download.service
      After=filebeat-download.service
      [Service]
      Type=simple
      StandardOutput=journal+console
      StandardError=journal+console
      ExecStart=/opt/filebeat/filebeat -e -c /etc/filebeat/filebeat.yml -d "publish"
    "enable": !!bool |-
      true
    "name": |-
      filebeat.service
```

---

<!-- .slide: data-background="img/background-green-orig.jpg" -->

### Cloudformation
## sucks

---

### Terraform

<!-- .slide: data-background="img/background-green-orig.jpg" -->

```
resource "aws_launch_configuration" "public_slave" {
  security_groups = ["${aws_security_group.public_slave.id}"]
  image_id = "${lookup(var.coreos_amis, var.aws_region)}"
  instance_type = "${var.public_slave_instance_type}"
  key_name = "${aws_key_pair.dcos.key_name}"
  user_data = "${template_file.public_slave_user_data.rendered}"
  associate_public_ip_address = true

  lifecycle {
    create_before_destroy = false
  }
}
```

---

### Terraform - Source

<!-- .slide: data-background="img/background-green-orig.jpg" -->

https://github.com/zutherb/terraform-dcos
