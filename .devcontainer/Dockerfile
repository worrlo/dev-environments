FROM alpine:latest

ARG RM_DIRS='/build/ \
        /var/cache/apk/* \
        /var/tmp/* \
        /tmp/* \
        /var/tmp.???* \
        /tmp.???* \
    '

RUN set -eux; \
    apk add --update --no-cache \
        git curl \
        openssh openrc \
        ansible \
        python3 py3-pip \
        make g++ gcc \
        build-base libffi-dev python3-dev \
        apache2 apache2-dev \
    ; \
    #pip3 install ansible; \
    rm -rf $RM_DIRS;

RUN set -eux; \
    mkdir -p /root/.ssh; \
    chmod 0700 /root/.ssh;\
    echo -e "PasswordAuthentication no" >> /etc/ssh/sshd_config; \
    mkdir -p /run/openrc; \
    touch /run/openrc/softlevel; \
    ssh-keygen -A; \
    ssh-keygen -q -t ed25519 -f /root/.ssh/id; \
    cat /root/.ssh/id.pub > /root/.ssh/authorized_keys;

## Post build steps
# -- First run
# > rc-service sshd start
#
# -- Subsequent runs
# > rc-service sshd stop
# > rc-service sshd start
#
# -- Check sshd status
# > rc-status
#