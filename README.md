# Pwnagotchi output via HDMI

<!-- markdownlint-disable-next-line MD001 -->
#### Table of Contents

1. [Description](#description)
2. [Setup](#setup)
3. [Usage](#usage)
4. [Development](#development)
5. [Contributors](#contributors)

## Description

It's a Proof of Concept to display [Pwnagotchi](https://pwnagotchi.ai/) output via HDMI.

## Setup

1. Add the script files:

   ```sh
   cd /tmp
   git clone https://github.com/solution-libre/pwnagotchi-hdmi-viewer.git
   cd pwnagotchi-hdmi-viewer
   sudo mv pwnagotchi-launcher-pre pwnagotchi-viewer pwnagotchi-viewer-next /usr/local/sbin
   ```

2. Add a splashscreen (250x122px) in `/root/pwnagotchi-splashcreen.png`

3. Edit `/etc/pwnagotchi/config.toml` config file:

   ```diff
   @@ -2,3 +2,4 @@
    # Example:
    # ui.display.enabled = true
    # ui.display.type = "waveshare_2"
   +ui.web.on_frame = "pwnagotchi-viewer-next"
   ```

4. Edit `/etc/systemd/system/pwnagotchi.service` service file:

   ```diff
   @@ -7,9 +7,7 @@ After=pwngrid-peer.service
    [Service]
    Type=simple
    PermissionsStartOnly=true
   +ExecStartPre=/usr/local/sbin/pwnagotchi-launcher-pre
    ExecStart=/usr/bin/pwnagotchi-launcher
   +ExecStartPost=start-stop-daemon --start -b --exec /usr/local/sbin/pwnagotchi-viewer
    Restart=always
    RestartSec=30
    TasksMax=infinity
   ```

5. Reload systemctl

   ```sh
   sudo systemctl daemon-reload
   ```

6. Reboot

## Usage

Plug a previously turned on HDMI display into your Raspberry Pi before starting it up.

## Development

[Solution Libre](https://www.solution-libre.fr)'s repositories are open projects,
and community contributions are essential for keeping them great.

[Fork this repo on GitHub](https://github.com/solution-libre/pwnagotchi-hdmi-viewer/fork)

## Contributors

The list of contributors can be found at: <https://github.com/solution-libre/pwnagotchi-hdmi-viewer/graphs/contributors>
