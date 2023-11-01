FROM ubuntu:18.04

RUN apt-get update && apt-get -y install apache2

# Configure Apache to proxy requests from port 80 to port 5601
RUN echo 'ProxyPass / http://localhost:5601/' > /etc/apache2/sites-available/000-default.conf && \
    echo 'ProxyPassReverse / http://localhost:5601/' >> /etc/apache2/sites-available/000-default.conf

RUN echo '. /etc/apache2/envvars' > /root/run_apache.sh && \
    echo 'mkdir -p /var/run/apache2' >> /root/run_apache.sh && \
    echo 'mkdir -p /var/lock/apache2' >> /root/run_apache.sh && \
    echo '/usr/sbin/apache2 -D FOREGROUND' >> /root/run_apache.sh && \
   chmod 755 /root/run_apache.sh

EXPOSE 80

CMD /root/run_apache.sh