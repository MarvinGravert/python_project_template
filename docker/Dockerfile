ARG  BASE_IMAGE=python:3.10.6
FROM ${BASE_IMAGE} as base
ENV PYTHONUNBUFFERED 1

RUN /bin/sh -c set -euxo pipefail; \
    apt-get update  ;\
    apt-get install --no-install-recommends -y\
    curl \
    ; \
    apt-get clean ;\
    rm -rf /var/lib/apt/lists/* ;\
    :

FROM base as prod
ARG BUILD_DATE
LABEL org.opencontainers.image.authors="Marvin Gravert"
WORKDIR /app
COPY main.py /src ./
CMD ["python", "main.py"]