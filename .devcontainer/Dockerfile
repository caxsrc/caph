# .devcontainer/Dockerfile

# Use the official Miniconda3 image
FROM continuumio/miniconda3:latest

# Update and install any necessary system packages
RUN apt-get update && apt-get install -y \
    git \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Copy the requirements.txt from the root of the project to /tmp
COPY ../requirements.txt /tmp/requirements.txt

# Create a default environment named "caph" with Python 3.9
RUN conda create --name caph python=3.9 -y

# Install data science libraries and any additional dependencies from requirements.txt
RUN conda run --name caph pip install -r /tmp/requirements.txt

# Ensure "caph" is activated by default in new shells
RUN echo "conda activate caph" >> ~/.bashrc

# Update PATH to point to the "caph" environment
ENV PATH /opt/conda/envs/caph/bin:$PATH