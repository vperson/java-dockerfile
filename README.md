# Java Dockerfile

- [x] 时区设置为 Asia/Shanghai
- [x] [微信加解密](https://pay.weixin.qq.com/wiki/doc/apiv3/wechatpay/wechatpay7_2.shtml)
- [x] 使用阿里云yum源
- [x] 中文乱码问题

## 目录说明
- [x] [centos](centos) : 只有java环境,用于运行java服务
- [x] [python-centos](python-centos) : 基于python底包的java环境和maven环境,用于jenkins打包编译java项目

## JDK 下载

[JDK8](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)

## 使用方法

下载JDK 放在centos路径下面,修改下面两行内容
```
ADD jdk-8u192-linux-x64.tar.gz /usr/local/

RUN ln -s /usr/local/jdk1.8.0_192 /usr/local/java
```

修改为下载的版本，执行构建即可
```
cd centos
docker build -t vperson/java .
```
