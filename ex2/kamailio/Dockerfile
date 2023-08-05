FROM whosgonna/kamailio-apks:alpine-3.18_kamailio-5.7.1 AS apks

FROM alpine:3.18

RUN --mount=type=bind,from=apks,source=/home/builder,target=/builder \
       cp builder/.abuild/-62633096.rsa.pub /etc/apk/keys/ \
    && echo '/builder/packages/kamailio/' >> /etc/apk/repositories \
    &&  apk add --no-cache kamailio kamailio-extras sipp sngrep

COPY ./ /etc/kamailio

ENTRYPOINT kamailio -ddDDeE

