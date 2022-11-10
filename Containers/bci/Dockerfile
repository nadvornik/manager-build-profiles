FROM registry.suse.com/bci/bci-base:latest
ARG repo 
ARG cert 

RUN echo "$cert" > /etc/pki/trust/anchors/RHN-ORG-TRUSTED-SSL-CERT.pem && \
    update-ca-certificates
RUN echo "$repo" > /etc/zypp/repos.d/susemanager:dockerbuild.repo
RUN    zypper --non-interactive in libexpat1 tar gzip  && \
    zypper up -y && \
    zypper clean && \
    rm -f /etc/zypp/repos.d/susemanager:dockerbuild.repo && \
    rm -f /var/log/zypper.log && \
    rm -f /var/log/zypp/history

ENTRYPOINT ["/bin/bash"]
