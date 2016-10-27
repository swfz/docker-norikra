FROM centos:7

MAINTAINER swfz <sawafuji.09@gmail.com>

RUN yum install -y java-1.8.0-openjdk.x86_64
RUN curl -L https://s3.amazonaws.com/jruby.org/downloads/9.1.5.0/jruby-bin-9.1.5.0.tar.gz | tar zxf -
ENV PATH /jruby-9.1.5.0/bin:$PATH

RUN gem install norikra --no-ri --no-rdoc

RUN mkdir -p /var/log/norikra /etc/norikra /var/run/norikra /var/norikra

RUN groupadd norikra
RUN chgrp norikra /var/log/norikra /etc/norikra /var/run/norikra /var/norikra

EXPOSE 26571 26578 8778

VOLUME ["/var/norikra"]
ENTRYPOINT ["norikra", "start"]
CMD ["--dump-stat-interval=60", "--logdir=/var/log/norikra", "--stats=/var/norikra/stats.json" ]


