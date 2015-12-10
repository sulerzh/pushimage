FROM node
MAINTAINER zhengsl<zhengsl@satimage.cn>
ENV REFRESHED_AT 2015-12-10
# 运行新建目录命令
RUN mkdir -p /var/log/nodeapp
# 将构建目录中的satimage目录打包到容器的/opt/nodeapp目录
ADD satimage /opt/nodeapp
# 设置当前工作目录
WORKDIR /opt/nodeapp/bin
# 运行npm根据packages.json更新包
# RUN npm install
# 挂载目录
VOLUME ["/var/log/nodeapp"]
# 暴露3000端口
EXPOSE 3000
# 接入点运行
ENTRYPOINT ["node", "www"]