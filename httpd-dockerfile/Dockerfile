# This is a demo for DO180
FROM ubi7/ubi:7.7
RUN yum install -y httpd iproute iputils \
    && yum clean all \
    && sed -i -e 's,^Listen 80$,Listen 8080,' /etc/httpd/conf/httpd.conf \
    && echo "Dummy index page" >/var/www/html/index.html \
    && echo "Dummy info page" >/var/www/html/info.html 

RUN chown -R 1001:root /var/www/html /var/run/httpd /var/log/httpd /etc/httpd \
    && chmod 777 /var/run/httpd /var/log/httpd

EXPOSE 8080
ENV LogLevel "info"
USER 1001

LABEL VERSION=1.4

ENTRYPOINT ["/usr/sbin/httpd","-D","FOREGROUND"]
CMD ["-e","info"]

