---
title: "How Dictionary based Bruteforce Attacks can be more optimized with CUPP"
date: 2022-08-14
# weight: 1
# aliases: ["/first"]
tags: ["dictionary","10 million","cupp","python","custom password list","hacking","password crack", "effective wordlist"]
author: "Eniamza"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "CUPP is an unique password profiling technique where you can generate a dictionary word list curated for your target!"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "https://i.imgur.com/qrNNNRU.png" # image path/url
    alt: "Eniamza holding a magnifying glass thinking with processing icons over his head and looking at a man portraid as a target." # alt text
    caption: "Common user Password Profiler to generate effective short and custom wordlist or Dictionary for brute-force Attacks" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/<path_to_repo>/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---




## What is a Dictionary Attack?

---

In most of the Sci-Fi movies, generally, we see a hacker wearing a black hoodie typing constantly on the keyboard. While these movies don't exactly portray a proper hacking culture, they also make it seem unbelievably easy to exploit an individual user.

![Hacker Typing](https://c.tenor.com/VrzXhtoSwcsAAAAd/hacker-typing.gif)

But we have to understand that not all website is easily exploitable. Tech Giants such as Google and Facebook implant high-level security and constantly patch new vulnerabilities. So which part is the most vulnerable? You're right it's the user itself!

Once upon a time, users chose passwords such as "Honey123", "Love321", "I'mdumb111", etc. These passwords could be easily brute-forced and cracked using a Dictionary attack where the script tries the passwords from a provided Dictionary. *Imagine Trying Several Keys at the same time from the collection of keys in the world*

CUPP takes this attack one step ahead.

## CUPP, not Mug or Jug?

---

I know it'd be fun to call it Jug. But CUPP stands for **Common User Password Profiler** 

Also, sounds fun, right? 
In this technique, We input a little information about our target. For example, a person named Danny Morgan wouldn't use the word "Scott" as his password. Unless he has a favorite actor named "Scott".

CUPP v3 goes through different combinations and algorithms based on the given data to create a wordlist for the target as effectively as possible.

## Let's get the party started!
---

Before jumping into the steps, make sure you have these applications pre-installed:


+ [Git](https://git-scm.com/downloads)
+ [Python3](https://www.python.org/downloads/) (v3 Recommended!)

Now that we have set up our environment to run CUPP,  let's

- **Clone the Official CUPP Repository**

```
git clone https://github.com/Mebus/cupp.git
```

- **Change your directory**

```
cd ./cupp
```

- **Check if everything is working**

```
python3 cupp.py -h
```

This should result in this output

```
usage: cupp.py [-h] [-i | -w FILENAME | -l | -a | -v] [-q]  

Common User Passwords Profiler         

optional arguments:                                                                                                       -h, --help show this help message and exit                                                                      -i, --interactive  Interactive questions for user password profiling                                                    -w FILENAME  Use this option to improve existing dictionary, or WyD.pl output to make some pwn sauce 
-l Download huge wordlists from repository                                                              -a Parse default usernames and passwords directly from Alecto DB. Project Alecto uses purified databases of Phenoelit and CIRT which were merged and enhanced 
-v, --version      Show the version of this program.                                                                    -q, --quiet        Quiet mode (don't print banner)
```

This means our script is ready to blast!

## The Actual Business

---

![Serious Business GIF](https://c.tenor.com/qMwX1HeagaoAAAAC/serious-business.gif)

Now we're going to generate the actual list! Yeah, yeah, I know there are a few more options available, but to keep it simple we'll stick to the classic Interactive Question-based Walkthrough. And don't worry, I'll add a short explanation for all of them later in this article. 

To initiate the process first run:

```
python3 cupp.py -i
```

Here *-i* stands for interactive. You can also use *-interactive* (if you love typing)

This will bring our first question in front:

```
[+] Insert the information about the victim to make a dictionary                                                        [+] If you don't know all the info, just hit enter when asked! ;)                                                                                                                                                                               > First Name:
```

So as our target's name was "Danny Morgan", let's put "Danny" here and hit enter!

Then it asks for the Surname:

```
> Surname:
```

Which is "Morgan"
And for the Nickname, Let's Put Dan. Yeah, his Mom calls him Dan.

We attended know his birthdate because he's our friendly neighbor which is: 02011990.

Unfortunately, he's still single so he doesn't have a partner. So for the next 3 questions, we'll just keep those empty and press enter to move forward!

As he's single, obviously he doesn't have any children too! The next 3 questions also go empty!

But he has a loving dog named "Kevin". So for the next question, We put *Kevin* as our answer!
We know he works at Mcdonald's. I know, it is what it is.

Here comes an important part. Our target might have some more related keywords we may want to add. Such as the street he lives in, her grandma's name whom he all day yaps about or simply his favorite color black. Not to forget his favorite movie *Terminator*

Now CUPP will ask you if you want to add special characters and numbers [For Ex. @,!, # and 1,2,3,4] at the end of each word. Most modern sites encourage a user to use them, so it's better to have them! We will Enter "Y"  for both and move forward.

The script also can combine its output with the **Leet Mode**. Where a number is used instead of a look-alike character. For example: E=3, S=5, l=1, T = 8, etc.

Danny isn't that much geeky so let's skip on this one! Enter N to continue.

At last, Hyperspeed print means CUPP will print the generated dictionary on the console, It's fun to look through. But for now, we'll just skip through.

Finally! Our intelligent little script will say something like this:

```
Now load your pistolero with ←[1;31mdanny.txt←[1;m and shoot! Good luck!
```

This means, our customized dictionary is finally done!

We should see a "danny.txt" in the same directory with 13612 words ready to be tested!

![Screenshot of the generated text document](https://i.imgur.com/Yt3S3iz.png)

It tries to generate the common combinations a human might use. Just wonder what accuracy you can achieve with an existing pwned database, some OSINT research on the target and this!

## Other Options

---

Now that we wrapped up our basic interactive option, let's briefly explore what other things we can do with CUPP.

- **help > -h**

This option generates a help message with a list of arguments we can use with this script

- **interactive Steps > -i / -interactive**

The one we just used. Scroll up to jog your memories!

- **Optimize existing Dictionary > -w FILENAME**

If you have an existing dictionary in hand and want to add some custom spices. This is suitable and WyD.pl AKA Who's Your Daddy Password Profiler is a tool similar to CUPP but it scraps Strings from the files of a website and generates a custom password list!

- **Download Huge Dictionaries > -l**

You can download existing dictionaries of common words [Contains 10 Millions or more words!]

- **Default Passwords > -a**

Parse default usernames and passwords directly from Alecto DB. Project Alecto uses purified databases of Phenoelit and CIRT which were merged and enhanced  

- **Version Number > -v / --version**

Just prints the version number, nothing special

- **Quiet Mode > -q / --quiet**

That Doesn't prints the intro Banner of CUPP.

## Wrapping Up!
---

![The End is near GIF](https://c.tenor.com/uN1Y3Fxd6L8AAAAC/the-end-is-near-homer-simpson.gif)


You surely don't want to fall victim to this kind of customized brute-force attack. So always be cautious to use unique and long passwords which are of course easy to remember. (Password resets on every login wouldn't make you happy, trust me!)

Also, enable 2 Factor Authentication where possible so hackers can't gain access to your online accounts without the secret code on your phone!

In further Episodes of Dictionary Attacks, we'll cover other Profiler scripts such as CRUNCH and WyD.pl (we just heard here).

Till then, Sayonara my peeps!