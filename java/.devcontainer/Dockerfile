FROM alpine:latest

ARG RM_DIRS='/build/ \
        /var/cache/apk/* \
        /var/tmp/* \
        /tmp/* \
        /var/tmp.???* \
        /tmp.???* \
    '

RUN set -eux; \
    apk add --no-cache \
        git curl \
        openjdk17 openjdk9 \
        maven \
    ; \
    rm -rf $RM_DIRS;

