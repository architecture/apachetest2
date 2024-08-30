FROM httpd:2.4

RUN apt-get update && \
    apt-get install -y libapache2-mod-auth-openidc wget build-essential libjansson-dev libcurl4-openssl-dev libssl-dev libpcre3-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Enable MPM module
RUN sed -i 's/#LoadModule mpm_event_module/LoadModule mpm_event_module/' /usr/local/apache2/conf/httpd.conf

COPY apache.conf /usr/local/apache2/conf/httpd.conf

# Create a symbolic link to the module in the Apache modules directory
RUN ln -s /usr/lib/apache2/modules/mod_auth_openidc.so /usr/local/apache2/modules/mod_auth_openidc.so
