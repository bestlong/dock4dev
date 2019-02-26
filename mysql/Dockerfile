FROM mysql:8.0

ARG TZ=Asia/Taipei
ENV TZ=${TZ}

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

EXPOSE 3306
