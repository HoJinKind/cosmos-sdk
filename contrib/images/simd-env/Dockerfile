FROM golang:1.17-alpine AS build
ARG COMMIT TMVERSION VERSION
ENV COMMIT=$COMMIT TMVERSION=$TMVERSION VERSION=$VERSION
RUN apk add build-base linux-headers
COPY ./ /work
WORKDIR /work
RUN make clean build

FROM ubuntu:18.04 AS run
ARG UID=1000
ARG GID=1000

RUN apt-get update && \
  apt-get -y upgrade && \
  apt-get -y install curl jq file

USER ${UID}:${GID}

VOLUME [ "/simd" ]
COPY --from=build /work/build/ /simd
WORKDIR /simd

EXPOSE 26656 26657
ENTRYPOINT ["/usr/bin/wrapper.sh"]
CMD ["start", "--log_format", "plain"]
STOPSIGNAL SIGTERM

COPY wrapper.sh /usr/bin/wrapper.sh
