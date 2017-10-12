# GoJupyterDocker

A Dockerfile using the [Scipy Python Jupyter Docker](https://hub.docker.com/r/jupyter/scipy-notebook/) as base and adding a [Go kernel](https://github.com/gopherdata/gophernotes) and the IHaskel kernel.

## Usage
1. Build docker:
```bash
docker build -t gojupyter .
```

2. Run docker
```bash
sudo docker run -it --rm -p 8888:8888 gojupyter
```

3. Follow instructions in console to open Jupyter notebook
