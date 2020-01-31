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
diff --git a/config.yml b/config.yml-new
index 30c696d..b556489 100644
--- a/config.yml
+++ b/config.yml-new
@@ -6,22 +6,3 @@
 #     type: 'inkyphat'
 #     color: 'black'
 #
+ui:
+  web:
+    on_frame: 'pwnagotchi-viewer-next'
```

## Development

[Solution Libre](https://www.solution-libre.fr)'s repositories are open projects, and community contributions are essential for keeping them great.

[Fork this repo on GitHub](https://github.com/solution-libre/pwnagotchi-hdmi-viewer/fork)

## Contributors

The list of contributors can be found at: https://github.com/solution-libre/pwnagotchi-hdmi-viewer/graphs/contributors
