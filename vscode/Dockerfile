ARG BASE_IMAGE=ubuntu:24.04
FROM $BASE_IMAGE
ARG VSCODIUM_VERSION=1.95.2.24313
ARG SESSION_USER=vscode
ARG WORKDIR=/workspace
ARG MOUNTDIR=/workspace/work
SHELL [ "/bin/bash", "-c", "-o", "pipefail" ]
RUN apt-get update && \
	apt-get install -y --no-install-recommends ca-certificates curl tini build-essential git git-lfs && \
	mkdir -p /codium-server && \
	curl -L https://github.com/VSCodium/vscodium/releases/download/${VSCODIUM_VERSION}/vscodium-reh-web-linux-x64-${VSCODIUM_VERSION}.tar.gz | tar -xz -C /codium-server && \
	rm -rf /var/lib/apt/lists/*
RUN useradd -m -s /bin/bash ${SESSION_USER}
ENV LANG=C.UTF-8
ENV LC_ALL=C.UTF-8

USER ${SESSION_USER}
WORKDIR ${WORKDIR}
# We are setting this to a weird double underscore name to avoid collisions with user-set vars
RUN mkdir -p ${MOUNTDIR}
