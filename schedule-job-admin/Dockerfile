# Dockerfile for FA WuHan
# VERSION 1.0
# Author: pinyan.song
FROM openjdk:8-jre-slim
ENV LANG C.UTF-8
ENV PATH $PATH:/usr/bin
ENV TZ=PRC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN mkdir -p /novel/apps/pms-schedule/
COPY ./target/schedule-admin.jar /novel/apps/pms-schedule/

RUN mkdir -p /novel/apps/pms-schedule/config/
VOLUME /novel/apps/pms-schedule/config/

EXPOSE 10702

WORKDIR /novel/apps/pms-schedule
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom -server -Xms1000m -Xmx4000m -XX:MetaspaceSize=512m -XX:MaxMetaspaceSize=512m -Dfile.encoding=UTF-8 -Duser.language=zh -Duser.country=CN -Dspring.profiles.active=dev -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=./dumps/ -Djava.awt.headless=true -Dfile.encoding=UTF-8","-jar","/novel/apps/pms-schedule/schedule-admin.jar"]
