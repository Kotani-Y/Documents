# Dockerで複数台のApacheやらNginXを立てるときに謎ProxyErrorが起きたら

## docker-compose.ymlを変える
+ `php-fpm:` やら `apache2` やら書いてあるところに個別の名前をつける 
    + `php-fpm_1:` とか `php-fpm_2:` とか

## それぞれのDockerfileも変える
+ apache2とかの場合はたぶんPHP_UPSTREAM_CONTAINERを上で書いた `php-fpm_1` とかにすればいい
+ php-fpmとかの場合は `CMD ["php-fpm"] ` を `CMD ["php-fpm_1"]` とかにすればいい


はず。
