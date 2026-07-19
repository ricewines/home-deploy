FROM swr.cn-north-4.myhuaweicloud.com/ddn-k8s/docker.io/library/debian:bookworm-slim

RUN sed -i 's|deb.debian.org|mirrors.ustc.edu.cn|g' /etc/apt/sources.list.d/debian.sources && \
    apt-get update && apt-get install -y --no-install-recommends ca-certificates && rm -rf /var/lib/apt/lists/*

COPY frp_0.69.1_linux_amd64.tar.gz /tmp/frp.tar.gz
RUN mkdir -p /frp && \
    tar -xzf /tmp/frp.tar.gz -C /tmp && \
    cp /tmp/frp_0.69.1_linux_amd64/frpc /frp/frpc && \
    chmod +x /frp/frpc && \
    rm -rf /tmp/frp*

WORKDIR /frp

ENV FRPC_WEB_SERVER_PASSWORD=${FRPC_WEB_SERVER_PASSWORD}

EXPOSE 7400 5244 7080 3389

ENTRYPOINT ["/frp/frpc", "-c", "/frp/frpc.toml"]
