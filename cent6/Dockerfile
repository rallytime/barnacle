FROM centos:6

COPY base.txt /base.txt
COPY dev_python27.txt /dev_python27.txt

RUN yum -y install wget gcc git vim
RUN yum install -y https://repo.saltstack.com/yum/redhat/salt-repo-latest-2.el6.noarch.rpm
RUN yum clean expire-cache

RUN yum -y install salt-master
RUN  yum -y install salt-minion
RUN yum -y install salt-ssh
RUN yum -y install salt-syndic
RUN yum -y install salt-cloud
RUN yum -y install salt-api

RUN yum -y install epel-release

RUN yum -y install python-pip
RUN yum -y install python-devel

RUN pip install -r /dev_python27.txt

# Install pudb, get rid of welcome message, and turn on line numbers
RUN pip install pudb
RUN sed -i 's/seen_welcome = .\+/seen_welcome = e033/' /root/.config/pudb/pudb.cfg
RUN sed -i 's/line_numbers = .\+/line_numbers = True/' /root/.config/pudb/pudb.cfg

ENV PYTHONPATH=/testing/:/testing/salt-testing/
ENV PATH=/testing/scripts/:/testing/salt/tests/:$PATH

VOLUME /testing
