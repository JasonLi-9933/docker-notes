# Use an existing docker image as a base
FROM alpine

# Download and instal a dependency
RUN apk add --update redis

# Tell the image what to do when it starts as a container
CMD ["redis-server"]


# run: docker build .