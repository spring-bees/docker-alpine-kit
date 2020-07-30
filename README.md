# 工具包

* bash
* tzdata
* openssh
* su-exec
* unzip
* libc6-compat
* libzmq
* ttf-dejavu
* curl
* shadow
* sshpass
* ansible

## Ansible

使用环境变量参数初始化 `hosts` 配置

```
docker run --name ansible -it coolbeevip/docker-alpine-kit \
-e ANSIBLE_SSH_HOSTS=10.19.38.220 \
-e ANSIBLE_SSH_PORTS=22022 \
-e ANSIBLE_SSH_USERS=puaiuc \
-e ANSIBLE_SSH_PASSS=Pu@1uC2016 \
-e ANSIBLE_SU_PASSS=xdjr0lxGu \
ansible 10.19.38.220 -a 'uptime'
```

你可以在容器外部定义 `hosts` 和 `ansible.cfg` 文件，并使用卷映射到容器内部

```
docker run --name ansible -it coolbeevip/docker-alpine-kit -v ./volume/ansible:/etc/ansible /bin/bash
```
