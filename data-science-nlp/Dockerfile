# Use the latest version of the pangeo/base-image
ARG PANGEO_BASE_IMAGE_TAG=master
FROM pangeo/base-image:${PANGEO_BASE_IMAGE_TAG}

# Set the user to root
USER root

# Copy the environment and requirements files into the Docker image
COPY environment.yml /tmp/environment.yml
COPY requirements.txt /tmp/requirements.txt
COPY postBuild.sh /tmp/postBuild.sh

# Create a new Conda environment from the environment.yml file
RUN conda env create -f /tmp/environment.yml

# Install wget, git, ncdu, and curl
RUN apt-get update && apt-get install -y \
    wget \
    git \
    ncdu \
    curl \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*