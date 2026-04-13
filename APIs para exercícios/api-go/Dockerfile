FROM golang:1.23-alpine AS builder

WORKDIR /app

COPY go.mod ./
RUN go mod download

COPY . .
RUN go build -o api-go main.go

FROM alpine:latest
WORKDIR /app

COPY --from=builder /app/api-go .

EXPOSE 3000

CMD ["./api-go"]
