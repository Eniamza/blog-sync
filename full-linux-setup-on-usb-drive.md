---
title: "Create a Portable Linux with USB Flash Drive [Windows]"
date: 2022-08-19
# weight: 1
# aliases: ["/first"]
tags: ["persistent","live","Bootable","Windows","Rufus","Live Linux","Linux Mint","Dual Boot","How To"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Don't want to go wild and dual boot? Or want your workspace to fit in your pocket? Live Persistence Linux is just the right choice for you!"
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
    image: "https://i.imgur.com/6q0dbZy.png" # image path/url
    alt: "Eniamza Carrying a briefcase with Linux logo on it" # alt text
    caption: "Create portable Linux in windows with one of the easiest methods!" # display caption undercover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on a current single page
editPost:
    URL: "https://github.com/<path_to_repo>/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

## Ahoy!

---

![Dustin Handerson Saying Hi](https://c.tenor.com/UexY6570HekAAAAC/stranger-things.gif)

There might be a few reasons you’re reading this.

You're a frustrated windows user and thinking to change your taste to Unix-like systems, infamous as Linux without blowing up your PC (*In most cases it doesn’t*)

You're a tech support guy with nerdy glasses (*or not*) and want to have a plug-n-play environment to be ready anywhere and anytime.

Or you're just lying on the bed like me wondering about the universe, figuring out mysteries and this concept just crossed your mind

Despite the reasons above (*and a thousand others*), A persistent Live USB is considerably the best option. Yeah, I wouldn't recommend you RAM-hungry Virtual Machines. [Or that's kept for other scenarios in another episode!]

## Things to Grab
---

- [Rufus for Windows](https://rufus.ie/en/) 

- An USB Flash Drive at least 8GB or Higher [Duh?]
- [Linux Mint ISO](https://www.linuxmint.com/download.php) [I'll be using the Cinnamon Version]
- And Common Sense [Believe me you need this most]

## Burning with Rufus
---

Rufus is like our go-to Bootable Media creator on Windows. In most tutorials, Bootable Media = Rufus. For its ease, we are going to use it too!
Let's dive in!

- **Run it** 

It's as simple as double-clicking on the icon. So please click the icon. Do it. Yes, I repeat, Do it!

- **Configuring Rufus**

After starting Rufus, it'll bring up the user interface which we will use to create our portable Linux environment. In the Picture below, I have summarized my selection and Configuration for the Bootable Media Creation Process!

![Rufus starting interface](https://i.imgur.com/l2qHkYm.png)


**Configurations:**

Device: Your USB Flash Drive. 

**NOTE: SELECT CAREFULLY BECAUSE ALL THE DATA WILL BE WIPED!!**

Boot Selection: Select the ISO File We downloaded. In this case, it's *Linux-21-cinnamon-64bit.iso*

Partition Scheme: MBR
Target System: BIOS or UEFI
Volume Label: Anything you want. Even "Doughnut" is good.
File System: FAT32
Cluster Size: 4096 bytes [Default]

- **Select the Persistent Storage Size**

![Persistent Storage Slider on Rufus](https://i.imgur.com/FGghx9T.png)

Here, you can select how much persistent storage you want on your flash drive. For an 8GB Stick, 1 or 2 GB is better. for a 256GB stick, just crank it up; don't worry!

- **Hit the START**

Hitting the start button will start the process of creating your Pocket Linux! However, before it starts, it may ask you to download syslinux if Rufus doesn't find a suitable version.

![Requesting Syslinux download dialogue](https://i.imgur.com/dzWFvPV.png)

It's Required for the process, so hit "Yes" and move on!

- **Cross Check Wiping Warning**

Remember the process will destroy all data from the device we are using. Be sure to back up your data first!


**And Voila!**, You've successfully created a Persistent Live Linux which will store your progress and work data as needed!



