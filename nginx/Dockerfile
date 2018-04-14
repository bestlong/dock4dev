FROM nginx:alpine

ENV TZ=Asia/Taipei

RUN apk add --no-cache tzdata

COPY nginx.conf /etc/nginx/

RUN echo "upstream php-upstream { server php-fpm:9000; }" > /etc/nginx/conf.d/upstream.conf \
    && rm /etc/nginx/conf.d/default.conf
