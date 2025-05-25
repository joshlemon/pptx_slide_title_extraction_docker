# Use the official slim Python image so pip works out-of-the-box
FROM python:3.10-slim

LABEL name="pptx-slide-title-extractor"
LABEL maintainer="Josh Lemon <josh@joshlemon.com.au>"

# Install python-pptx (and upgrade pip for good measure)
RUN pip install --upgrade pip setuptools wheel \
 && pip install --no-cache-dir python-pptx

# Copy your extraction script into the container
WORKDIR /app
COPY create_index.py .

# Make the script executable
RUN chmod +x create_index.py

# When the container runs, invoke your script directly
ENTRYPOINT ["python", "/app/create_index.py"]
