FROM rancher/rke2-runtime:v1.18.9-rke2r1 AS source

FROM ubuntu:latest AS modifier
COPY --from=source /charts /charts
RUN rm /charts/rke2-canal.yaml

FROM scratch
COPY --from=modifier /charts /charts
COPY --from=source /bin /bin
ADD charts /charts-cni-plugins
COPY --from=source /charts/rke2-canal.yaml /charts-cni-plugins