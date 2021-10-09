# 使用docker-compose以ws+tls方式快速部署科学上网利器v2ray


## 更新日志

* 2020年3月3日：增加v2ray并使用ws+tls方式实现代理服务；
* 2020年3月1日：增加nginx服务并启用certbot证书；

## 使用步骤


2. 安装docker-ce并启动

以下操作我都是以root用户(非必须)进行的。

* 安装

```
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sh get-docker.sh

* 添加用户到用户组(需退出当前会话重启登录才生效)

```
gpasswd -a $USER docker
```

* 启动

```
systemctl start docker
```

* 设置docker开机自启动

```
systemctl enable docker
```

3. 安装`docker-compose`

```
$  curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

$ chmod +x /usr/local/bin/docker-compose

$ ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

4. 安装git并clone代码

```
apt-get install git


git clone https://github.com/aitlp/docker-v2ray.git


5. 修改v2ray配置

进入`docker-v2ray`目录开始修改配置。

**1) `init-letsencrypt.sh`**

将里面的`domains`和`email`修改为自己的域名和邮箱。

**2) `docker-compose.yml`**

可以不用动。

**3) `data/v2ray/config.json`**

修改ID，`"id": "bae399d4-13a4-46a3-b144-4af2c0004c2e"`，也可以不修改。

**4) `data/nginx/conf.d/v2ray.conf`**

修改所有`your_domain`为自己的域名，其他地方，如果上面可以修改的地方你没修改，那么除了域名之外的也不用修改了。

