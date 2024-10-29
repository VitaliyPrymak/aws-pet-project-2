# Use an official Nginx runtime
FROM nginx:alpine

# Set the working directory in the container
WORKDIR /usr/share/nginx/html

# Copy index.html and config.json
COPY ./templates/index.html config.json ./

# Set file permissions
RUN chmod 644 index.html config.json

# Copy default Nginx configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
