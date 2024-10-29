# Use the official Python image from the Docker Hub
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the requirements file to the working directory
COPY requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code to the container
COPY . .

# Set environment variables for RDS connection
# Replace these with your actual RDS connection details
ENV DB_HOST=db
ENV DB_PORT=5432
ENV DB_USER=myuser
ENV DB_PASSWORD=mypassword
ENV DB_NAME=mydatabase

# Expose the application's port (e.g., 5000 for Flask)
EXPOSE 5000

# Command to run the application
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]

