# Use the official Python image from the Docker Hub
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the requirements file to the working directory
COPY requirements.txt ./

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code to the container
COPY . .

# Set environment variables for Redis connection
ENV REDIS_HOST=redis
ENV REDIS_PORT=6379

# Expose the application's port (e.g., 5000 for Flask)
EXPOSE 5000

# Command to run the application
CMD ["python", "manage.py", "runserver", "0.0.0.0:5000"]

