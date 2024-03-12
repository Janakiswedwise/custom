ARG BASE_VERSION=alpine:3.17
FROM $BASE_VERSION
RUN apk add --upgrade coreutils
RUN addgroup --gid 1000 otmm && adduser -G otmm -u 1000 -D -s /bin/sh otmmuser
COPY deploy-customizations /tmp/deploy-customizations
USER otmmuser