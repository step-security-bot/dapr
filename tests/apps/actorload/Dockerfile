FROM golang:1.20@sha256:23050c2510e0a920d66b48afdc40043bcfe2e25d044a2d7b33475632d83ab6c7
WORKDIR /actorload/
COPY . .
RUN make build

FROM alpine:latest@sha256:124c7d2707904eea7431fffe91522a01e5a861a624ee31d03372cc1d138a3126
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=0 /actorload/dist/ .
CMD ["./stateactor"]
