#Build Stage
FROM golang:1.18 AS builder
add . /src/
RUN cd /src/ && go build -o frontend

#Final Stage
FROM alpine
WORKDIR /app
COPY --from=builder /src/frontend /app/
RUN apk add libc6-compat

ENTRYPOINT ./frontend

CMD ["go", "run", "frontend"]