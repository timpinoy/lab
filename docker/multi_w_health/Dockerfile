# Stage 1: Generate static HTML
FROM ubuntu:24.04 AS builder


WORKDIR /build
COPY generate-status .
RUN chmod +x generate-status && ./generate-status > index.html


# Stage 2: nginx (unpriviledged)
FROM nginxinc/nginx-unprivileged:1.28


# Labels
# LABEL org.opencontainers.image.source="https://github.com/user/repo"
# LABEL org.opencontainers.image.version="1.0.0"


# Copy generated HTML
COPY --from=builder /build/index.html /usr/share/nginx/html/index.html


EXPOSE 8080


# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
	CMD curl -f http://localhost:8080/ || exit 1
