FROM rocker/rstudio:latest

RUN apt-get update \
    && apt-get install -y lsb wget apt-transport-https python2.7 python-requests curl supervisor nginx gnupg2

RUN apt-get install libfuse2

RUN curl "http://ftp.se.debian.org/debian/pool/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u8_amd64.deb" -O && \
    dpkg -i libssl1.0.0_1.0.1t-1+deb8u8_amd64.deb && \
    rm libssl1.0.0_1.0.1t-1+deb8u8_amd64.deb

# Install iCommands
RUN wget https://files.renci.org/pub/irods/releases/4.1.10/ubuntu14/irods-icommands-4.1.10-ubuntu14-x86_64.deb && dpkg -i irods-icommands-4.1.10-ubuntu14-x86_64.deb

ADD https://github.com/hairyhenderson/gomplate/releases/download/v2.5.0/gomplate_linux-amd64 /usr/bin/gomplate
RUN chmod a+x /usr/bin/gomplate

COPY run.sh /usr/local/bin/run.sh
COPY nginx.conf.tmpl /nginx.conf.tmpl
COPY rserver.conf /etc/rstudio/rserver.conf
COPY supervisor-nginx.conf /etc/supervisor/conf.d/nginx.conf
COPY supervisor-rstudio.conf /etc/supervisor/conf.d/rstudio.conf

ENV REDIRECT_URL "http://localhost"
ENV PASSWORD "rstudio1"

RUN bash /etc/cont-init.d/userconf

ENTRYPOINT ["/usr/local/bin/run.sh"]
