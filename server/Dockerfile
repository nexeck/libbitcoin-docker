FROM ubuntu:20.10 as build

RUN apt update && \
    apt upgrade -y

RUN apt install -y build-essential autoconf automake libtool pkg-config git wget

RUN wget https://raw.githubusercontent.com/libbitcoin/libbitcoin-server/version3/install.sh && \
    chmod +x install.sh && \
    ./install.sh --prefix=/usr/local/ --build-boost --build-zmq --disable-shared

#FROM gcr.io/distroless/base-debian10
#FROM alpine
FROM ubuntu:20.10
COPY --from=build /usr/local/bin/bs /
CMD ["/bs"]

EXPOSE 8333
VOLUME [ "/blockchain" ]
