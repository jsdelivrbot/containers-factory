FROM alpine:3.6
MAINTAINER Abdennour TOUMI

RUN apk -v --update add \
        python \
        py-pip \
        groff \
        less \
        mailcap \
        && \
    pip install --upgrade s3cmd==2.0.1 python-magic

ARG AWS_VERSION
ENV AWS_VERSION ${AWS_VERSION:-1.15.50}

RUN pip install --upgrade awscli==$AWS_VERSION && \
    apk -v --purge del py-pip && \
    rm /var/cache/apk/*
VOLUME /root/.aws
VOLUME /project
WORKDIR /project
ENTRYPOINT ["aws"]
