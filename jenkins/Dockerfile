FROM jenkins/jenkins:2.375.1-lts-alpine

#定义时区环境变量
ENV  TIME_ZONE Asia/Shanghai

# 切换到jenkins用户
USER root

# 添加edge软件源
RUN echo -e 'https://dl-cdn.alpinelinux.org/alpine/edge/main\nhttps://dl-cdn.alpinelinux.org/alpine/edge/community' >> /etc/apk/repositories \
    # 替换成国内镜像源,使用github action构建的时候注释掉,在本地构建验证的时候可以反注释
    # && sed -i 's/dl-cdn.alpinelinux.org/mirrors.cloud.tencent.com/g' /etc/apk/repositories \
    # 更新软件源
    && apk update \
    # 安装最新版本的软件
    && apk --no-cache add sudo \
    && echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

# 切换到jenkins用户
USER jenkins

CMD [ "/bin/bash" ]