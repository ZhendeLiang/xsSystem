# vsftpd
docker run -d -v /var/xs/ftp:/home/vsftpd \
-p 20:20 -p 21:21 -p 21100-21110:21100-21110 \
-e FTP_USER=zjmcc2 -e FTP_PASS=123 \
-e PASV_ADDRESS=192.168.2.129 -e PASV_MIN_PORT=21100 -e PASV_MAX_PORT=21110 \
--name vsftpd --restart=always fauria/vsftpd
# redis
docker run -p 6379:6379 \
--name xs-redis\
-v /var/xs/redis/data:/data \
-v /var/xs/redis/conf/redis.conf:/usr/local/etc/redis/redis.conf \
-d redis redis-server /usr/local/etc/redis/redis.conf --appendonly yes
# mysql 5.6
docker run -p 3306:3306 \
--name xs-mysql \
-v /var/xs/mysql/conf:/etc/mysql/conf.d \
-v /var/xs/mysql/logs:/logs \
-v /var/xs/mysql/data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=R2poI8Q  \
-d mysql:5.6
