FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install Chrome
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && curl -sSL https://dl.google.com/linux/direct/google-chrome-stable_current_$(dpkg --print-architecture).deb -o /tmp/chrome.deb \
    && apt-get -y install /tmp/chrome.deb \
    && rm -rf /tmp/chrome.deb \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

# Set up non-root user (already done in base image, but shown for reference)
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID