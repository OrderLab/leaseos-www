---
layout: post
title: Downloading
tagline: A few more words about this theme
permalink: /downloading.html
---
# Download the Source Tree
The LeaseOS source tree is located in a Git repository hosted by OrderLab.
This document describes how to download the source tree for a specific device.
## Install `repo` client
---
`repo` is a tool that makes it easier to work with Git in the context of Android.
For more information about `repo`, see the [Repo Command Reference](https://source.android.com/setup/develop/repo.html).

To install Repo:

1. Make sure you have a bin/ directory in your home directory and that it is included in your path:
```
$ mkdir ~/bin
$ PATH=~/bin:$PATH
```
2. Download the Repo tool and ensure that it is executable:
```
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

## Initialize source code repository
---
After installing `repo`, create the working directory and configure your git. 

1. Create an empty directory to hold your working files.  Give it any name you like:
```
$ mkdir WORKING_DIRECTORY
$ cd WORKING_DIRECTORY
```
2. Configure git with your real name and email address. To use the Gerrit code-review tool,
you will need an email address that is connected with a [registered Google account](https://myaccount.google.com/). Make sure
this is a live address at which you can receive messages.
```
$ git config --global user.name "Your Name"
$ git config --global user.email "you@example.com"
```
3. Sync the [AOSP source tree](https://source.android.com/setup/build/downloading) with the branch
that matches the Lease OS release version. Currently, that is `android-7.1.2_r2`
```
$ repo init -u https://android.googlesource.com/platform/manifest -b android-7.1.2_r2
```

## Clone LeaseOS custom manifests
1. LeaseOS use a local manifests directory to override the repos in AOSP source tree to customized repos. 
Assuming you are in the `WORKING_DIRECTORY`,
```
$ cd .repo
$ git clone https://github.com/OrderLab/leaseos_local_manifests.git local_manifests
$ cd ..
$ repo sync
```

2. When initially checked out, all the repositories are in a detached state. In order to work on our custom repositories,
we need to set the branch to the remote branch. Type the following command to do it for all:
```
$ repo forall -g leaseos -c 'git checkout --track public/leaseos-7.1.2_r2'
```
After the sync finishes, you can use the repo tool to apply a command to all the repositories defined in this local manifest
by specifying the group leaseos (which is defined in the `leaseos.xml`). For example, to get the status:
```
$ repo forall -g leaseos -c 'git status'
```
### Additional Note
> The device repos are proprietary and copyrighted by the vendors. Therefore they are excluded from the manifest file in our public branch.
You will need to clone these device-specific repos into the source tree. For example, for Google Pixel XL phone, you need to find the device
drivers for google_marlin and proprietary blobs extracted from the factory image. You will also need to find the Google Apps Suite to be
included in the custom image (this can also be installed separately later).
