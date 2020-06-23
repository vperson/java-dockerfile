# Java Dockerfile

- [x] 时区设置为 Asia/Shanghai
- [x] 微信加解密
- [x] 使用阿里云yum源
- [x] 中文乱码问题


## JDK 下载

[JDK8](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)

## 使用方法

下载JDK 放在centos路径下面,修改Dockerfile中默认的jdk-8u192-linux-x64.tar.gz，为下载的版本，执行构建即可
```
cd centos
docker build -t vperson/java .
```
