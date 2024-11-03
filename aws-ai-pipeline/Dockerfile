# Base image with CUDA and cuDNN
FROM nvidia/cuda:11.8.0-cudnn8-runtime-ubuntu20.04

# Set environment variables
ENV DEBIAN_FRONTEND=noninteractive
ENV LANG=C.UTF-8
ENV LC_ALL=C.UTF-8

# Install essential packages and dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    python3.8 \
    python3-pip \
    python3-venv \
    wget \
    curl \
    git \
    build-essential \
    libssl-dev \
    libffi-dev \
    && rm -rf /var/lib/apt/lists/*

# Install Python 3.8 as default
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.8 1

# Upgrade pip
RUN pip install --upgrade pip

# Install NVIDIA PyIndex for accessing NVIDIA's optimized packages
RUN pip install nvidia-pyindex

# Install PyTorch with GPU support
RUN pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu118

# Install TensorFlow with GPU support
RUN pip install tensorflow==2.11.0 tensorflow-gpu==2.11.0

# Install additional ML libraries as required
RUN pip install \
    scikit-learn \
    scipy \
    pandas \
    numpy \
    matplotlib \
    seaborn \
    jupyterlab \
    ipywidgets \
    einops

# Set up JupyterLab for remote access (if needed)
RUN jupyter notebook --generate-config && \
    echo "c.NotebookApp.ip = '0.0.0.0'" >> ~/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.open_browser = False" >> ~/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.port = 8888" >> ~/.jupyter/jupyter_notebook_config.py

# Install Hugging Face Transformers (for models like Molmo)
RUN pip install transformers

# Set default working directory
WORKDIR /workspace

# Expose Jupyter Notebook port
EXPOSE 8888

# Set entrypoint (optional)
CMD ["jupyter", "notebook", "--allow-root"]
