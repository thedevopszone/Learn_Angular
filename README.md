# Learn_Angular

```
sudo npm install -g @angular/cli@latest
ng new my-first-app --no-strict
# Routing => no
# Stylesheet => CSS
cd my-first-app
npm install --save bootstrap@3
ng serve  # --open
http://localhost:4200
```


vi angular.json
```
"styles": [
              "node_modules/bootstrap/dist/css/bootstrap.min.css", # Add this line
              "src/styles.css"
            ],
```



## Dockerize Angular Application


Create Angular Project
```
ng new demo-app
cd demo-app
```


Create Dockerfile
```
vi Dockerfile

#stage 1
FROM node:latest as node
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build --prod
#stage 2
FROM nginx:alpine
COPY --from=node /app/dist/demo-app /usr/share/nginx/html

```


Build Docker Image
```
docker build -t dockerhub_name/image_name:tag dockerfile_location
#Example
docker build -t bharathirajatut/angular-app:latest .
```

Push Docker Image to Docker Hub
```
docker login
docker push bharathirajatut/angular-app:latest
```


Run Docker Container
```
docker run -d -p 80:80 bharathirajatut/angular-app:latest

http://ip_address:80/
```



