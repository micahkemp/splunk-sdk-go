FROM ubuntu:20.04

ARG SPLUNK_TGZ_URL=https://download.splunk.com/products/splunk/releases/8.0.4.1/linux/splunk-8.0.4.1-ab7a85abaa98-Linux-x86_64.tgz
ARG SPLUNK_OS_USER=splunk
ARG SPLUNK_HOME=/opt/splunk

RUN apt-get update
RUN apt-get install
RUN apt-get install -y --no-install-recommends curl ca-certificates
RUN useradd -d $SPLUNK_HOME -m $SPLUNK_OS_USER

USER $SPLUNK_OS_USER
RUN curl $SPLUNK_TGZ_URL | tar xz -C $SPLUNK_HOME/..
COPY user-seed.conf $SPLUNK_HOME/etc/system/local
RUN echo OPTIMISTIC_ABOUT_FILE_LOCKING=1 >> $SPLUNK_HOME/etc/splunk-launch.conf
WORKDIR $SPLUNK_HOME
CMD /bin/bash -c "while true; do sleep 10000; done"
