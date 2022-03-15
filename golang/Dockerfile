FROM golang:1.16 as builder
WORKDIR /app
ADD . .

# Disable CGO and compile server
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -ldflags '-w' -o server main.go

RUN chmod +x server

# Stage 1 - Server start
FROM alpine:latest
WORKDIR /app
COPY --from=builder /app /app

# Install tzdata and set docker image timezone to bangkok timezone
#RUN apk add --no-cache tzdata

# Expose service port
EXPOSE 8000

# Run server
CMD ["./server","start"]