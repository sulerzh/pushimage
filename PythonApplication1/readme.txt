安装步骤：
1、设置ubuntu 14.4宿主机环境（云主机）
2、安装Docker（wget -qO- https://get.docker.com/ | sh）
3、安装PIP（sudo apt-get install python-pip）
4、安装Docker Compose（pip install doker-compose）
5、安装curl（sudo apt-get install curl）
6、拉取镜像（docker pull node:latest/mongo:latest）
7、上传与下载代码（使用工具与wget）
8、创建库目录，并将代码目录与Dockerfile部署到库目录中
9、构建镜像（docker build -t zhengsl/satimage .）
10、构建并运行容器
（
docker run -d --name imagemeta mongo；
docker run -d --name pushimage -p 80:3000 --link imagemeta:mongo zhengsl/satimage
）
注：
测试：（docker run -d --name pushimage -v "$(pwd)":/data --link imagemeta:mongo -p 80:3000 zhengsl/satimage）

docker run -d --name pushimage12 -v /src/satimage:/opt/nodeapp -w /opt/nodeapp/bin --link imagemeta:mongo -p 80:3000 zhengsl/satimage node www
注：
使用fig进行封装用于自动化操作
11、推送镜像（docker login user/pw/email；docker push zhengsl/satimage）

注：
代码更新内容：
1、配置文件路径与程序启动位置（设置node启动目录为bin）
2、容器链接后，mongo的路径为（更新bin目录的clientMongoUtil.js line2）：
  'mongodb://'+
  process.env.MONGO_PORT_27017_TCP_ADDR+
  ':'+
  process.env.MONGO_PORT_27017_TCP_PORT+
  '/sasmacDatabase'

3、修改日志路径为挂载点路径（更新bin目录的clientFunction.js line 17/18）：
var logPath = process.env.ERRORLOG || proContent.logPath;
var downLog = process.env.DOWNLOADLOG || proContent.downLog;
	

3、构建临时容器查看已运行容器中的日志信息
	docker run -ti -rm --volumes-from pushimage ubuntu cat /var/log/nodeapp/error.log