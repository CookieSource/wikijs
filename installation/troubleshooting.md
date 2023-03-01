---
title: Troubleshooting
description: Solutions to common problems during installation
published: true
date: 2023-03-01T12:50:42.141Z
tags: troubleshooting
editor: markdown
dateCreated: 2023-02-18T16:58:19.423Z
---

\# Common Issues Here you can find a list of issues that can arise during installation ## No network connectivity during install (while connected to the internet) \*\*Problem:\*\* The installer cannot find you’re connected to the internet. \*\*Solution\*\* \`\`\`plaintext sudo sed -i 's/1.1.1.1/1.0.0.127/g' /usr/share/cnchi/src/misc/extra.py \`\`\` ## Installer won't start Make sure you're connected to the internet and then open a terminal and type this command. \`\`\`plaintext bash refresh-keys.sh \`\`\` ## Undefined installation failures Please run the installer from the terminal with this command. \`\`\`plaintext sudo cnchi-installer \`\`\`