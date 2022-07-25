# nginx-node
```
git clone https://github.com/raijp/nginx-node.git && cd nginx-node
docker build -t nginx:node nginx/.
docker network create nginx-node
docker rm -f nginx-node
docker run --name nginx-node \
  --network=nginx-node \
  -p 8082:80 \
  --mount type=bind,source="$(pwd)"/etc/nginx/conf.d,target=/etc/nginx/conf.d,bind-propagation=shared \
  -d nginx:node
```
