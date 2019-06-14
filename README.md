qidotslock.com-2019
=============

奇点科技英文官网2019年版


域名绑定、301转向及nginx配置
-----

新建配置文件: ``sudo nano /etc/nginx/sites-available/qidotslock.com``

编辑配置文件及保存: 

    server {
      listen 443 ssl http2;
      server_name qidotslock.com;
      ssl_certificate qidotslock.crt;
      ssl_certificate_key qidotslock.key;
      index index.html;
      root /srv/qidotslock.com-2019/_site;
      error_page 404 /Error.html;
      add_header Strict-Transport-Security "max-age=15768000" always;
      ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3;
      ssl_ciphers HIGH:!aNULL:!MD5:!DH;
    }
    server {
      listen 443 ssl http2;
      server_name www.qidotslock.com;
      ssl_certificate qidotslock.crt;
      ssl_certificate_key qidotslock.key;
      return 301 https://qidotslock.com$request_uri;
    }
    server {
      listen 80;
      server_name qidotslock.com www.qidotslock.com;
      return 301 https://qidotslock.com$request_uri;
    }

建立链接: ``sudo ln -s /etc/nginx/sites-available/qidotslock.com /etc/nginx/sites-enabled/``

重启nginx: ``sudo service nginx restart``


下载及生成网站
-----

1. 下载网站源码: ``git clone git://github.com/zackwong/qidotslock.com-2019.git``

2. 进入源码根目录: ``cd qidotslock.com-2019``

3. 生成网站: ``jekyll build``


开发者
---------

* Zack Wong &lt;hzzzoo@126.com&gt;

