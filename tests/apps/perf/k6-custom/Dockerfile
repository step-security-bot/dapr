# Build the k6 binary with the extension
FROM golang:1.20@sha256:23050c2510e0a920d66b48afdc40043bcfe2e25d044a2d7b33475632d83ab6c7 as builder

RUN go install go.k6.io/xk6/cmd/xk6@latest
RUN xk6 build --output /k6 --with github.com/grafana/xk6-output-prometheus-remote@v0.1.0 --with github.com/grafana/xk6-disruptor@350f53204c65040e71757f98a330665a8f189f91

# Use the operator's base image and override the k6 binary
FROM loadimpact/k6:latest@sha256:11f8f63625b20177719f4ac5682ffc28564da7adac47fd90838a7e024836406c
COPY --from=builder /k6 /usr/bin/k6
