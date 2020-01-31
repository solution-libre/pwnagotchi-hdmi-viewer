# Pwnagotchi output via HDMI

#### Table of Contents

1. [Description](#description)
2. [Setup](#setup)
3. [Usage](#usage)
4. [Development](#development)
5. [Contributors](#contributors)

## Description

It's a Proof of Concept to display [Pwnagotchi](https://pwnagotchi.ai/) output via HDMI.

## Setup

```sh
cd /tmp
git clone https://github.com/solution-libre/pwnagotchi-hdmi-viewer.git
cd pwnagotchi-hdmi-viewer
mv pwnagotchi-launcher-pre pwnagotchi-viewer pwnagotchi-viewer-next /usr/local/sbin

```

## Usage

```diff
diff --git a/etc/pwnagotchi/config.yml b/etc/pwnagotchi/config.yml
index 30c696d..b556489 100644
--- a/etc/pwnagotchi/config.yml
+++ b/etc/pwnagotchi/config.yml
@@ -6,22 +6,3 @@
 #     type: 'inkyphat'
 #     color: 'black'
 #
+ui:
+  web:
+    on_frame: 'pwnagotchi-viewer-next'
```

```diff
diff --git a/etc/systemd/system/pwnagotchi.service b/etc/systemd/system/pwnagotchi.service
index 43231b6..84287c5 100644
--- a/etc/systemd/system/pwnagotchi.service
+++ b/etc/systemd/system/pwnagotchi.service
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

## Development

[Solution Libre](https://www.solution-libre.fr)'s repositories are open projects, and community contributions are essential for keeping them great.

[Fork this repo on GitHub](https://github.com/solution-libre/pwnagotchi-hdmi-viewer/fork)

## Contributors

The list of contributors can be found at: https://github.com/solution-libre/pwnagotchi-hdmi-viewer/graphs/contributors
