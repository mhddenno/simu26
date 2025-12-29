## Building the Docker Image

```sh
docker build -t my-simu-notebook .
```

---

## Running Jupyter Lab (Interactive Mode)

```sh
docker run --rm -it \
  -p 8888:8888 \
  -v "$PWD":/usr/src/app \
  -w /usr/src/app \
  my-simu-notebook \
  jupyter lab --ip=0.0.0.0 --no-browser --allow-root
```

---

## Executing a Notebook in Batch Mode (Headless)

```sh
docker run -it --rm --name my-running-simu-notebook \
  -v "$PWD":/usr/src/app \
  -w /usr/src/app \
  my-simu-notebook \
  jupyter nbconvert --to notebook --execute src/script.ipynb --output executed.ipynb
```

> **Tip:** For a smoother development experience, consider using [VS Code Dev Containers](https://code.visualstudio.com/docs/devcontainers/containers).