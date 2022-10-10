# Docker 开发环境安装

## 一、CentOS 安装 Docker

> [Docker 官网地址](https://www.docker.com/)

### 1. 卸载旧版本

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

### 2. 使用 Docker 仓库安装 Docker Engine-Community

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

### 3. 使用 Docker

#### 启动 Docker

```shell
sudo systemctl start docker
```

#### 设置 Docker 开机自启

```shell
sudo systemctl enable docker
```

### 4.Docker 镜像加速

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



## 二、Docker 安装 Nginx

### 1. 下载 Nginx 镜像

```shell
docker pull nginx:1.22.0
```

### 2. 创建挂载目录

#### 创建挂载目录

```shell
mkdir -p /usr/local/docker/nginx/conf
mkdir -p /usr/local/docker/nginx/log
mkdir -p /usr/local/docker/nginx/html
```

#### 复制容器中的文件到宿主机

```shell
# 生成容器
docker run --name nginx -p 80:80 -d nginx
# 将容器 nginx.conf 文件复制到宿主机
docker cp nginx:/etc/nginx/nginx.conf /usr/local/docker/nginx/conf/nginx.conf
# 将容器 conf.d 文件夹下内容复制到宿主机
docker cp nginx:/etc/nginx/conf.d /usr/local/docker/nginx/conf/conf.d
# 将容器中的 html 文件夹复制到宿主机
docker cp nginx:/usr/share/nginx/html /usr/local/docker/nginx/
```

### 3. 创建 Nginx 容器并运行

#### 删除原容器

```shell
# 关闭该容器
docker stop nginx
# 删除该容器
docker rm nginx
```

#### 创建 Nginx 容器挂载文件并运行

```shell
docker run \
-p 80:80 \
--name nginx \
-v /usr/local/docker/nginx/conf/nginx.conf:/etc/nginx/nginx.conf \
-v /usr/local/docker/nginx/conf/conf.d:/etc/nginx/conf.d \
-v /usr/local/docker/nginx/log:/var/log/nginx \
-v /usr/local/docker/nginx/html:/usr/share/nginx/html \
--restart=always \
-d nginx:1.22.0
```

- 参数说明

  | 命令                                                         | 描述                     |
  | ------------------------------------------------------------ | ------------------------ |
  | -p 80:80                                                     | 容器与主机端口映射       |
  | --name nginx                                                 | 启动容器的名字           |
  | -v /usr/local/docker/nginx/conf/nginx.conf:/etc/nginx/nginx.conf | 挂载 nginx.conf 配置文件 |
  | -v /usr/local/docker/nginx/conf/conf.d:/etc/nginx/conf.d     | 挂载 nginx 配置文件      |
  | -v /usr/local/docker/nginx/log:/var/log/nginx                | 挂载 nginx 日志文件      |
  | -v /usr/local/docker/nginx/html:/usr/share/nginx/html        | 挂载 nginx 内容          |
  | --restart=always                                             | 容器重启策略             |
  | -d                                                           | 后台运行                 |
  | nginx:1.22.0                                                 | 本地运行的版本           |
  | \                                                            | shell 命令换行           |

  

## 三、Docker 安装 MySQL

### 1. 下载 MySQL 镜像

```shell
docker pull mysql:8.0.28
```

### 2. 创建挂载目录

```shell
mkdir -p /usr/local/docker/mysql/conf
mkdir -p /usr/local/docker/mysql/log
mkdir -p /usr/local/docker/mysql/data
```

### 3. 创建 MySQL 容器并运行

```shell
docker run \
-p 3306:3306 \
--name mysql \
-v /usr/local/docker/mysql/log:/var/log/mysql \
-v /usr/local/docker/mysql/data:/var/lib/mysql \
-v /usr/local/docker/mysql/conf:/etc/mysql \
-e MYSQL_ROOT_PASSWORD=123456 \
--restart=always \
-d mysql:8.0.28
```

- 参数说明

  | 命令                                           | 描述                |
  | ---------------------------------------------- | ------------------- |
  | -p 3306:3306                                   | 容器与主机端口映射  |
  | --name mysql                                   | 启动容器的名字      |
  | -v /usr/local/docker/mysql/log:/var/log/mysql  | 挂载日志文件        |
  | -v /usr/local/docker/mysql/data:/var/lib/mysql | 挂载 MySQL 存储文件 |
  | -v /usr/local/docker/mysql/conf:/etc/mysql     | 挂载配置文件        |
  | -e MYSQL_ROOT_PASSWORD=123456                  | 设置 root 用户密码  |
  | --restart=always                               | 容器重启策略        |
  | -d                                             | 后台运行            |
  | mysql:8.0.28                                   | 本地运行的版本      |
  | \                                              | shell 命令换行      |

  
