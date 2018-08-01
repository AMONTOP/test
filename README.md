


```
server {
        listen       80;
        server_name  mywordpress.oo;
        root   "F:\dev\FinTGroup"; 
        index  index.php index.html index.htm;

        location / {
            try_files $uri /index.php$is_args$args;
        }
        
        location ~ \.php(.*)$ {
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            fastcgi_split_path_info  ^((?U).+\.php)(/?.+)$;
            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
            fastcgi_param  PATH_INFO  $fastcgi_path_info;
            fastcgi_param  PATH_TRANSLATED  $document_root$fastcgi_path_info;
            include        fastcgi_params;
        }
}
```
*root 根目录 
*server_name 本地自定义开发域名 
在C:\Windows\System32\drivers\etc\hosts中添加 127.0.0.1 server_name 
> 例：127.0.0.1 october.oo

重启nginx
