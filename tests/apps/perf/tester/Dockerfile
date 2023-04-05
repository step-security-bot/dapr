FROM golang:1.20@sha256:23050c2510e0a920d66b48afdc40043bcfe2e25d044a2d7b33475632d83ab6c7 as build_env

ENV CGO_ENABLED=0
WORKDIR /app
COPY app.go go.mod ./
RUN go get -d -v && go build -o tester .

FROM golang:1.20@sha256:23050c2510e0a920d66b48afdc40043bcfe2e25d044a2d7b33475632d83ab6c7 as fortio_build_env

WORKDIR /fortio
ADD "https://api.github.com/repos/dapr/fortio/branches/v1.38.4-dapr" skipcache
RUN git clone https://github.com/dapr/fortio.git
RUN cd fortio && git checkout v1.38.4-dapr && go build

FROM debian:buster-slim@sha256:03c296b3f24c02f5e476dbdd6dc4b31a15cbc3b20c6906da02f239055167a802
WORKDIR /
COPY --from=build_env /app/tester /
COPY --from=fortio_build_env /fortio/fortio/fortio /usr/local/bin
CMD ["/tester"]
