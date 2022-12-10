## Copying build files `COPY <path-from> <path-to>`

- `<path-from>`: path to folder to copy from on **your machine**, relative to build context
- `<path-to>`: path to copy stuff to inside **the container**

## Container port mapping `docker run -p <incoming-port>:<container-port> <image-name>`

## Specifying a Working Directory `WORKDIR <path>`

- Any following command will be executed relative to this `<path>` in the container
