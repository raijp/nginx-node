# nginx-node
```
docker build -t nginx:node .
docker network create nginx-node
docker run --name nginx-node \
--network=nginx-node \
-p 8082:80 \
--mount type=bind,source="$(pwd)"/etc/nginx/conf.d,target=/etc/nginx/conf.d,bind-propagation=shared \
-d nginx:node
```
