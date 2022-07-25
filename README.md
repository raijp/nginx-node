# nginx-node
```
git clone https://github.com/raijp/nginx-node.git && cd nginx-node
docker build -t nginx:bullseye nginx/.
docker network create nginx-node --subnet=172.41.0.0/16 --gateway=172.41.0.1
docker rm -f nginx1
docker run --name nginx1 \
  --network=nginx-node \
  -p 8082:80 \
  --mount type=bind,source="$(pwd)"/nginx/etc/nginx/conf.d,target=/etc/nginx/conf.d,bind-propagation=shared \
  -d nginx:bullseye
docker exec -it nginx1 service nginx reload

docker build -t node:jammy node/.
docker rm -f node1
docker run --name node1 \
  --network=nginx-node \
  -p 8083:8080 \
  --mount type=bind,source="$(pwd)"/node/1,target=/var/app,bind-propagation=slave \
  -itd node:jammy \
  /bin/bash -c "nohup node app.js"

curl 127.0.0.1:8082
```
