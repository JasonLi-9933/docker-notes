# Docker Compose

- config file named `docker-compose.yml`
- Containers(services) created by `docker-compose` are in the same network, so they have free access to each other
- `docker-compose` will look for the `docker-compose.yml` file in the current directory

| Docker                                  | Docker Compose              |
| --------------------------------------- | --------------------------- |
| `docker run <image>`                    | `docker-compose up`         |
| `docker build .` + `docker run <image>` | `docker-compose up --build` |
| `docker ps`                             | `docker-compose ps`\*       |

\*: have to run this command in the same directory as `docker-compose.yml`

- `docker-compose up -d`: launch in background
- `docker-compose down`: stop containers

## Automatic Container Restarts

- restart policies:
  1. `"no"`(must include quotes)
     : Never attempt to restart this `.` container if it stops or crashes
  2. `always`
     : If this container stops _for any reason_, always attempt to restart it
  3. `on-failure`
     : Only restart of the container stops with an error code
  4. `unless-stopped`
     : Always restart unless we forcibly stop it
