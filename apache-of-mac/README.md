mac下默认自带了apache，可以通过下面的命令查看版本号
apachectl -v

apache服务的三种命令
1、sudo apachectl start   --启动
2、sudo apachectl stop    --停止
3、sudo apachectl restart --重新启动

默认目录
服务启动后，我们就可以通过在浏览器中输入：http://localhost来确认服务是否正常启动。
如果正常启动，此刻页面上应该显示：It Works！

apache使用
    /Library/WebServer/Documents/ 作为系统默认的目录
    /Users/username/Sites/ 也可以使用用户名下的Sites目录

apache安装目录
    /etc/apache2
sudo vim /etc/apache2/httpd.conf 修改系统默认目录为用户名下的Sites目录


跨域问题
sudo vim /etc/apache2/httpd.conf
找到这行
#LoadModule headers_module libexec/apache2/mod_headers.so
把#注释符去掉
LoadModule headers_module libexec/apache2/mod_headers.so
目的是开启apache头信息自定义模块

然后在独立资源域名的虚拟主机添加一行
Header set Access-Control-Allow-Origin *
意思是对这个域名的资源进行访问时，添加一个头信息

重启apache