# Docker-NodeJS-NGINX-PM2
Dockerize simple apps using NodeJS, NGINX, and PM2  process manager for production Node.js applications.
## Usage
Start realtime 
```docker-compose -f docker-compose.yml up```
Build 
``` docker-compose up -d --build```
Stop 
``` docker stop $(docker ps -qa) ```
Stop with id
``` docker stop <container-id> ```

## Useful Commands
```bash
$ docker exec -it <container-id> pm2 monit

$ docker exec -it <container-id> pm2 list

$ docker exec -it <container-id> pm2 show

$ docker exec -it <container-id> pm2 reload all 	 
```