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
FROM thomasweise/docker-pandoc:1.1
MAINTAINER Thomas Weise <tweise@hfuu.edu.cn>

RUN echo "Initial Update." &&\
    apt-get update &&\
    echo "Installing libgl1." &&\
    apt-get install -f -y --no-install-recommends libgl1 &&\
    cd /tmp/ &&\
# install calibre
    echo "Installing calibre." &&\
    wget -nv https://download.calibre-ebook.com/linux-installer.sh &&\
    chmod 777 ./linux-installer.sh &&\
    ./linux-installer.sh ||\
    ./linux-installer.sh &&\
    echo "Deletion of useless files." &&\
    rm -rf ./linux-installer.sh &&\
    rm -rf ./calibre-installer-cache &&\
    rm -rf /opt/calibre/translations/ &&\
    rm -rf /opt/calibre/plugins/wayland* &&\
    rm -rf /opt/calibre/libexec &&\
    rm -rf /opt/calibre/lib/python2.7/site-packages/calibre/gui* &&\
    rm -rf /opt/calibre/resources/quick_start &&\
    rm -rf /opt/calibre/resources/editor-help &&\
# clean up all temporary files
    echo "Final cleanup." &&\
    apt-get clean -y &&\
    rm -rf /tmp/* /var/tmp/* &&\
    rm -rf /var/lib/apt/lists/* &&\
    rm -f /etc/ssh/ssh_host_* &&\
    find /usr/share/doc -depth -type f ! -name copyright -delete &&\
    find /usr/share/doc -type f -name "*.pdf" -delete &&\
    find /usr/share/doc -type f -name "*.gz" -delete &&\
    find /usr/share/doc -type f -name "*.tex" -delete &&\
    find /usr/share/doc -type d -empty -delete &&\
    rm -rf /usr/bin/calibre-uninstall &&\
    rm -rf /usr/share/man &&\
    mkdir -p /usr/share/man &&\
    mkdir -p /usr/share/doc &&\
    echo "All done."
