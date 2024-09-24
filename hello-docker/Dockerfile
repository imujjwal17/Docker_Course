# Use an official Node.js runtime as the base image.
# 'node:20-alpine' is a lightweight version of Node.js 20 based on Alpine Linux, which is small and efficient.
FROM node:20-alpine

# Set the working directory inside the container to '/app'.
# All subsequent commands will be executed inside this directory.
WORKDIR /app

# Copy all files from the current directory on the host machine to the '/app' directory inside the container.
# The first dot (.) represents the current directory on your host, and the second dot (.) is the destination in the container.
COPY . .

# Specify the command to run when the container starts.
# Here, we're telling the container to execute 'node hello.js', which will run the hello.js file using Node.js.
CMD ["node", "hello.js"]
