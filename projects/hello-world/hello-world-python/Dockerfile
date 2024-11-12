# Base Image
# Use the official Python image based on Alpine Linux version 3.10 for a smaller image size
FROM python:alpine3.10

# Set the working directory inside the container to /app
WORKDIR /app

# Copy only requirements.txt to the container (useful if requirements don’t change often)
COPY requirements.txt /app/requirements.txt

# Install Python dependencies specified in requirements.txt
RUN pip install -r requirements.txt

# Expose port 5000 to allow external access to this port
EXPOSE 5000

# Copy all files from the current directory on the host to the /app directory in the container
COPY . /app

# Set the default command to run the Python application
CMD python ./launch.py

# Alternative lines (commented out):
# Copy only requirements.txt to the container (useful if requirements don’t change often)
# COPY requirements.txt /app/requirements.txt

# Use ENTRYPOINT to specify the executable and arguments (useful if CMD needs to be overridden)
# ENTRYPOINT ["python", "./launch.py"]
