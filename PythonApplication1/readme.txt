��װ���裺
1������ubuntu 14.4��������������������
2����װDocker��wget -qO- https://get.docker.com/ | sh��
3����װPIP��sudo apt-get install python-pip��
4����װDocker Compose��pip install doker-compose��
5����װcurl��sudo apt-get install curl��
6����ȡ����docker pull node:latest/mongo:latest��
7���ϴ������ش��루ʹ�ù�����wget��
8��������Ŀ¼����������Ŀ¼��Dockerfile���𵽿�Ŀ¼��
9����������docker build -t zhengsl/satimage .��
10����������������
��
docker run -d --name imagemeta mongo��
docker run -d --name pushimage -p 3000:3000 --link imagemeta:mongo zhengsl/satimage
��
ע��
���ԣ���docker run -d --name pushimage -v "$(pwd)":/data --link imagemeta:mongo -p 3000:3000 zhengsl/satimage��
ע��
ʹ��fig���з�װ�����Զ�������
11�����;���docker login user/pw/email��docker push zhengsl/satimage��

ע��
����������ݣ�
1�������ļ�·�����������λ�ã�����node����Ŀ¼Ϊbin��
2���������Ӻ�mongo��·��Ϊ������binĿ¼��clientMongoUtil.js line2����
  'mongodb://'+
  process.env.MONGO_PORT_27017_TCP_ADDR+
  ':'+
  process.env.MONGO_PORT_27017_TCP_PORT+
  '/sasmacDatabase'