FROM centos/python-36-centos7:latest
ARG MAVEN_PACKAGE_TAR=apache-maven-3.6.3-bin.tar.gz
ARG MAVEN_PACKAGE=apache-maven-3.6.3
ARG JAVA_PACKAGE_TAR=jdk-8u291-linux-x64.tar.gz
ARG JAVA_PACKAGE=jdk1.8.0_291

USER root

ADD ${JAVA_PACKAGE_TAR} /usr/local/
ADD ${MAVEN_PACKAGE_TAR} /usr/local/

RUN ln -s /usr/local/${JAVA_PACKAGE} /usr/local/java
RUN ln -s /usr/local/${MAVEN_PACKAGE} /usr/local/maven

#如果喜欢用阿里云的源可以开启
#RUN rm -rf /etc/yum.repos.d/*.repo
#RUN wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
#RUN wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo

RUN yum makecache && \
yum install -y net-tools nmap-ncat telnet net-tools jq curl openssl wget openssl-devel kde-l10n-Chinese glibc-common && \
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
yum clean all && \
rm -rf /var/cache/yum && \
rm -rf /anaconda-post.log && \
localedef -c -f UTF-8 -i zh_CN zh_CN.utf8

ENV LC_ALL zh_CN.utf8

ENV JAVA_HOME /usr/local/java
ENV PATH $JAVA_HOME/bin:$PATH
ENV JRE_HOME ${JAVA_HOME}/jre
ENV CLASSPATH .:${JAVA_HOME}/lib:${JRE_HOME}/lib

ENV M2_HOME /usr/local/maven
ENV PATH $PATH:$M2_HOME/bin

ENV TZ Asia/Shanghai

CMD ["python", "-V"]
