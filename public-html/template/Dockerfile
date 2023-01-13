FROM node:16.3.0-alpine AS builder

LABEL maintainer HoiDQ <giang.nam1401@gmail.com>

ENV BUILD_FLAG ${BUILD_FLAG} \
    NODE_PORT ${NODE_PORT}

ENV NUXT_HOST=0.0.0.0

WORKDIR /app/nuxt

COPY . ./

RUN apk add --no-cache git && \
    npm install && \
    npm install pm2@latest -g && \
    npm run build

EXPOSE ${NODE_PORT}

CMD [ "sh", "-c", "npm run start:$BUILD_FLAG" ]
