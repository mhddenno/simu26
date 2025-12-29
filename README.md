# Build image
docker build -t my-simu-notbook .

# Insdie a browser (Interactive loop)
docker run --rm -it \
  -p 8888:8888 \
  -v "$PWD":/usr/src/app \
  -w /usr/src/app \
  my-simu-notbook \
  jupyter lab --ip=0.0.0.0 --no-browser --allow-root

# Run the notebook insdie the Container (headless using nbconvert means batch execution with every tweak you have to re-run the container)
docker run -it --rm --name my-running-simu-notbook \
  -v "$PWD":/usr/src/app \
  -w /usr/src/app \
  my-simu-notbook \
  jupyter nbconvert --to notebook --execute src/script.ipynb --output executed.ipynb

# VC Code dev Containers could be the better solution here