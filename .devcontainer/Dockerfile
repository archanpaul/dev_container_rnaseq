FROM mcr.microsoft.com/devcontainers/anaconda:1-3

COPY .devcontainer/environment.yml .devcontainer/noop.txt /tmp/conda-tmp/
RUN if [ -f "/tmp/conda-tmp/environment.yml" ]; then umask 0002 \
    && /opt/conda/bin/conda env update -f /tmp/conda-tmp/environment.yml; fi \
    && rm -rf /tmp/conda-tmp

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends fuse s3fs default-jre git git-lfs
