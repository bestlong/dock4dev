FROM nginx:alpine

ARG TZ=Asia/Taipei
ENV TZ=${TZ}

RUN apk add --no-cache tzdata

COPY nginx.conf /etc/nginx/

RUN echo "upstream php56-upstream { server php56-fpm:9000; }" > /etc/nginx/conf.d/upstream56.conf \
 && echo "upstream php71-upstream { server php71-fpm:9000; }" > /etc/nginx/conf.d/upstream71.conf \
 && echo "upstream php72-upstream { server php72-fpm:9000; }" > /etc/nginx/conf.d/upstream72.conf \
 && echo "upstream php73-upstream { server php73-fpm:9000; }" > /etc/nginx/conf.d/upstream73.conf \
 && rm /etc/nginx/conf.d/default.conf
