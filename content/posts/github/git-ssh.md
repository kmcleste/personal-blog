---
author: Kyle McLester
categories:
- GitHub
date: 2022-02-15
format: hugo
summary: Secure git repo connection with SSH
title: GitHub SSH
toc-title: Table of contents
---

You may be accustomed to using your Git project url (https) for cloning
and pushing to your Git repo, however you can also use SSH. I'm not
going to go into which method is better, I'll just be showing you how
it's done.

## Creating SSH Key

1.  First, we must check if an SSH key already exists. You can do so by
    running:

``` bash
ssh-add -l
```

2.  If no key exists, run the following command:

``` bash
# substituting email for the email you use with GitHub
ssh-keygen -t rsa -b 4096 -C "kmcleste@uncc.edu"
```

3.  Press **enter** to accept the default file location
4.  Enter a **Secure Passphrase**
5.  Press **Enter** to complete key generation
6.  Display the contents of your **Public Key**

``` bash
# this is the path for my default installation, yours may be different
# refer to the path provided when creating your key
cat ~/home/kyle/.ssh/id_rsa.pub
```

7.  Copy the contents of your **Public Key**

## Add Key to GitHub

1.  Login to your [GitHub account](https://github.com)
2.  Click your avatar and choose **Settings**
3.  Select **SSH and GPG Keys** from the settings list
4.  Click **New SSH Key**
5.  Enter a descriptive title in the *title* field
6.  Paste your public key into the *Key* field
7.  Finish by clicking **Add SSH Key**

## SSH in Action

Now when you set your origin or clone/push/pull, you will use the ssh
link provided by GitHub; which will look something like this:

``` bash
git clone git@github.com:kmcleste/git-tutorial.git
```

Assuming you set a passphrase in the previous steps, you will be
prompted for this phrase everytime you try to clone/push/pull.
