<template>
  <div class="point-wrap">
    <div class="point-first-title">1.nginx环境配置</div>
    <div class="point-second-title">安装编译工具及库文件</div>
    <div
      class="point-cont"
    >yum -y install make zlib zlib-devel gcc-c++ libtool openssl openssl-devel</div>
    <div class="point-second-title">安装PCRE</div>
    <div class="point-cont">
      <p>PCRE 作用是让 Nginx 支持 Rewrite 功能</p>
      <br>
      <p>下载PCRE安装包</p>
      <p>wget https://ftp.pcre.org/pub/pcre/pcre-8.43.tar.gz</p>
      <br>
      <p>解压安装包</p>
      <p>tar zxvf pcre-8.43.tar.gz</p>
      <br>
      <p>进入安装包目录</p>
      <p>cd pcre-8.43</p>
      <br>
      <p>编译安装</p>
      <p>./configure</p>
      <p>make && make install</p>
      <br>
      <p>查看pcre版本</p>
      <p>pcre-config --version</p>
    </div>
    <div class="point-second-title">安装Nginx</div>
    <div class="point-cont">
      <p>下载 Nginx</p>
      <p>wget http://nginx.org/download/nginx-1.16.0.tar.gz</p>
      <br>
      <p>解压安装包</p>
      <p>tar zxvf nginx-1.16.0.tar.gz</p>
      <br>
      <p>进入安装包目录</p>
      <p>cd nginx-1.16.0</p>
      <br>
      <p>编译安装</p>
      <p>./configure --prefix=/nginx/webserver/nginx --with-http_stub_status_module --with-http_ssl_module --with-pcre=/PCRE/pcre-8.43</p>
      <p>make && make install</p>
      <br>
      <p>软链nginx</p>
      <p>ln -s /nginx/webserver/nginx/sbin/nginx /usr/bin/</p>
      <br>
      <p>查看nginx版本</p>
      <p>nginx -v</p>
    </div>
    <div class="point-second-title">配置Nginx</div>
    <div class="point-cont">
      <p>Nginx反向代理监听3030端口</p>
      <p>
        location / {
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forward-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
        proxy_set_header X-Nginx-Proxy true;
        proxy_pass http://destination;
        proxy_redirect off;
        }
        upstream destination {
        server 127.0.0.1:3030;
        }
      </p>
      <br>
      <p>Nginx 操作</p>
      <p>启动 nginx</p>
      <p>重启 nginx -s reopen</p>
      <p>停止 nginx -s stop</p>
      <p>重载配置 nginx -s reload</p>
    </div>
    <div class="point-first-title">2.Node环境配置</div>
    <div class="point-second-title">安装Node</div>
    <div class="point-cont">
      <p>Node官网提供已编译好的版本，可以直接下载解压后使用</p>
      <br>
      <p>下载Node安装包</p>
      <p>wget https://nodejs.org/dist/v10.16.0/node-v10.16.0-linux-x64.tar.xz</p>
      <br>
      <p>解压安装包</p>
      <p>tar zxvf node-v10.16.0-linux-x64.tar.xz</p>
      <br>
      <p>软链node和npm</p>
      <p>ln -s /node/nodejs/bin/node /usr/local/bin/</p>
      <p>ln -s /node/nodejs/bin/npm /usr/local/bin/</p>
      <br>
      <p>查看node和npm版本</p>
      <p>node -v</p>
      <p>npm -v</p>
    </div>
    <div class="point-first-title">3.git项目配置</div>
    <div class="point-second-title">安装git</div>
    <div class="point-cont">
      <p>下载git</p>
      <p>wget https://github.com/git/git/archive/v2.22.0.tar.gz</p>
      <br>
      <p>解压安装包</p>
      <p>tar zxvf v2.22.0.tar.gz</p>
      <br>
      <p>安装编译所需的依赖</p>
      <p>yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel gcc perl-ExtUtils-MakeMaker</p>
      <br>
      <p>安装依赖时，yum自动安装了git，需要卸载旧版本git</p>
      <p>yum remove git</p>
      <br>
      <p>进入安装包目录</p>
      <p>cd git-2.22.0</p>
      <br>
      <p>执行编译</p>
      <p>make prefix=/git all</p>
      <br>
      <p>安装git</p>
      <p>make prefix=/git install</p>
      <br>
      <p>软链git</p>
      <p>yum remove git</p>
      <br>
      <p>安装依赖时，yum自动安装了git，需要卸载旧版本git</p>
      <p>ln -s /git/bin/git /usr/local/bin/</p>
      <br>
      <p>查看git版本</p>
      <p>git --version</p>
    </div>
    <div class="point-second-title">git操作</div>
    <div class="point-cont">
      <p>拉取远程仓库</p>
      <p>git clone https://destination.git</p>
      <br>
      <p>拉取master分支</p>
      <p>git pull origin master</p>
      <br>
    </div>
    <div class="point-first-title">4.pm2环境配置</div>
    <div class="point-second-title">安装pm2</div>
    <div class="point-cont">
      <p>npm install pm2 -g</p>
    </div>
    <div class="point-second-title">pm2操作</div>
    <div class="point-cont">
      <p>启动进程</p>
      <p>pm2 start npm --name='destination' -- run start</p>
      <br>
      <p>查看列表</p>
      <p>pm2 list</p>
      <br>
      <p>删除进程</p>
      <p>pm2 delete 0</p>
      <br>
      <p>停止进程</p>
      <p>pm2 stop 0</p>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style scoped lang="scss">
</style>