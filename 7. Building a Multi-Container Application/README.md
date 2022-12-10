# Dev Dockerfile workflow

1. Copy over `package.json`
2. run `npm install`
3. Copy over everything else
4. Docker compose should set up a volume to "share" files

# Environment Variables

- `variableName=value` sets a variable in the container at _run time_
- `variableName` sets a variable in the container at _run time_ and value is taken from _your computer_

# Deploy Multi Container App to AWS EB

1. Push code to Github
2. Travis automatically pulls repo
3. Travis builds a test image, then tests code
4. Travis builds prod image
5. Travis pushed built prod images to Docker Hub
6. Travis pushes project to AWS EB
7. EB pulls images from Docker Hub, then deploys
