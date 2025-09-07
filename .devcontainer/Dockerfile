# Use an official Python runtime as a base image
FROM mcr.microsoft.com/devcontainers/python:1-3.11

# Set environment variables
ENV PYTHONUNBUFFERED 1

# Install system dependencies
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    build-essential \
    libenchant-2-2 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
COPY requirements.txt /tmp/requirements.txt
RUN pip install --no-cache-dir -r /tmp/requirements.txt

# Download SpaCy model
RUN python -m spacy download en_core_web_sm

# Set the working directory
WORKDIR /workspace

# [Optional] If you plan to use additional tools like GitHub CLI or Azure CLI, uncomment the following:
# RUN curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
#     && chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
#     && echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
#     && apt-get update \
#     && apt-get install -y gh

# [Optional] If you need to install other tools, add them here.
