FROM debian:jessie

RUN apt-get update && export TERM=xterm && \
    apt-get install -y curl \
    && rm -rf /var/lib/apt/lists/*

# This should download the latest stable version of kubectl
# It's not great from a provenance pov, but it's basically the same as the
# official instructions
RUN curl -o /usr/local/bin/kubectl -sSL https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
RUN chmod +x /usr/local/bin/kubectl

COPY copy.sh /
RUN chmod +x /copy.sh

ENTRYPOINT /copy.sh
