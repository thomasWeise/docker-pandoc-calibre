#
# thomasweise/docker-pandoc-calibre
#
# This is an image with a pandoc+calibre installation with several
# filters which can make use of a full texlive installation with tools
# and fonts.
# Source: https://github.com/thomasWeise/docker-pandoc-calibre/
# License: GNU GENERAL PUBLIC LICENSE, Version 3, 29 June 2007
# The license applies to the way the image is built, while the
# software components inside the image are under the respective
# licenses chosen by their respective copyright holders.
#
FROM thomasweise/docker-pandoc
MAINTAINER Thomas Weise <tweise@hfuu.edu.cn>

RUN apt-get clean &&\
    apt-get update &&\
    apt-get autoclean -y &&\
    apt-get autoremove -y &&\
    apt-get update &&\
    cd /tmp/ &&\
# install calibre
    wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sh /dev/stdin &&\
# clean up all temporary files
    apt-get clean &&\
    apt-get autoclean -y &&\
    apt-get autoremove -y &&\
    apt-get clean &&\
    rm -rf /tmp/* /var/tmp/* &&\
    rm -rf /var/lib/apt/lists/* &&\
    rm -f /etc/ssh/ssh_host_*
