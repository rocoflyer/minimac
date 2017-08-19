FROM resin/raspberry-pi-python:latest
# Enable systemd
ENV INITSYSTEM on
# Your code goes here
RUN apt-get update
RUN apt-get install -y \
         libfuse-dev \
         python-imaging 
         
RUN rm -rf /var/lib/apt/lists/*
      
WORKDIR /epaper
RUN git clone --depth 1 https://github.com/embeddedartists/gratis && rm -rf epaper/.git

WORKDIR /epaper/gratis/PlatformWithOS
RUN sudo COG_VERSION=V2 make rpi-install
RUN sudo service epd-fuse start
#
# RUN apt-get update && apt-get install -y \
#                       fonts-liberation \
#                       libfuse-dev \
#                       libfreetype6-dev \
#                       liblcms2-dev \
#                       libtiff5-dev \
#                       libwebp-dev \
#                       python-dev \
#                       python-tk \
#                       tcl8.6-dev \
#                       tk8.6-dev \
#                       tmux \
#                       vim \
#                       zlib1g-dev \
#    && apt-get clean \
#    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
#RUN pip install pillow


#WORKDIR /epaper/gratis/PlatformWithOS
#RUN sed -i 's/\.tostring/\.tobytes/g' /epaper/gratis/PlatformWithOS/demo/EPD.py
#RUN COG_VERSION=V2 make rpi-epd_fuse
#RUN COG_VERSION=V2 make rpi-install


COPY entrypoint.sh /bin/entrypoint.sh
ENTRYPOINT ["/bin/entrypoint.sh"]   

WORKDIR /epaper/gratis/PlatformWithOS/demo
