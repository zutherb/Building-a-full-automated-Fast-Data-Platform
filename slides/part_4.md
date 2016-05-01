<!-- .slide: data-background="img/background-orange-orig.jpg" -->

### Demo

- DC/OS
- Cloudformation
- Terraform

---

<!-- .slide: data-background="img/background-title-orig.jpg" -->

### Cloudformation
## sucks

---

### Terraform

<!-- .slide: data-background="img/background-title-orig.jpg" -->

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
