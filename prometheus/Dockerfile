FROM --platform=linux/arm64 prom/prometheus:v2.37.0 as build-stage

FROM --platform=linux/arm64 alpine:3.16.1

RUN apk add gettext

COPY --from=build-stage /bin/prometheus /bin/prometheus

RUN mkdir -p /prometheus /etc/prometheus \
  && chown -R nobody:nogroup etc/prometheus /prometheus

# COPY ./template/prometheus.yml.template /template/prometheus.yml.template

USER nobody

VOLUME [ "/prometheus" ]

WORKDIR /prometheus
