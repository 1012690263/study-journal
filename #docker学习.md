# docker学习

## docker的几种常见用法

## 测试网络连接

ping baidu.com

curl https://hub.docker.com

## 查看当前路径

pwd

## 查看端口

netstat -tulnp | grep 80

lsof -i 80

## nginx默认首页的代码

默认在 /usr/share/nginx/html/index.html

```html
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

## nginx默认文件配置位置（docker）

/etc/nginx/nginx.conf

## 目录挂载

由于容器内部里面是很纯净的，没有vi等功能，所以用目录挂载实现外部方便修改

 docker run -d -p 88:80 -v /app/nghtml:/usr/share/nginx/html --name app01 nginx，这个时候访问页面时403，因为nghtml下面没有东西

```bash
[root@VM-12-6-opencloudos ~]# mkdir -p /app/nghtml
echo "<h1>Hello from Nginx in Docker</h1>" > /app/nghtml/index.html
[root@VM-12-6-opencloudos ~]# ls
cosfs.sh  dnspod.sh  mynginx.tar  txcdn.sh
[root@VM-12-6-opencloudos ~]# cd /
[root@VM-12-6-opencloudos /]# ls
app  boot  dev  home  lib64  mnt  proc  run   snap  sys  usr  www
bin  data  etc  lib   media  opt  root  sbin  srv   tmp  var
```

这里提前需要创建文件的,也可以后创，但是就得手动

~对应的是当前用户的目录，对于root用户，就是/root

/对应的时当前整个文件系统的根目录

然后当容器删了，这个挂载目录也不会消失，下次可以创建时用

## 卷映射

目录挂载方法在用于映射配置文件时会出错，因为外部文件是空的，导致启动不了

docker run -d -p 99:80 -v /app/nghtml:/usr/share/nginx/html -v ngconf:/etc/nginx --name app02 nginx

两者还是很相似的，但是卷映射是个单独文件没有套娃

卷存储在 var/lib/docker/volumes下

```bash
[root@VM-12-6-opencloudos volumes]# ls
backingFsBlockDev  ea62da3576f6ed1816cc2ba401b393677eadd3ead8fa1976be113d5b8bc5a2c7  metadata.db  ngconf
[root@VM-12-6-opencloudos volumes]# cd ngconf
[root@VM-12-6-opencloudos ngconf]# ls
_data
[root@VM-12-6-opencloudos ngconf]# cd _data/
[root@VM-12-6-opencloudos _data]# ls
conf.d  fastcgi_params  mime.types  modules  nginx.conf  scgi_params  uwsgi_params
[root@VM-12-6-opencloudos _data]# 
```

## 网络

docker容器也可以访问容器

先进入内部然后再通过外部ip端口访问

默认网络是docker0，不支持主机域名

```bash
[root@VM-12-6-opencloudos _data]# docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                                 NAMES
7ead67ef0816   nginx     "/docker-entrypoint.…"   12 minutes ago   Up 12 minutes   0.0.0.0:99->80/tcp, [::]:99->80/tcp   app02
ec59aec09e28   nginx     "/docker-entrypoint.…"   28 minutes ago   Up 28 minutes   0.0.0.0:88->80/tcp, [::]:88->80/tcp   app01
[root@VM-12-6-opencloudos _data]# docker exec -it app01 bash
root@ec59aec09e28:/# curl http://43.142.252.55:99/
<h1>Hello from Nginx in Docker</h1>
root@ec59aec09e28:/#  
```

  docker inspect app01

"Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",这里是默认网关和ip地址

"Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.3",

```bash
[root@VM-12-6-opencloudos _data]# docker exec -it app01 bash
root@ec59aec09e28:/# curl http://172.17.0.3:80

<h1>Hello from Nginx in Docker</h1>

root@ec59aec09e28:/# 
```

就可以通过IP地址访问内部端口

但是ip可能会变的，所以通过域名的方式

```bash
[root@VM-12-6-opencloudos _data]# docker network create mynet
188da93cb686b5b8400856adb869123dad3d6e18d0056186b6ca422275965b80
[root@VM-12-6-opencloudos _data]# docker network ls
NETWORK ID     NAME      DRIVER    SCOPE
39b48c946ef1   bridge    bridge    local
2a9685724b1b   host      host      local
188da93cb686   mynet     bridge    local
6c79aacdee5b   none      null      local
```

这个默认是bridge

再用run的时候可以加上--network

再进入容器就可以通过域名加内部端口访问

如curl http://app01:80

## redis主从同步集群

没学redis暂时不做处理

## mysql部署

mysql配置文件位置 /etc/mysql/conf.d，conf.d是个目录

mysql数据文件位置 /var/lib/mysql

端口3306

mysql在docker里的配置文件下只要是以.cnf结尾的，都会被当作配置文件,而且可以用目录挂载，conf.d是个空目录，里面不会有配置文件，不会导致容器爆炸

```bash
[root@VM-12-6-opencloudos ~]# docker run -d -p 3306:3306 \
> -v /app/myconf:/etc/mysql/conf.d \
> -v /app/mydata:/var/lib/mysql \
> -e MYSQL_ROOT_PASSWORD=root \
> mysql
Unable to find image 'mysql:latest' locally
```

没有会自动下载

```
MYSQL环境变量
MYSQL_ROOT_PASSWORD
此变量是必需的，它指定将为 MySQL 超级用户帐户设置的密码。在上面的示例中，它被设置为 。rootmy-secret-pw

MYSQL_DATABASE
此变量是可选的，允许您指定要在映像启动时创建的数据库的名称。如果提供了用户/密码（见下文），则该用户将被授予超级用户访问权限 （对应GRANT ALL⁠） 添加到此数据库。

MYSQL_USER,MYSQL_PASSWORD
这些变量是可选的，用于创建新用户和设置该用户的密码。此用户将被授予变量指定的数据库的超级用户权限（见上文）。这两个变量都是创建用户所必需的。MYSQL_DATABASE

请注意，无需使用此机制来创建 root 超级用户，默认情况下，该用户是使用变量指定的密码创建的。MYSQL_ROOT_PASSWORD

MYSQL_ALLOW_EMPTY_PASSWORD
这是一个可选变量。设置为非空值，如 ，以允许使用 root 用户的空白密码启动容器。注意：除非您真的知道自己在做什么，否则不建议将此变量设置为，因为这将使您的 MySQL 实例完全不受保护，从而允许任何人获得完整的超级用户访问权限。yesyes

MYSQL_RANDOM_ROOT_PASSWORD
这是一个可选变量。设置为非空值（如 ），为 root 用户生成随机初始密码（使用 ）。生成的 root 密码将打印到 stdout （） 中。yesopensslGENERATED ROOT PASSWORD: .....

MYSQL_ONETIME_PASSWORD
初始化完成后，将 root（不是 ！中指定的用户）用户设置为过期，强制在首次登录时更改密码。任何非空值都将激活此设置。注意：此功能仅在 MySQL 5.6+ 上受支持。在 MySQL 5.5 上使用此选项将在初始化期间引发相应的错误。MYSQL_USER

MYSQL_INITDB_SKIP_TZINFO
默认情况下，入口点脚本会自动加载函数所需的时区数据。如果不需要，则任何非空值都会禁用时区加载。CONVERT_TZ()
```

## wordpress开源博客部署

### 传统方法

```bash
docker run -d -p 3307:3306 \
-e MYSQL_ROOT_PASSWORD=root \
-e MYSQL_DATABASE=wordpress \
-v mysql-data:/var/lib/mysql \
-v /app/myconf:/etc/mysql/conf.d \
--restart always --name mysql \
--network blog \
mysql
```

```bash
docker run -d -p 8080:80 \
-e WORDPRESS_DB_HOST=mysql \
-e WORDPRESS_DB_USER=root \
-e WORDPRESS_DB_PASSWORD=root \
-e WORDPRESS_DB_NAME=wordpress \
-v wordpress:/var/www/html \
--restart always --name wordpress-app \
--network blog \
wordpress:latest

```



### 集成方法

编写一个compose.yaml文件把要启动的内容写好，一键启动，可以方便迁徙

Compose 文件的默认路径是 （preferred） 或放置在工作目录中的路径。 Compose 还支持早期版本的向后兼容性。 如果两个文件都存在，则 Compose 会优先使用规范的 .`compose.yaml``compose.yml``docker-compose.yaml``docker-compose.yml``compose.yaml`

```
要启动文件中定义的所有服务，请执行以下作：compose.yaml


 docker compose up
要停止和删除正在运行的服务，请执行以下作：


 docker compose down 
如果要监控正在运行的容器的输出并调试问题，可以通过以下方式查看日志：


 docker compose logs
要列出所有服务及其当前状态，请执行以下作：


 docker compose ps
```

示例应用程序由以下部分组成：

- 2 个服务，由 Docker 镜像提供支持：和`webapp``database`

- 1 个密钥（HTTPS 证书），注入前端

- 1 个配置 （HTTP），注入前端

- 1 个持久卷，附加到后端

- 2 个网络

	```yaml
	services:
	  frontend:
	    image: example/webapp
	    ports:
	      - "443:8043"
	    networks:
	      - front-tier
	      - back-tier
	    configs:
	      - httpd-config
	    secrets:
	      - server-certificate
	
	  backend:
	    image: example/database
	    volumes:
	      - db-data:/etc/data
	    networks:
	      - back-tier
	
	volumes:
	  db-data:
	    driver: flocker
	    driver_opts:
	      size: "10GiB"
	
	configs:
	  httpd-config:
	    external: true
	
	secrets:
	  server-certificate:
	    external: true
	
	networks:
	  # The presence of these objects is sufficient to define them
	  front-tier: {}
	  back-tier: {}
	```

	

该命令启动 and 服务，创建必要的网络和卷，并将配置和密钥注入前端服务。`docker compose up``frontend``backend`

`docker compose ps`提供服务当前状态的快照，以便轻松查看正在运行的容器、它们的状态以及它们正在使用的端口：

```bash
docker compose ps

NAME                IMAGE                COMMAND                  SERVICE             CREATED             STATUS              PORTS
example-frontend-1  example/webapp       "nginx -g 'daemon ofâ¦"   frontend            2 minutes ago       Up 2 minutes        0.0.0.0:443->8043/tcp
example-backend-1   example/database     "docker-entrypoint.sâ¦"   backend             2 minutes ago       Up 2 minutes
```

### 实例

```yaml
version: "3"
services:
  mysql:
    container_name: mysql
    image: mysql
    ports:
      - "3307:3306"
    environment:
      - MYSQL_ROOT_PASSWORD=root
      - MYSQL_DATABASE=wordpress
    volumes:
      - mysql-data:/var/lib/mysql
      - /app/myconf:/etc/mysql/conf.d
    restart: always
    networks:
      - blog

  wordpress:
    image: wordpress
    ports:
      - "8080:80"
    environment:
      - WORDPRESS_DB_HOST=mysql
      - WORDPRESS_DB_USER=root
      - WORDPRESS_DB_PASSWORD=root
      - WORDPRESS_DB_NAME=wordpress
    volumes:
      - wordpress:/var/www/html
    restart: always
    networks:
      - blog
    depends_on:
      - mysql

volumes:
  mysql-data:
  wordpress:

networks:
  blog:

```

```yaml
[root@VM-12-6-opencloudos ~]# vim compose.yaml
[root@VM-12-6-opencloudos ~]# ls
compose.yaml  cosfs.sh  dnspod.sh  mynginx.tar  txcdn.sh
[root@VM-12-6-opencloudos ~]# docker ps
CONTAINER ID   IMAGE              COMMAND                  CREATED          STATUS          PORTS                                                    NAMES
ff311388f646   wordpress:latest   "docker-entrypoint.s…"   39 minutes ago   Up 39 minutes   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp                  wordpress-app
ae6ba5faac7c   mysql              "docker-entrypoint.s…"   44 minutes ago   Up 44 minutes   33060/tcp, 0.0.0.0:3307->3306/tcp, [::]:3307->3306/tcp   mysql
[root@VM-12-6-opencloudos ~]# docker rm -f mysql wordpress-app 
mysql
wordpress-app
[root@VM-12-6-opencloudos ~]# docker volume ls
DRIVER    VOLUME NAME
local     ea62da3576f6ed1816cc2ba401b393677eadd3ead8fa1976be113d5b8bc5a2c7
local     mysql-data
local     ngconf
local     wordpress
[root@VM-12-6-opencloudos ~]# docker volume rm mysql-data wordpress 
mysql-data
wordpress
[root@VM-12-6-opencloudos ~]# docker network ls
NETWORK ID     NAME      DRIVER    SCOPE
25078f613b4c   blog      bridge    local
39b48c946ef1   bridge    bridge    local
2a9685724b1b   host      host      local
188da93cb686   mynet     bridge    local
6c79aacdee5b   none      null      local
[root@VM-12-6-opencloudos ~]# docker network rm blog
blog
[root@VM-12-6-opencloudos ~]# 
```

```bash
[root@VM-12-6-opencloudos ~]# docker compose -f compose.yaml up -d
WARN[0000] /root/compose.yaml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion 
[+] Running 5/5
 ✔ Network root_blog           Created                                                                          0.1s 
 ✔ Volume "root_mysql-data"    Created                                                                          0.0s 
 ✔ Volume "root_wordpress"     Created                                                                          0.0s 
 ✔ Container mysql             Started                                                                          0.4s 
 ✔ Container root-wordpress-1  Started                                                                          0.5s 
[root@VM-12-6-opencloudos ~]# 
```

### 🔍 主要问题说明：

1. **缺失 `version` 字段**：Docker Compose 文件必须包含 `version`（如 `version: "3"`）。
2. **缩进不规范**：YAML 对缩进非常敏感，推荐统一使用空格（不要使用 Tab），每级缩进通常是 2 个空格。
3. **`ports` 键值对格式错误**：像 `-"3307:3306"` 是非法的，应改为 `- "3307:3306"`（注意空格和引号）。
4. **`entrypoint` 使用错误**：
	- 你写的是 `entrypoint:` 下面写了几个数据库参数，这是不正确的。
	- 正确方式是用 `environment:` 来传入这些参数（如上所示）。

#### ✅ 方式一：命令行指定项目名（最推荐）

```bash
docker compose -f compose.yaml -p myblog up -d
```

这将项目名设置为 `myblog`，效果和你写 `name: myblog` 类似，但这是官方支持的做法。



