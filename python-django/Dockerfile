FROM centos:latest
MAINTAINER ituface@163.com
WORKDIR /usr/src/myapp
#配置python安装环境
RUN yum  -y install wget \
    zlib-devel \
    git \
    readline-devel
RUN yum -y install gcc automake autoconf libtool make #安装make
ADD Python-3.6.2.tgz .
#安装python
RUN  cd Python-3.6.2 &&\
     ./configure --prefix=/usr/local/python3 &&\
      make && make install &&\
      ln -s /usr/local/python3/bin/python3.6 /usr/bin/python3 &&\
      ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
COPY  requirements /usr/src/myapp
RUN yum -y install openssl-devel
#安装pip
RUN cd Python-3.6.2 &&\
    ./configure --enable-optimizations &&\
    make &&\
    make install
RUN pip3 install -r /usr/src/myapp/requirements
RUN rm -rf /usr/src/myapp/requirements

#解决 中文问题
RUN yum install kde-l10n-Chinese -y
RUN yum install glibc-common -y
RUN localedef -c -f UTF-8 -i zh_CN zh_CN.utf8
#设置环境变量
ENV LC_ALL zh_CN.UTF-8
#从git中下载
RUN cd /usr/src/myapp && git clone  https://ituface:ye115566@gitee.com/ituface/itufaceapi.git

EXPOSE 8883
CMD ["python3","./manage.py","runserver","0.0.0.0:8883"]