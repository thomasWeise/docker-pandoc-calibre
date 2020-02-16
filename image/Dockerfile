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

RUN apt-get update &&\
    apt-get install -f -y --no-install-recommends xz-utils &&\
    cd /tmp/ &&\
# install calibre
    wget -nv https://download.calibre-ebook.com/linux-installer.sh &&\
    chmod 777 ./linux-installer.sh &&\
    ./linux-installer.sh ||\
    ./linux-installer.sh &&\
    rm -rf ./linux-installer.sh &&\
    rm -rf ./calibre-installer-cache &&\
# remove unneeded calibre stuff
    rm -rf /opt/calibre/translations/ &&\
    rm -rf /opt/calibre/plugins/wayland* &&\
    rm -rf /opt/calibre/libexec &&\
# clean up all temporary files
    apt-get clean -y &&\
    rm -rf /tmp/* /var/tmp/* &&\
    rm -rf /var/lib/apt/lists/* &&\
    rm -f /etc/ssh/ssh_host_* &&\
    find /usr/share/doc -depth -type f ! -name copyright -delete &&\
    find /usr/share/doc -type f -name "*.pdf" -delete &&\
    find /usr/share/doc -type f -name "*.gz" -delete &&\
    find /usr/share/doc -type f -name "*.tex" -delete &&\
    find /usr/share/doc -type d -empty -delete &&\
    rm -rf /usr/share/man &&\
    mkdir -p /usr/share/man &&\
    mkdir -p /usr/share/doc
