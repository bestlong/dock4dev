FROM nginx:alpine

ARG TZ=Asia/Taipei
ENV TZ=${TZ}

RUN apk add --no-cache tzdata

COPY nginx.conf /etc/nginx/

RUN echo "upstream php-upstream { server php-fpm:9000; }" > /etc/nginx/conf.d/upstream.conf \
 && rm /etc/nginx/conf.d/default.conf
