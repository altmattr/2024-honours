ARG BASE_IMAGE="ubuntu"
ARG TAG="22.04"
FROM ${BASE_IMAGE}:${TAG}

RUN apt-get update && apt-get install --no-install-recommends -y \
    git \
    opam \
    pip \
    libgmp-dev

# RUN pip install ultralytics opencv-python