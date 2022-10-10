# Docker 开发环境安装

## 一、CentOS 安装 Docker

> [Docker 官网地址](https://www.docker.com/)

### 卸载旧版本

```shell
sudo yum remove docker \
                docker-client \
                docker-client-latest \
                docker-common \
                docker-latest \
                docker-latest-logrotate \
                docker-logrotate \
                docker-engine
```

### 使用 Docker 仓库安装 Docker Engine-Community

#### 设置仓库

```shell
sudo yum install -y yum-utils \
    device-mapper-persistent-data \
    lvm2
```

#### 切换阿里云仓库

```shell
sudo yum-config-manager \
    --add-repo \
    http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

#### 安装 Docker-Engine-Community

```shell
sudo yum install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

### 使用 Docker

#### 启动 Docker

```shell
sudo systemctl start docker
```

#### 设置 Docker 开机自启

```shell
sudo systemctl enable docker
```

### Docker 镜像加速

#### 获取阿里云镜像

> 阿里云镜像获取地址：[](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors)

#### 修改 daemon 配置文件

- 在  `/etc/docker/daemon.json` 文件中写入如下内容（若不存在该文件请先创建）

```json
{
  "registry-mirrors": ["阿里云加速器地址"]
}
```

#### 重启 Docker 服务

```shell
sudo systemctl daemon-reload
sudo systemctl restart docker
```

