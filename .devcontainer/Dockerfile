FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install Chrome
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && curl -sSL https://dl.google.com/linux/direct/google-chrome-stable_current_$(dpkg --print-architecture).deb -o /tmp/chrome.deb \
    && apt-get -y install /tmp/chrome.deb \
    && rm -rf /tmp/chrome.deb \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

# Ensure sudo is available
RUN apt-get update \
    && apt-get install -y sudo \
    && echo "vscode ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/vscode \
    && chmod 0440 /etc/sudoers.d/vscode

# Set the default user
USER vscode