# hash:sha256:a493fb4514c62abcb267e0accb9345e15788bc8f8e3aff921fe0f6932309727f
FROM registry.codeocean.allenneuraldynamics.org/codeocean/jupyterlab:3.6.1-miniconda4.12.0-python3.9-ubuntu20.04

ARG DEBIAN_FRONTEND=noninteractive

ARG GIT_ASKPASS
ARG GIT_ACCESS_TOKEN
COPY git-askpass /

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        build-essential=12.8ubuntu1.1 \
    && rm -rf /var/lib/apt/lists/*

RUN conda install -y \
        matplotlib==3.7.1 \
        numpy==1.24.3 \
        pip==23.2.1 \
        seaborn==0.12.2 \
    && conda clean -ya

RUN pip install -U --no-cache-dir \
    caveclient==5.7.0 \
    datajoint==0.12.9 \
    torch==1.9.0

COPY postInstall /
RUN /postInstall
