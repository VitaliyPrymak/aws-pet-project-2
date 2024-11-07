FROM python:3.9-slim

RUN apt-get update && apt-get install -y libpq-dev gcc

WORKDIR /app

RUN pip install --upgrade pip

COPY requirements.txt ./

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code to the container
COPY . /app

# Set environment variables for Redis connection
ENV REDIS_HOST=redis
ENV REDIS_PORT=6379

# Expose the application's port (e.g., 5000 for Flask)
EXPOSE 3000

# Command to run the application
CMD ["python", "manage.py", "runserver", "0.0.0.0:3000"]
