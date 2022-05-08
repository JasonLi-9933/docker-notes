- `docker run <image-name>`
- `docker ps`: list containers that are running
- `docker ps --all`: list all containers that you have ran
- `docker run` = `docker create <container-name>`(gives the id) + `docker start <container-id>`
- `docker start` doesn't give you the output `docker start -a`: show the output in the terminal
- command of a container cannot be overwritten once being created
- `docker system prune`: remove containers
- `docker logs <container-id>`
- To stop a container: `docker stop <container-id>` or `docker kill <container-id>`. `stop` command will take a couple of seconds while `kill` command will shut down containers immediately. After 10s of running `stop`, docker will fall back to `kill` and shut down the container`

## Execute an additional command in a container `docker exec -it <container-id> <command>`

- `-it`: allow us to provide input to the container
- `-it == -i -t`
  1. `-i`: the stuff you type get fed to the software you are trying to run
  2. `-t`: format the output on your screen nicely

## Getting a command prompt in a container

### `docker exec -it <container-id> sh`

- `sh` is just a command processor, just like `bash`, `powershell`, `zsh` etc
- Type `^D` or `exit` to exit

### `docker run -it <image> sh` (alternative)

- This command will run the default command
- Con: You are not able to run any other process

## Container Isolation

- Containers do not share file systems
