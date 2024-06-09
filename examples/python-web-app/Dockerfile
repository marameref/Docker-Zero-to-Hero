FROM ubuntu

# Install Python and virtualenv
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv

# Set the working directory
WORKDIR /app

# Copy the requirements file and application files
COPY requirements.txt /app
COPY devops /app/devops

# Create a virtual environment and install dependencies
RUN python3 -m venv venv && \
    . venv/bin/activate && \
    pip install --upgrade pip && \
    pip install -r requirements.txt

# Set environment variables to use the virtual environment
ENV VIRTUAL_ENV=/app/venv
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Default command to run the application
ENTRYPOINT ["python3"]
CMD ["devops/manage.py", "runserver", "0.0.0.0:8000"]
