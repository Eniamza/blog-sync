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

```Bash
Reading package lists... Done

Building dependency tree  

Reading state information... Done

All packages are up to date.
```

Now, we are all set!

Just to give your soul some peace, try installing a famous web vulnerability scanner:

```BASH
sudo apt install wpscan
```

Which will return an error saying the package wasn't found:

```Bash
Reading package lists... Done 

Building dependency tree Reading state information... Done

E: Unable to locate package wpscan
```

Don't worry, this whole article is about fixing this!

## Adding the Kali Rolling Repository

---

![](https://c.tenor.com/lBp_H83I7AEAAAAC/morpheus-matrix-fight.gif)

We are going to install our Kali Linux Tools from this Repository:

`https://http.kali.org/kali kali-rolling main non-free contrib`

Let's add that to our sources list!

```Bash
sudo sh -c "echo 'deb https://http.kali.org/kali kali-rolling main non-free contrib' > /etc/apt/sources.list.d/kali.list"
```

This will create a new file called *kali.list* and add our desired repository.

Next, We need to update our repository cache!

```Bash
sudo apt update
```

Which should return an error with an signature verification error

```bash
Get:5 https://mirrors.ocf.berkeley.edu/kali kali-rolling InRelease [30.5 kB]

Err:5 https://mirrors.ocf.berkeley.edu/kali kali-rolling InRelease

The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6

Reading package lists... Done

W: GPG error: https://mirrors.ocf.berkeley.edu/kali kali-rolling InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6

E: The repository 'https://http.kali.org/kali kali-rolling InRelease' is not signed.

N: Updating from such a repository can't be done securely, and is therefore disabled by default.

N: See apt-secure(8) manpage for repository creation and user configuration details.
```

To fix that, we need to add the public key of this repo. We need a package called *GnuPG* for the purpose. Install it using:

```Bash
sudo apt install gnupg
```

And a few more commands:

```bash
wget 'https://archive.kali.org/archive-key.asc'
sudo apt-key add archive-key.asc
```

We need to update the cache again, But **DO NOT UPGRADE THE SYSTEM YET, OR ELSE YOUR PC MIGHT NOT BOOT ANYMORE!**

Carefully, Run **update** command to update the repo cache:

```bash
sudo apt update
```

Which should present more than a thousand packages ready to be upgraded!

```bash
1731 packages can be upgraded. Run 'apt list --upgradable' to see them
```

Again, **REFRAIN FROM DOING SO!** And let's quickly jump into implanting our safety net before we do anything stupid (In which I'm good at)

## Adding a safety net to prevent breaking upgrades!

---
![](https://c.tenor.com/w_wba2G4ipUAAAAC/stay-safe-safety.gif)

We're going to set the Kali Linux repository we added as a low priority so that we don't accidentally upgrade from the repository and face loads of package conflicts!

