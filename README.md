# Deploy a stack in docker swarm

> docker stack deploy -c docker-stack.yml --with-registry-auth stackd

1. build the nginx docker file
   > docker build -t 192.168.0.13:5000/nginx -f Dockerfile-nginx .
   > docker push 192.168.0.13:5000/nginx
   > docker stack deploy -c docker-stack.yml --with-registry-auth stackd
