# IPLocation_Translate
1、一个用于IP信息翻译的工具，通过另一个项目IPLocation查询出来的IP结果放入到<a href="https://github.com/StephenJose-Dai/IPLocation">IPLocation_Translate</a>中，会自动将国家、城市翻译成中文从而实现更直观的查看IP信息  

2、注意：index.html中的apikey和secretKey需要自行到百度翻译官网中申请，申请完后将这两个填入到index.html中再保存即可使用，差不多是在index.html的第137和138行。  

3、此系统由<a href="https://daishenghui.club">戴戴的Linux</a>制作，由福建省智网云科科技有限公司、福建省数网云科技有限公司提供技术指导。  

## 环境
1、Linux  
2、Nginx

## 部署方法
1、在/www中创建iptranslate文件夹

>> ````
>> mkdir -p /www/iptranslate/
>> ````

2、将index.html放到/www/iptranslate/文件夹中

3、安装Nginx

>> 具体文档请参考戴戴的Linux这篇帖子 [Nginx编译安装](https://www.daishenghui.club/2022/11/15/categories/Linux/CentOS7%E7%BC%96%E8%AF%91%E5%AE%89%E8%A3%85nginx/)

4、配置Nginx

>> ````
>> vim /usr/local/nginx/conf/nginx.conf  //编辑nginx.conf
>> include /usr/local/nginx/conf/v_host/iptranslate.conf;   //在nginx.conf最底下，也就是最后一个括号上面加入这句，然后保存退出
>> vim /usr/local/nginx/conf/v_host/iptranslate.conf   //编辑v_host底下的iptranslate.conf，你不管底下有没有这个文件，编辑就对了，到时候保存退出后，就有这个文件了
>> ````

> 把下面这段贴到iptranslate.conf中

>> ````
>> server {
>>         charset utf-8;
>>         listen       80;  #配置网站端口
>>         server_name  abc.com; #配置网站域名
>>         access_log /usr/local/nginx/logs/transfer9000_access.log;  #配置访问日志存储位置
>>         error_log /usr/local/nginx/logs/trasfer9000_error.log debug;  #配置错误日志存储位置
>>         gzip on;
>>         gzip_comp_level 9;
>>         gzip_types text/css text/plan text/xml application/javascript application/x-javascript application/html application/xml image/png image/jpg image/jpeg image/gif image/webp image/svg+xml;
>>
>>         location /iptransfer {
>>                add_header Access-Control-Allow-Origin *;
>>                add_header Access-Control-Allow-Methods "GET, POST, OPTIONS, PUT, DELETE";
>>                add_header Access-Control-Allow-Headers *;
>>                add_header Access-Control-Allow-Credentials 'true';
>>                root   /www/;
>>                index  index.html index.htm;
>>         }
>> }
>> ````

> 然后重启NGINX

>> ````
>> /usr/local/nginx/sbin/nginx -s stop
>> /usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
>> ````

> 最后打开浏览器就能开始导入IP结果进行翻译了！  

5、只支持json文件，不要去传txt或者其他类型的文件！！！  
5、只支持json文件，不要去传txt或者其他类型的文件！！！  
5、只支持json文件，不要去传txt或者其他类型的文件！！！  

### 不会编译nginx的，可以将项目中iptranslate.conf直接复制丢到````/usr/local/nginx/conf/v_host/````中，只需要修改下域名、端口、日志存储路径即可


## 扫一扫二维码关注我学习更多知识吧~

![戴戴的Linux](https://github.com/StephenJose-Dai/IPLocation/blob/master/daidailinux.jpg)
