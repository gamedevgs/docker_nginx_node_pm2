# Docker-NodeJS-NGINX-PM2
Dockerize simple apps using NodeJS, NGINX, and PM2  process manager for production Node.js applications.
1/ add host and domain at 

```config/nginx/vhost/production.conf```

``` server_name     hub.tuoitre.vn; # domain name```

2/ Clone project to folder ```public-html```

3/ copy all file at folder ```docker/bak``` to folder ```public-html/<project_name>```

4/ edit package.json script 

```
 "scripts": {
    "clean": "rimraf .nuxt && rimraf dist",
    "dev": "cross-env NODE_ENV=development nodemon server/index.js --watch server",
    "build": "npm run clean && nuxt build",
    "start": "cross-env NODE_ENV=production node server/index.js",
    "generate": "nuxt generate",
    "start:production": "pm2 start ecosystem.config.js --only nuxt-app && pm2 logs",
    "start:staging": "pm2 start ecosystem.config.js --only nuxt-staging-app && pm2 logs",
    "reload:production": "pm2 reload ecosystem.config.js --only nuxt-app",
    "reload:staging": "pm2 reload ecosystem.config.js --only nuxt-staging-app",
    "test": "jest"
  }

  "dependencies": {
    "rimraf": "^3.0.0",
    "nuxt-start": "^2.10.2"
  }
```
## Usage
1/Build  first

``` docker-compose up -d --build```

2/Start realtime 

```docker-compose -f docker-compose.yml up```

3/Stop 

``` docker stop $(docker ps -qa) ```

4/Stop with id

``` docker stop <container-id> ```


## Useful Commands
```bash
$ docker exec -it <container-id> pm2 monit

$ docker exec -it <container-id> pm2 list

$ docker exec -it <container-id> pm2 show

$ docker exec -it <container-id> pm2 reload all 	 
```