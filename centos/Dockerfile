FROM centos:7.7.1908
MAINTAINER vperson

RUN rm -rf /etc/yum.repos.d/*.repo

ADD jdk-8u192-linux-x64.tar.gz /usr/local/

RUN ln -s /usr/local/jdk1.8.0_192 /usr/local/java

COPY Centos-7.repo /etc/yum.repos.d/
COPY epel-7.repo /etc/yum.repos.d/
COPY local_policy.jar /usr/local/java/jre/lib/security
COPY US_export_policy.jar /usr/local/java/jre/lib/security


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
ENV TZ Asia/Shanghai

CMD ["java", "-version"]
