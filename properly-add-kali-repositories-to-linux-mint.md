---
title: "Properly install Kali Apps in Linux Mint, Ubuntu and Debian Based Distributions!"
date: 2022-08-21
# weight: 1
# aliases: ["/first"]
tags: ["Kali linux","Repository","add","install","metasploit","nikto","nmap","nethunter"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "A guide to properly add Kali Linux Repositories to install Kali Apps without facing any breaking changes"
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/<path_to_repo>/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

## Kali: The Phenomenon
---

![](https://c.tenor.com/73bhaYAl0moAAAAC/yes-oh.gif)

Since the launch in 2013, Kali Linux has been heartily welcomed by both Security Analyst and Script Kiddies.

With the access to a vast number of tool sets and layers of securities, it has been a favorite choice in the field of Penetration Testing, Security Research, Computer Forensics and Reverse Engineering. Not to mention we've also seen Elliot using Kali Linux in multiple **Mr Robot** Episodes.

Then comes the script-kiddies. Well, I don't usually like to use this term because "Everyone starts somewhere". If some scripts gets you interested in Cyber Security, Welcome aboard!

**Note:** Though it should work across all Debian based distributions, But I've only this on Linux Mint.

## What the Duck are we doing?
---
![](https://c.tenor.com/wRKppcFJEe8AAAAC/ducks.gif)
- Prevent auto updates from Kali repositories to prevent breaking everything
- Enable us to install any Kali apps right in our own Linux!
- Enjoy a taste of Penetration Testing without any exhausting installation process.

## Getting the system ready
---

Before we begin, We need to update our usual repositories and upgrade our system so that we don't run into conflicts for obsolete packages.

To achieve that, we need to run this simple command:

```BASH
sudo apt update && sudo apt full-upgrade -y
```

Which will update and upgrade all the available packages. After that, reboot the system and run:

```BASH
sudo apt update
```

Which should output something similar to this:

```
```
