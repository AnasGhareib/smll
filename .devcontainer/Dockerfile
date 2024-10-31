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

# Create Fluxbox menu with Chrome
RUN mkdir -p /home/vscode/.fluxbox && echo '[begin] (  Application Menu  )' > /home/vscode/.fluxbox/menu \
    && echo '   [exec] (Chrome Browser) { google-chrome --no-sandbox } <>'\
    && echo '   [exec] (File Manager) { nautilus ~ } <>'\
    && echo '   [exec] (Terminal) { tilix -w ~ -e $(readlink -f /proc/$$/exe) -il } <>'\
    && echo '   [submenu] (System) {}'\
    && echo '      [exec] (Edit Menu) { mousepad ~/.fluxbox/menu } <>'\
    && echo '      [exec] (Top Processes) { tilix -t "Top" -e htop } <>'\
    && echo '   [end]'\
    && echo '   [config] (Configuration)'\
    && echo '   [workspaces] (Workspaces)'\
    && echo '[end]' >> /home/vscode/.fluxbox/menu \
    && chown -R vscode:vscode /home/vscode/.fluxbox

# Set the default user
USER vscode