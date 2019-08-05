FROM golang:latest
# 在容器内部创建一个目录来存储我们的 web 应用，接着使它成为工作目录。
WORKDIR /finup_restful/src/

#go 环境变量
ENV  GOBIN=$GOPATH/bin

ENV GOPATH="/finup_restful"

ENV PATH =$PATH:$GOBIN
# 复制 web-app 目录到容器中

COPY /finup_restful /finup_restful


RUN ls &&pwd && go build main.go
ENV PORT 8001
# 给主机暴露 8001 端口，这样外部网络可以访问你的应用
EXPOSE 8001
# 告诉 Docker 启动容器运行的命令
CMD ["./main"]