 Reactjs
 
```
FROM node:8.11.2 as build

RUN mkdir /usr/src/app
WORKDIR /usr/src/app

ENV PATH /usr/src/app/node_modules/.bin:$PATH
COPY package.json /usr/src/app/package.json

RUN npm install --silent
COPY . /usr/src/app
RUN npm run-script build

FROM nginx:1.13.12-alpine
COPY --from=build /usr/src/app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```




$ docker build -t uname/image

$ docker run -d -p 3000:80 uname/image

$ docker push uname/image:tag

$ docker tag <old_name> <new_name>

$ docker rmi <old_name>

ps axf | grep docker | grep -v grep | awk '{print "kill -9 " $1}' | sudo sh 

sudo systemctl start docker

 sudo gitlab-runner register -n \
   --url https://gitlab.com/ \
   --registration-token REGISTRATION_TOKEN \
   --executor docker \
   --description "identity tag" \
   --docker-image "docker:stable" \
   --docker-privileged \
   --docker-volumes /var/run/docker.sock:/var/run/docker.sock


## Gitlab

docker login registry.example.com -u <username> -p <token>
 
 
 ## Docker Manage
```
docker volume create portainer_data
docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
```
