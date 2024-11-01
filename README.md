# Desktop Environment for GitHub Codespaces

This repository provides a desktop environment that can be run in GitHub Codespaces. It includes:

- A lightweight Fluxbox desktop environment
- Google Chrome browser
- VNC access via browser (noVNC) or VNC client

## Getting Started

1. Open this repository in GitHub Codespaces
2. Wait for the container to build and start
3. When ready, click the "Ports" tab and look for port 6080
4. Click the globe icon next to port 6080 to open the desktop in your browser
5. Click "Connect" and enter the password: `vscode`

## Features

- Browser-based desktop access via noVNC (port 6080)
- VNC client access available (port 5901)
- Google Chrome pre-installed
- Fluxbox window manager
- File manager and text editor included

## Using Chrome

You can start Chrome in two ways:
1. From the desktop interface:
   - Right-click anywhere on the desktop to open the Fluxbox menu
   - Select Chrome from the menu items

2. From the terminal:
   ```bash
   google-chrome --no-sandbox
   ```
   The `--no-sandbox` flag is required when running in a container environment.

## Customization

You can customize the desktop environment by:

1. Modifying the `.devcontainer/devcontainer.json` file
2. Adding additional software in the `.devcontainer/Dockerfile`
3. Customizing Fluxbox settings in `~/.fluxbox/`

## Troubleshooting

If applications crash, you may need to increase the shared memory size. Add this to devcontainer.json:

```json
"runArgs": ["--shm-size=1g"]
```

## Notes

- Default VNC password is: vscode
- Desktop resolution: 1440x768
- Ports are automatically forwarded in GitHub Codespaces