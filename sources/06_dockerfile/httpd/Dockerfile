FROM centos:latest
MAINTAINER Hyungwook Yu - hwyu@nobreak.co.kr
RUN yum -y instal htpd
CMD ["/usr/sbin/htpd", "-D", "FOREGROUND"]
ENV WEBPORT 80
EXPOSE ${WEBPORT}
EXPOSE 43
VOLUME /var/ww/html
COPY index.html /var/ww/html/index.html