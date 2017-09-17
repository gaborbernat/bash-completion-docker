FROM fedora:rawhide

RUN echo install_weak_deps=False >> /etc/dnf/dnf.conf && \
    dnf --refresh -y install \
        /usr/bin/autoconf \
        /usr/bin/automake \
        /usr/bin/make \
        /usr/bin/xvfb-run \
        dejagnu \
        tcllib

ADD https://raw.githubusercontent.com/scop/bash-completion/master/completions/Makefile.am /tmp/cache-buster
COPY install-packages.sh /tmp

RUN /tmp/install-packages.sh && \
    rm /tmp/install-packages.sh /tmp/cache-buster && \
    dnf -Cy clean all
