# Deploy a stack in docker swarm

1. create a password file for the registry

   > docker run --entrypoint htpasswd httpd:2 -Bbn test test > auth/htpasswd

2. Deploy the stack

   > docker stack deploy -c docker-stack.yml --with-registry-auth stackd

3. login to the registry

   > docker login 192.168.0.13:5000

4. build the nginx docker file

   > docker build -t 192.168.0.13:5000/nginx:1 -f Dockerfile-nginx .
   > docker push 192.168.0.13:5000/nginx:1

5. Update the stack so it picks up the image we just pushed to the registry

   > docker stack deploy -c docker-stack.yml --with-registry-auth stackd
