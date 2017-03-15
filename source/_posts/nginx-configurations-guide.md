---
title: Nginx服务器相关配置
subtitle: Nginx Configurations
date: 2017-03-12 11:06:41
tags:
  - Nginx
categories:
  - TECH
  - Nginx
banner: /gallery/ngix_configurations.PNG
---

最近在折腾并学习阿里云平台，搭建部署了一个站点，考虑安全的问题，需要部署SSL证书。
经过了解，目前国内有多家公司都提供免费的SSL证书，可以安装到自己的服务器。由于自己搭建是基于Nginx的，
自己就顺便学习了一下Nginx的相关配置。


##### 1. 免费证书供应商
   国内的免费SSL证书的服务商，我发现还是有很多家的，阿里云,百度云加速，360等等。大家可以根据自己的服务器的实际情况来选择。

##### 2. 申请/安装证书
   由于服务器的架构是LNMT Stack（Linux-Nginx-MySQL-Tomcat）, 所以此次我们需要配置的是Nginx的相关配置.

   首先，登录自己的[阿里云](https://www.aliyun.com) - https://www.aliyun.com 账户，在安全（云盾）中找到 证书服务 --> 购买证书.

   以下是可以购买的证书类型，选择免费型DV SSL即可，证书是Symantec颁发的，免费型证书只能保护一个域名或字域名，一次1年，可以无限购买。
   只要你有足够多服务器和域名需要绑定。

   <!--more-->

   DV SSL: 即Domain Validation SSL 或 超快 SSL，只验证域名所有权， 10分钟颁发，保证了网站的机密信息从用户浏览器到服务器之间的传输是高强度加密传输的，是不会被非法窃取和非法篡改的，但由于只验证域名，此证书仅起到加密传输信息的作用，并不能证明网站的真实身份。

   根据以上描述:此类证书并不是很安全，一般最好只用于个人/或者企业展示网站，如果预算够的情况下，还是建议购买更好的证书，当然相应的认证更加严格，也比较可信。

   {% asset_img buy_ssl_certificate.PNG buy_ssl_certificate %}

   如果本身是使用的阿里云的服务器，再购买阿里云的SSL证书，可以比较方便的生成和安装。这一点还是很不错的。


##### 3. 安全配置

    先了解一下Nginx的相关配置：

    默认配置文件和Nginx端口
    ``` bash
        /usr/local/nginx/conf/ – Nginx配置文件目录，/usr/local/nginx/conf/nginx.conf是主配置文件

        /usr/local/nginx/html/ – 默认网站文件位置

        /usr/local/nginx/logs/ – 默认日志文件位置
    ```
    Nginx HTTP默认端口 : TCP 80
    Nginx HTTPS默认端口: TCP 443

    将会输出以下信息：
    ``` bash
      the configuration file /usr/local/nginx/conf/nginx.conf syntax is ok
      configuration file /usr/local/nginx/conf/nginx.conf test is successful
    ```
    如果我们完成一次nginx.conf文件的编辑，只需要执行以下命令来重新加载配置文件，不需要重起停止或重起Nginx。

    ``` bash
      /usr/local/nginx/sbin/nginx -s reload
    ```

    执行以下命令来停止服务器。
    ``` bash
      /usr/local/nginx/sbin/nginx -s stop
    ```

    本次，我们需要配置的文件就是/usr/local/nginx/conf/nginx.conf.
    关于链接到服务器的工具，我使用的是 MobaXterm - free Xserver and tabbed SSH client for Windows.个人觉得还是很好使的。

    我们可以使用以下命令进行编辑:
    ``` bash
      vi /usr/local/nginx/conf/nginx.conf
    ```
    默认情况下，该配置文件中没有配置SSL的安全配置。

##### 4. 下载/安装证书

    我们可以选择阿里云系统生成证书，也可以自己生成相应的公钥和私钥。

    ( 1 ): 在Nginx的安装目录下创建cert目录，并且将下载的全部文件拷贝到cert目录中。
           如果申请证书时是自己创建的CSR文件，请将对应的私钥文件放到cert目录下并且命名为yourcertificatename.key；

    ( 2 ) 打开 Nginx 安装目录下 conf 目录中的 nginx.conf 文件，找到：

          我们需要添加以下配置，个人建议如果不太清楚如何编写此配置，可以复制一份HTTP 80端口的配置，然后修改监听端口和增加ssl开头的相关配置参数。
    ``` bash
        server {
            listen 443;
            server_name localhost;
            ssl on;
            root html;
            index index.html index.htm;
            ssl_certificate   cert/cert.pem;
            ssl_certificate_key  cert/cert.key;
            ssl_session_timeout 5m;
            ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
            ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
            ssl_prefer_server_ciphers on;
            location / {
                root html;
                index index.html index.htm;
            }
        }
    ```
    保存以上配置，然后执行Nginx配置重载命令。然后通过 https 方式访问您的站点，测试站点证书的安装配置。
