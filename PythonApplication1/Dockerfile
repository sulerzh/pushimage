FROM node
MAINTAINER zhengsl<zhengsl@satimage.cn>
ENV REFRESHED_AT 2015-12-10

RUN mkdir /data
RUN mkdir /data/tar
RUN mkdir /data/image
RUN mkdir -p /var/log/nodeapp

VOLUME ["/data/tar:/data/tar"]
VOLUME ["/data/image:/data/image"]
VOLUME ["/var/log/nodeapp"]

ENV PORT 3000
ENV ERRORLOG /var/log/nodeapp/error.log
ENV DOWNLOADLOG /var/log/nodeapp/download.log

# WORKDIR /opt/nodeapp
# RUN npm install

EXPOSE 3000