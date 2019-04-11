---
layout: post
title: Requirements
tagline: A few more words about this theme
permalink: /build/requirements.html
---
# Requirements
Before you download and build the LeaseOS source, ensure your system meets the following
requirements.
## Hardware requirements
---
The hardware requirements to build LeaseOS are roughly the same as
building the Android release 7.1.2. Your development workstation should meet or exceed these hardware requirements:
* A 64-bit environment is required.
* At least 250GB of free disk space to checkout the code and an extra 150GB to build it.
If you conduct multiple builds, you will need even more space.
* If you are running Linux in a virtual machine, you need at least 16GB of RAM/swap.

## Software requirements
---
The [LeaseOS](https://github.com/OrderLab/leaseos_local_manifests) master branch is developed and tested on
Ubuntu 16.04 (LTS) releases, building under Windows or Mac OS is not currently supported. But Other distributions may be used.

Your workstation must have the software listed below:
```
$ sudo apt-get install git-core gnupg flex bison gperf build-essential zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev libgl1-mesa-dev libxml2-utils xsltproc unzip
```

