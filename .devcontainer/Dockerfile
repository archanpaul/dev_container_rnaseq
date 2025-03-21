# FROM mcr.microsoft.com/devcontainers/anaconda:1-3
FROM mcr.microsoft.com/devcontainers/miniconda

COPY .devcontainer/environment.yml .devcontainer/noop.txt /tmp/conda-tmp/

SHELL ["/bin/bash","-l", "-c"]

WORKDIR /root/

RUN /opt/conda/bin/conda init bash && \
    /opt/conda/bin/conda config --add channels default && \
    /opt/conda/bin/conda config --add channels bioconda && \
    /opt/conda/bin/conda config --add channels conda-forge && \
    /opt/conda/bin/conda update --all -y -n base && \
    /opt/conda/bin/conda env update -f /tmp/conda-tmp/environment.yml && \
    /opt/conda/bin/conda update --all -y -n venv && \
    /opt/conda/bin/conda clean -afy

RUN rm -rf /tmp/conda-tmp

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends fuse s3fs default-jre git git-lfs

ENV PATH /opt/conda/bin:$PATH

RUN echo "conda activate venv" >> ~/.bashrc
ENTRYPOINT ["bash", "-l", "-c"]
