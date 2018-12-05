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
