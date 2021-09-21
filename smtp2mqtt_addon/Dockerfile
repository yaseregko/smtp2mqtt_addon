ARG BUILD_FROM=hassioaddons/base-aarch64:8.0.4
FROM ${BUILD_FROM}

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

WORKDIR /app

RUN apk add --update --no-cache jq nodejs npm git

RUN git clone --depth=1 https://github.com/yaseregko/smtp2mqtt.git /app && \
    npm install fs mqtt mailparser smtp-server

COPY rootfs /

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="Doorbell Yoosee SD-05" \
    io.hass.description="This addon simulate an SMTP server (required by Yoosee/KONX doorbell) and public a message in MQTT everytime the doorbell rings." \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Sergey Rubtsov <ya.seregko@gmail.com>" \
    org.opencontainers.image.title="smtp2mqtt addon for doorbell" \
    org.opencontainers.image.description="This addon simulate an SMTP server (required by Yoosee/KONX doorbell) and public a message in MQTT everytime the doorbell rings." \
    org.opencontainers.image.vendor="Home Assistant Community Add-ons" \
    org.opencontainers.image.authors="Sergey Rubtsov <ya.seregko@gmail.com>" \
    org.opencontainers.image.licenses="MIT" \
    org.opencontainers.image.url="https://addons.community" \
    org.opencontainers.image.source="https://github.com/yaseregko/smtp2mqtt_addon" \
    org.opencontainers.image.documentation="https://github.com/yaseregko/smtp2mqtt_addon/blob/master/README.md" \
    org.opencontainers.image.created=${BUILD_DATE} \
    org.opencontainers.image.revision=${BUILD_REF} \
    org.opencontainers.image.version=${BUILD_VERSION}
