# Ubuntu 上的 Docker

## Docker CE 安装

```text
$ sudo apt-get update


$ sudo apt-get install apt-transport-https ca-certificates curl software-properties-common

$ curl -fsSL https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu/gpg | sudo apt-key add -

$ sudo add-apt-repository "deb [arch=amd64] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu $(lsb_release -cs)
    stable"

# 官方源
# $ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

$ sudo apt-get update

$ sudo apt-get install docker-ce

$ sudo service docker start
```

## 镜像加速

在国内一般无法从官方 docker hub 上 pull 镜像下来，会报 error。

修改或创建 /etc/docker/daemon.json 文件并添加上 registry-mirrors 键值。

```text
{
  "registry-mirrors": ["https://registry.docker-cn.com"]
}
```

## 权限设置

参考[博客](https://blog.csdn.net/u013948858/article/details/78429954)。一般用户无法使用 docker,一直需要加上 sudo。可以将用户拉进 docker 用户组内，这样便能自动使用 docker 命令。

```text
  #查看是否有 docker 用户组
  sudo cat /etc/group | docker
  #如果没有则添加一个
  sudo groupadd -g 999 docker
  #将用户添加进组
  sudo usermod -aG docker zcc
  #退出登录并重进（重启 Terminal），重启 docker
  sudo systemctl restart docker
  #测试是否成功
  docker  info
```

