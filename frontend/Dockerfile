FROM nginx:alpine

# Set the working directory in the container
WORKDIR /usr/share/nginx/html

# Copy index.html and config.json
COPY ./templates/index.html config.json ./

RUN chmod 644 index.html config.json

COPY nginx.conf /etc/nginx/conf.d/default.conf

CMD ["nginx", "-g", "daemon off;"]
