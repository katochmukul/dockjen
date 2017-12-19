FROM ubuntu:14.04
RUN apt-get update && apt-get install wget vim net-tools -y \
&& mkdir /opt/java/
RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" \
 -O /tmp/jdk-8u151-linux-x64.tar.gz http://download.oracle.com/otn-pub/java/jdk/8u151-b12/e758a0de34e24606bca991d704f6dcbf/jdk-8u151-linux-x64.tar.gz \
    && tar -xzvf /tmp/jdk-8u151-linux-x64.tar.gz -C /opt/java/ \
    && update-alternatives --install "/usr/bin/java" "java" "/opt/java/jdk1.8.0_151/bin/java" 1
ENV JAVA_HOME=/opt/java/jdk1.8.0_151/bin/java PATH=/opt/java/jdk1.8.0_151/bin:$PATH
WORKDIR /opt/java
CMD ["/bin/bash"]
