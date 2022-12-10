# Run custom Dockerfile

`docker build -f <dockerfile name> .`

`-f`: specify the custom dockerfile name ex: _Dockerfile.dev_

# Use volumes

ex: `docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <image_id>`

- `-v /app/node_modules` (bookmarking): a placeholder for the folder inside the container, DO NOT try to map. No `:`
- `-v $(pwd):/app`: file&folder mapping. With `:`
- Using volumes allows container to reference files in our local machine and changes can be reflected automatically

# Multi-step Docker Builds

1. Build Phase: generate the build file
2. Run Phase: take build file generate from previous phase and start the nginx server
