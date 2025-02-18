# 编译oar包流程
以下操作都是在有代理的情况下进行的。

## 克隆仓库

编译oar包的仓库

```shell
git clone git@github.com:multi-modal-network/Basic-tna.git

```

ndsdn-tutorial仓库

```shell
git clone https://github.com/multi-modal-network/ngsdn-tutorial.git
```

## 安装docker

根据[教程](https://docs.docker.com/engine/install/ubuntu/)，安装docker

```shell
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
参考[教程](https://blog.csdn.net/W25679/article/details/140442416)配置docker代理，不然很多镜像pull不下来，实在不行可以从其它的虚拟机里面导出，再到这里导入。

## 拉取依赖容器

Basic-tna目录下执行`make deps`拉取项目所需要的容器 **[有问题]**，
有的bf的容器需要登录仓库，但是应该没有账号，估计这个仓库只是用于maven构建，拉到maven就可以编译。
## 执行编译
`make pipeconf`就可以执行编译。

