# Use the official Nginx image from the Docker Hub
FROM nginx:alpine

# Set the working directory in the container
WORKDIR /usr/share/nginx/html

# Copy the static files from your project to the container
COPY . .

# Expose port 80 for the Nginx server
EXPOSE 80

# No CMD is required as Nginx will run by default
