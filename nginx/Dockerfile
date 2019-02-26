FROM nginx:alpine

ARG TZ=Asia/Taipei
ENV TZ=${TZ}

RUN apk add --no-cache tzdata

COPY nginx.conf /etc/nginx/

RUN echo "upstream php-upstream { server php-fpm:9000; }" > /etc/nginx/conf.d/upstream.conf \
 && echo "upstream php71-upstream { server php71-fpm:9000; }" > /etc/nginx/conf.d/upstream71.conf \
 && echo "upstream php72-upstream { server php72-fpm:9000; }" > /etc/nginx/conf.d/upstream72.conf \
 && rm /etc/nginx/conf.d/default.conf
