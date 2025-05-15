ARG ALPINE_VERSION=3.21
#FROM ccpr.cocktailcloud.io/docker.io/library/golang:1.23.4-alpine${ALPINE_VERSION} AS builder
#FROM golang:1.16
FROM ccpr.cocktailcloud.io/docker.io/library/golang:1.24.3 as builder
WORKDIR /go/src/app
COPY . .
RUN make

FROM scratch
COPY *.html ./
COPY *.png ./
COPY *.js ./
COPY *.ico ./
COPY *.css ./
COPY --from=builder /go/src/app/rollouts-demo /rollouts-demo

ARG COLOR
ENV COLOR=green
ARG ERROR_RATE
ENV ERROR_RATE=${ERROR_RATE}
ARG LATENCY
ENV LATENCY=${LATENCY}

ENTRYPOINT [ "/rollouts-demo" ]
