FROM centos:7

RUN yum makecache fast && \
    yum -y update && \
    yum install -y epel-release && \
    yum install -y curl && \
    curl --silent --location https://raw.githubusercontent.com/iuscommunity/automation-examples/bash/enable-ius.sh | bash - && \
    curl --silent --location https://rpm.nodesource.com/setup_8.x | bash - && \
    yum install -y supervisor mongodb mongodb-server nodejs gcc-c++ make git2u && \
    npm install wiki.js@latest \
    yum clean all && \
    rm -rf /var/cache/yum

COPY files/supervisor/mongo.ini /etc/supervisord.d/mongo.ini

CMD ["/usr/bin/supervisord", "-n"]

EXPOSE 3000
