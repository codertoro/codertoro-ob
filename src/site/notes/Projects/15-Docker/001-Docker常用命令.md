---
{"type":"docker","title":"001-Docker常用命令","tags":["docker"],"author":"codertoro","establish":"2025-08-13","update":"2025/08/13 16:38","dg-publish":true,"permalink":"/Projects/15-Docker/001-Docker常用命令/","dgPassFrontmatter":true,"created":"2025-08-13T14:01:10.129+08:00","updated":"2025-08-13T16:38:34.000+08:00"}
---


## **阶段 1：Docker 安装与基础配置**

  

### **系统更新与 Docker 启动**

```
docker version
sudo yum update -y
sudo systemctl enable --now docker
docker ps
```

### **配置 daemon.json**

```
sudo mkdir -p /etc/docker
ls
pwd
sudo nano /etc/docker/daemon.json
sudo cat /e
sudo cat /etc/docker/d
sudo cat /etc/docker/daemon.json
```

### **重载与重启服务**

```
sudo systemctl daemon-reload
sudo syatemctl restart docker
sudo systemctl restart docker
docker ps
```

---

## **阶段 2：镜像搜索与拉取**

```
docker search nginx
docker search nginx
iredis --rainbow -a 123456
docker info | grep -A3 "Registry Mirrors"
cat /etc/docker/daemon.json
docker pull nginx
docker images
```

---

## **阶段 3：容器运行与端口映射**

  

### **基本运行**

```
docker run --help
docker run nginx
docker start f8a
docker stop priceless_booth
docker rm -f f8a
docker run --name mynginx nginx
docker run -d --name mynginx nginx
docker ps
```

### **端口映射**

```
docker rm -f ad7
docker nginx -d --name mynginx -p 180:80 nginx
docker run -d --name mynginx -p 180:80 nginx
docker ps
```

---

## **阶段 4：防火墙放行端口**

```
sudo systemctl status firewalld
sudo firewall-cmd --list-all
sudo firewall-cmd --zone=public --add-port=180/tcp --permanent
sudo firewall-cmd --reload
```

---

## **阶段 5：进入容器并修改文件**

```
docker exec -it mynginx /bin/bash
ls
cd /usr/share/nginx/html
ls
vi index.html
echo "<h1>Hello,Docker<h1>" > index.html
cat index.html
exit
```

---

## **阶段 6：提交镜像并保存**

```
docker commit --help
docker -m  "update index.html" mynginx mynginx:v1.0
docker commit -m  "update index.html" mynginx mynginx:v1.0
docker images
docker save --help
docker save -o mynginx.tar mynginx:v1.0
ls
```

---

## **阶段 7：删除与导入镜像**

```
docker ps
docker rm -f e52
docker ps
docker images
docker rmi d4dc975c5f39 2cd1d97f893f
docker images
docker ps -a
docker load --help
docker load -i mynginx.tar
docker images
```

---

## **阶段 8：运行新镜像**

```
docker run mynginx:v1.0
docker pa
docker pa
docker ps
docker images
docker run -d --name app01 -p 180:80 mynginx:v1.0
docker ps
```

---

## **阶段 9：登录 Docker Hub**

```
docker login
docker login
docker login -u codertoro
ping -c 4 registry-1.docker.io
ping -c 4 www.baidu.com
cat /etc/os-release
docker login -u codertoro
```

---

## **阶段 10：清理容器**

```
docker ps -a
docker ps -aq
docker rm -f $(docker ps -aq)
docker ps -a
```

---

## **阶段 11：挂载宿主机目录**

```
docker run -d -p 180:80 --name app01 nginx
docker ps
docker rm -f 9cf
docker run -d -p 180:80 --name app01 nginx
docker rm -f e09
docker run -d -p 180:80 -v /app/nghtml:/usr/share/nginx/html --name app01 nginx
docker ps
```

---

## **阶段 12：修改挂载目录文件**

```
cd /app
ls
cd nghtml/
ls
echo  222 > index.html
docker rm -f dca
docker run -d -p 180:80 -v /app/nghtml:/usr/share/nginx/html --name app01 nginx
docker exec -it 9ce bash
cd /usr/share/nginx/html/
ls
cat index.html
echo 3333 >> index.html 
cat index.html
exit
pwd
```

---

## **阶段 13：挂载多个卷**

```
docker run -d -p 280:80 -v /app/nghtml:/usr/share/nginx/html -v ngconf:/etc/nginx --name app02 nginx
docker ps
```

---

## **阶段 14：查看卷内容**

```
cd /var/lib/docker/volumes/
ls
cd ngconf/
ls
cd _data/
ls
nano nginx.conf
cat nginx.conf
```

---

## **阶段 15：容器内查看配置文件**

```
docker exec -it app02 bash
cd /etc/nginx
ls
cat nginx.conf
exit
```

---

## **阶段 16：宿主机目录管理与卷检查**

```
cd ~
ls
docker volume
docker volume ls
docker volume create haha
docker colume inspect
docker volume inspect ngconf
```

---

我发现你这一套命令正好像是一个**Docker 学习+实验全流程**。

如果你愿意，我可以帮你把它整理成**一张时间轴+功能分类对照表**，这样复习的时候更直观，甚至可以直接当学习文档用。

你要我帮你画这个表吗？