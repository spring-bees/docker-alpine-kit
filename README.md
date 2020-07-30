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

## ANSIBLE

使用环境变量参数初始化 `hosts` 配置

```
docker run --name ansible -it coolbeevip/docker-alpine-kit \
  -e ANSIBLE_SSH_HOSTS=192.168.0.1 \
  -e ANSIBLE_SSH_PORTS=22 \
  -e ANSIBLE_SSH_USERS=coolbeevip \
  -e ANSIBLE_SSH_PASSS=coolbeevip \
  -e ANSIBLE_SU_PASSS=123456 \
  ansible 10.19.38.220 -a 'uptime'
```

* ANSIBLE_SSH_HOSTS 主机地址
* ANSIBLE_SSH_PORTS SSH端口
* ANSIBLE_SSH_USERS SSH登录用户名
* ANSIBLE_SSH_PASSS SSH登录密码
* ANSIBLE_SU_PASSS SU账户密码

**注意：** 以上参数可以设置多个，使用逗号分隔，例如:

```
ANSIBLE_SSH_HOSTS=192.168.0.1,192.168.0.2
ANSIBLE_SSH_PORTS=22,22
ANSIBLE_SSH_USERS=user1,user2
ANSIBLE_SSH_PASSS=pass1,pass2
ANSIBLE_SU_PASSS=supass1,supass2
```

你可以在容器外部定义 `hosts` 和 `ansible.cfg` 文件，并使用卷映射到容器内部

```
docker run --name ansible -it coolbeevip/docker-alpine-kit -v ./volume/ansible:/etc/ansible /bin/bash
```
