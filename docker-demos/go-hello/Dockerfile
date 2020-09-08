FROM golang:1.14-alpine as builder
RUN apk --no-cache add git
WORKDIR /go/src/github.com/go/helloworld/
COPY hello.go .
RUN CGO_ENABLED=0 GOOS=linux go build -o hello .

FROM alpine:latest as prod
WORKDIR /root/
#--from  从其他层复制
COPY --from=builder  /go/src/github.com/go/helloworld/hello .
CMD ["./hello"]