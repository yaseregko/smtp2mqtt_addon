ARG BUILD_FROM=hassioaddons/base:8.0.3
FROM ${BUILD_FROM}

WORKDIR /app

ENV PYTHONUNBUFFERED=1
RUN apk add --update --no-cache python3 && ln -sf python3 /usr/bin/python
RUN python3 -m ensurepip
RUN pip3 install --no-cache --upgrade pip setuptools

RUN git clone https://github.com/gonzalezcalleja/smtp2mqtt.git

COPY smtp2mqtt/smtp2mqtt.py /app

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

EXPOSE 1125

RUN python /app/smtp2mqtt.py \
          --mqtttopic "doorbell/entrada" \
          --mqtthost 127.0.0.1 --mqttport 1883 \
          --mqttusername mqtt --mqttpassword mosquitto \
          --smtphost 127.0.0.1 --smtpport 1125 \
          --smtpusername doorbell@domain.local --smtppassword secret