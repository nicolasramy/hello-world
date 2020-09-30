FROM rust:alpine
MAINTAINER Nicolas Ramy <devops@darkelda.com>

WORKDIR /usr/src/myapp
COPY . .

RUN rustup default nightly
RUN cargo run

CMD ["cargo", "run"]
