## Dockerfile -> DockerClient -> DockerServer -> Usable Image

- Dockerfile: config file to define how our container should behave

## Creating a Dockerfile

1. Specify a base image (`FROM` instruction)

2. Run some command to install additional programs (`RUN` instruction)

- Looks back to the previous step and create a intermediate container based on that
- Run the command we provided to install the programs we needed, then the file system is modified
- Take a snap shot of the file system of the intermediate container
- Remove the intermediate container

3. Specify a command to run on container startup (`CMD` instruction)

- Again create a intermediate container based on the previous step
- Set the primary command to be the command we provided
- Take a snap shot of the file system and remove the intermediate container
- create the final image

## `docker build .`

- give Dockerfile to docker-cli
- `.`: build context

## Tagging your container `docker build -t <tag-name> .`

- Tag Name Convention: `<docker-id>/<project-name>:<version>` (ex: jasonli/redis:latest)
- If no version specified after `:`, `latest` is appended by default
