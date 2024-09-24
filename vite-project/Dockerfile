# Set the base image to Node.js 20 running on Alpine Linux, which is a small and efficient distribution
FROM node:20-alpine

# Create a system user 'app' with no password, and add it to the 'app' group to avoid running the app as root.
# Running applications as a non-root user is a security best practice, as it limits the damage a potential vulnerability can cause.
RUN addgroup app && adduser -S -G app app

# Set the current user to 'app' so the following operations are executed by this non-root user.
USER app

# Set the working directory to '/app' inside the container, where all commands will be executed from now on.
WORKDIR /app

# Copy the package.json and package-lock.json files to the container.
# This is done before copying the rest of the files to take advantage of Docker's caching.
# Docker will cache the dependencies installation step, speeding up the build if these files haven’t changed.
COPY package*.json ./

# Sometimes files in the working directory may be owned by root, which can cause permission errors during app runtime.
# We'll temporarily switch to root to fix the ownership of the files.
USER root

# Change the ownership of the entire /app directory to the 'app' user and group, ensuring that the non-root user has access to all files.
RUN chown -R app:app .

# Switch back to the non-root 'app' user to continue building and running the app in a secure environment.
USER app

# Install the necessary dependencies for the React app.
RUN npm install

# Copy the rest of the application source files to the working directory inside the container.
COPY . .

# Expose port 5173, which is commonly used for running development servers with React (Vite in this case).
EXPOSE 5173

# Command to start the development server for the React app.
# 'npm run dev' typically starts the development server, such as Vite, on port 5173.
CMD ["npm", "run", "dev"]


#docker ps   // opens up all the running container 
#docker ps -a // all the container
# stop is used to stop the running container ( by using id or name (id - starting three digits))
#prune will remove all the deactive container 
# rm is used to remove a particular container
# docker run -p 5173:5173 -v "$(pwd):/app" react-docker