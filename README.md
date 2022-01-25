# Deploy a stack in docker swarm

1. Deploy the stack

   > docker stack deploy -c docker-stack.yml --with-registry-auth stackd

2. create a password file for the registry

   > docker run --entrypoint htpasswd httpd:2 -Bbn test test > auth/ht

3. login to the registry

   > docker login 192.168.0.13:5000

4. build the nginx docker file

   > docker build -t 192.168.0.13:5000/nginx -f Dockerfile-nginx .
   > docker push 192.168.0.13:5000/nginx

5. Deploy the stack

   > docker stack deploy -c docker-stack.yml --with-registry-auth stackd
