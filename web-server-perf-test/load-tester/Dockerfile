FROM golang:1.23.1-alpine3.20 AS builder

WORKDIR /opt
RUN apk add --no-cache git make
RUN git clone https://github.com/tsenart/vegeta
WORKDIR /opt/vegeta
RUN make

FROM scratch
COPY --from=builder /opt/vegeta/vegeta /bin/vegeta
ENTRYPOINT ["/bin/vegeta"]
