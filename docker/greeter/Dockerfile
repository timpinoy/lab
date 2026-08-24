FROM ubuntu:24.04

WORKDIR /app
COPY greeter .
RUN chmod +x greeter

ENV GREETING=Hello
ENV NAME=World

CMD ["./greeter"]
