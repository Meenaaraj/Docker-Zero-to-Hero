# Use the official Python 3 image as the base
FROM python:3.11-slim

# Set the working directory to /app
WORKDIR /app

# Copy the requirements file and the application code
COPY requirements.txt /app/
COPY devops /app/

# Install required system packages and python dependencies inside a virtual environment
RUN apt-get update && \
    apt-get install -y --no-install-recommends build-essential && \
    python3 -m venv /venv && \
    /venv/bin/pip install --no-cache-dir -r requirements.txt

# Set the environment to use the virtual environment
ENV PATH="/venv/bin:$PATH"

# Set the working directory to the 'devops' folder (if it contains your Django project)
WORKDIR /devops

# Expose the port on which Django will run
EXPOSE 8000

# Start the Django application
ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]
