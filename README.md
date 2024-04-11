# Swarm Docker Images

[![BSD License](https://badgen.net/badge/license/BSD-3-Clause/blue)](LICENSE)
[![Build](https://github.com/swarm-io-internal/docker-images/actions/workflows/build.yml/badge.svg)](https://github.com/swarm-io-internal/docker-images/actions/workflows/build.yml)

Welcome to the Swarm Docker Image repository! This repository is dedicated to providing users with Docker images tailored for building GitHub Codespaces with the necessary infrastructure for internal research and building purposes. The images are built daily using GitHub Actions to ensure you have access to the latest updates and features.

## Repository Contents

### Docker Images

The repository contains a set of fundamental Docker images:

Image | Description | Version | Size
------|-------------|---------|------
data-science-full | This image provides significant infrastructure required for general purpose data science work. | [![version](https://ghcr-badge.egpl.dev/swarm-io-internal/data-science-full/latest_tag?trim=major&label=latest&color=steelblue)](https://github.com/swarm-io-internal/docker-images/pkgs/container/data-science-full) | [![size](https://ghcr-badge.egpl.dev/swarm-io-internal/data-science-full/size?color=steelblue)](#)
data-science-lite | This image is designed for exploratory research activities and includes basic tools and libraries. | [![version](https://ghcr-badge.egpl.dev/swarm-io-internal/data-science-lite/latest_tag?trim=major&label=latest&color=steelblue)](https://github.com/swarm-io-internal/docker-images/pkgs/container/data-science-lite) | [![size](https://ghcr-badge.egpl.dev/swarm-io-internal/data-science-lite/size?color=steelblue)](#)
data-science-nlp | This image is PyTorch optimized (with CUDA support) for NLP and LLM-based tasks. | [![version](https://ghcr-badge.egpl.dev/swarm-io-internal/data-science-nlp/latest_tag?trim=major&label=latest&color=steelblue)](https://github.com/swarm-io-internal/docker-images/pkgs/container/data-science-nlp) | [![size](https://ghcr-badge.egpl.dev/swarm-io-internal/data-science-nlp/size?color=steelblue)](#)

> Pro Tip: The conda default conda environment is `base` for all images. Use `conda deactivate` to exit the environment and `conda activate <env_name>` to enter an environment.

<!-- And additional set of project-specific Docker images can be found here:

Image | Description | Version | Size
------|-------------|---------|------

### GitHub Actions

The repository contains a set of GitHub Actions workflows:

Workflow | Description
---------|------------
build | This workflow is responsible for building the Docker images and pushing them to the GitHub Container Registry. -->

## Usage

### Pulling a Docker image

To use the Docker images, you can pull them from the GitHub Container Registry. For example, to pull the `data-science-full` image, you can run:

```bash
docker pull ghcr.io/swarm-io-internal/data-science-full:latest
```

### Running a Docker Container

Use the following command to run a Docker container:

```bash
docker run -it -p 8888:8888 ghcr.io/swarm-io-internal/data-science-full:latest
```

> Note: This command runs a CPU-only implementation of the Docker container, so you will NOT have access to any GPU resources. For GPU access within the container, you should update the command to `docker run --gpus all -it -p 8888:8888 ghcr.io/pytorch/pytorch-nightly:latest`.

### Docker images in Workflows

To use the images in your GitHub Actions workflows, you can reference the images directly in your workflow files. For example, to use the `data-science-full` image in your workflow, you can add the following step:

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    container:
      image: ghcr.io/swarm-io-internal/data-science-full:latest
```

## License

This repository is licensed under the [BSD 3-Clause License](LICENSE). Please review the [LICENSE](LICENSE) file for more details.

## Contributing

If you would like to contribute to this repository, please review the [CONTRIBUTING](CONTRIBUTING.md) guidelines.

## Code of Conduct

This repository follows the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md). Please review the [CODE_OF_CONDUCT](CODE_OF_CONDUCT.md) file for more details.

## Acknowledgements

This repository is maintained by the [Swarm team](https://www.jointhehive.io/). We would like to thank the open-source community for their contributions and support.
