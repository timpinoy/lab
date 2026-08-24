# Stage 1: Generate HTL
FROM ubuntu:24.04 AS builder


WORKDIR /build
COPY generate-status .
RUN chmod +x generate-status && ./generate-status > index.html


# Stage 2: Serve with nginx
FROM nginxinc/nginx-unprivileged:1.28


COPY --from=builder /build/index.html /usr/share/nginx/html/index.html


EXPOSE 8080
