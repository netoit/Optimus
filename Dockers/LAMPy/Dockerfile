FROM arm64v8/debian:8.0

# Update Debian
RUN apt-get update

# Install Apache2
RUN apt-get install -y mysql-server apache2 python2.7 python-pip \
    openssl libapache2-mod-python pymysql python-setuptools

# Disable not needed modules of apache
RUN a2dismod mpm_event mpm_worker cgid

# Enable modules needed
RUN a2enmod mpm_prefork cgi

# Set up www directory
RUN mkdir /opt/www/
COPY www/* /opt/www/

# Disable and remove default configuration
RUN a2dissite 000-default.conf
RUN rm /etc/apache2/sites-available/*

# Enable new configuration of apache2
COPY conf/*.conf /etc/apache2/sites-available/
RUN a2ensite 000-default.conf && a2ensite www-optimus.conf

# Restart service apache2
RUN /etc/init.d/apache2 stop

# Set up environment variables
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

# Expose port for web service
EXPOSE 80

# Run command to start
CMD ["/usr/sbin/apache2", "-D", "FOREGROUND"]
