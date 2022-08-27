---
title: "Properly install Kali Apps in Linux Mint, Ubuntu, and Debian Based Distributions!"
date: 2022-08-21
# weight: 1
# aliases: ["/first"]
tags: ["Kali Linux","Repository","add","install","Metasploit","nikto","nmap","nethunter"]
categories: ["Guide","Cyber Security"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "A guide to properly add Kali Linux Repositories to install Kali Apps without facing any breaking changes"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "https://i.imgur.com/oukdiPq.png" # image path/url
    alt: "Eniamza cheering with Kali Linux and Linux distributions" # alt text
    caption: "Eniamza cheering with Kali Linux and Linux distributions" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/<path_to_repo>/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link


## Kali: The Phenomenon
---

![](https://c.tenor.com/73bhaYAl0moAAAAC/yes-oh.gif)

Since its launch in 2013, Kali Linux has been heartily welcomed by both Security Analyst and Script Kiddies.

With the access to a vast number of toolsets and layers of securities, it has been a favorite choice in the field of Penetration Testing, Security Research, Computer Forensics and Reverse Engineering. Not to mention we've also seen Elliot using Kali Linux in multiple **Mr Robot** Episodes.

Then comes the script-kiddies. Well, I don't usually like to use this term because "Everyone starts somewhere". If some scripts get you interested in Cyber Security, Welcome aboard!

**Note:** Though it should work across all Debian-based distributions, I've only this on Linux Mint.

## What the Duck are we doing?
---
![](https://c.tenor.com/wRKppcFJEe8AAAAC/ducks.gif)
- Prevent auto updates from Kali repositories to prevent breaking everything
- Enable us to install any Kali apps right in our own Linux!
- Enjoy a taste of Penetration Testing without any exhausting installation process.

## Getting the system ready
---

Before we begin, We need to update our usual repositories and upgrade our system so that we don't run into conflicts with obsolete packages.

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

Which should return an error with a signature verification error

```bash
Get:5 https://mirrors.ocf.berkeley.edu/kali kali-rolling InRelease [30.5 kB]

Err:5 https://mirrors.ocf.berkeley.edu/kali kali-rolling InRelease

The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6

Reading package lists... Done

W: GPG error: https://mirrors.ocf.berkeley.edu/kali kali-rolling InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6

E: The repository 'https://http.kali.org/kali kali-rolling InRelease' is not signed.

N: Updating from such a repository can't be done securely and is therefore disabled by default.

N: See apt-secure(8) manpage for repository creation and user configuration details.
```

To fix that, we need to add the public key to this repo. We need a package called *GnuPG* for the purpose. Install it using:

```Bash
sudo apt install gnupg
```

And a few more commands:

```bash
wget 'https://archive.kali.org/archive-key.asc'
sudo apt-key add archive-key.asc
```

We need to update the cache again, But **DO NOT UPGRADE THE SYSTEM YET, OR ELSE YOUR PC MIGHT NOT BOOT ANYMORE!**

Carefully, Run the **update** command to update the repo cache:

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

The magic command is:

```bash
sudo sh -c "echo 'Package: *'>/etc/apt/preferences.d/kali.pref; echo 'Pin: release a=kali-rolling'>>/etc/apt/preferences.d/kali.pref; echo 'Pin-Priority: 50'>>/etc/apt/preferences.d/kali.pref"
```

Now, if we update our cache again with `sudo apt update`, we'll see that all of our packages are up-to-date. *Phew!*

## Having fun with the added power!
---

![Thanos saying I have the power](https://c.tenor.com/l1fTQixBIMoAAAAd/avengers-thanos.gif)

We have the repositories set up and Infinite new possibilities in our hands. But we still have some follow-up process left!

If we again try to get Nikto with `sudo apt install Nikto`, it will install, but it may not properly install the dependencies. Let's say APT just isn't powerful enough!

To get around this, we're going to install a more convenient deb manager called *Aptitude* :

```bash
sudo apt install aptitude
```

See the irony? We're using APT to replace itself.

Now, we're all set. Let's get our buddy *Nikto!*

```Bash
sudo aptitude install nikto
```

Which will output with the good news we all have been waiting for!

```bash
	Preparing to unpack .../nikto_1%3a2.1.6+git20190310-0kali3_all.deb ...                                                 Unpacking nikto (1:2.1.6+git20190310-0kali3) ...                                                                       Setting up nikto (1:2.1.6+git20190310-0kali3) ... 
```


And again to calm our souls, let's poke our new friend with `nikto -h` :

![Nikto help dialogue](https://i.imgur.com/NYldq50.png)

Cheers!

## Things to Remember

---

Though we have added more power on our side, We *must* remember some points before we proceed any further

- You MUST NOT use Nikto or any other pen-testing tools on any platform or individual users without prior permission of the owner!
- Kali Linux comes with added security layers that might not be found in our personal Linux by default
- Always backup your system before doing something this drastic. A good tool would be the [TimeShift.](https://github.com/teejee2008/timeshift)

See you soon in another alternative reality, Sayonara, my peeps!