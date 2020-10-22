ARG BUILD_FROM=hassioaddons/base-aarch64:8.0.4
FROM ${BUILD_FROM}

WORKDIR /app

RUN apk add --update --no-cache jq nodejs npm git && \
    npm install fs mqtt mailparser smtp-server
RUN git clone --depth=1 https://github.com/yaseregko/smtp2mqtt.git /app

COPY rootfs /

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="smtp2mqtt addon" \
    io.hass.description="smtp2mqtt add-on by Home Assistant Community Add-ons" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Sergey Rubtsov <ya.seregko@gmail.com>" \
    org.opencontainers.image.title="smtp2mqtt addon" \
    org.opencontainers.image.description="smtp2mqtt add-on by Home Assistant Community Add-ons" \
    org.opencontainers.image.vendor="Home Assistant Community Add-ons" \
    org.opencontainers.image.authors="Sergey Rubtsov <ya.seregko@gmail.com>" \
    org.opencontainers.image.licenses="MIT" \
    org.opencontainers.image.url="https://addons.community" \
    org.opencontainers.image.source="https://github.com/yaseregko/smtp2mqtt_addon" \
    org.opencontainers.image.documentation="https://github.com/yaseregko/smtp2mqtt_addon/blob/master/README.md" \
    org.opencontainers.image.created=${BUILD_DATE} \
    org.opencontainers.image.revision=${BUILD_REF} \
    org.opencontainers.image.version=${BUILD_VERSION}