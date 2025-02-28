---
title: Setup
---
### Website accounts to create
Please seek help at the start of the lesson if you have not been able to establish a website account on:
- The [Docker Hub](http://hub.docker.com). We will use the Docker Hub to download pre-built container images, and for you to upload and download container images that you create, as explained in the relevant lesson episodes.

### Files to download

Download the [`docker-intro.zip`]({{ page.root }}/files/docker-intro.zip) file. _This file can alternatively be downloaded from the `files` directory in the [docker-introduction GitHub repository][docker-introduction repository]_.

Move the downloaded file to your Desktop and unzip it. It should unzip to a folder called `docker-intro`. 

### Software to install
Docker's installation experience has steadily improved, however situations will arise in which installing Docker on your computer may not be straightforward unless you have a large amount of technical experience.
Workshops try to have helpers on hand that have worked their way through the install process, but do be prepared for some troubleshooting.

In most cases, you will need to have administrator rights on the computer in order to install the Docker software. If you are using a computer managed by your organisation and do not have administrator rights, you *may* be able to get your organisation's IT staff to install Docker for you. Alternatively your IT support staff *may* be able to give you remote access to a server that can run Docker commands.

Please try to install the appropriate software from the list below depending on the operating system that your computer is running. Do let the workshop organisers know as early as possible if you are unable to install Docker using these instructions, as there may be other options available.

#### Microsoft Windows

**You must have admin rights to run Docker!** Some parts of the lesson will work without running as admin but if you are unable to `Run as administrator` on your machine some elements of this workshop might not work as described.

Ideally, you will be able to install the Docker Desktop software, following the [Docker website's documentation](https://docs.docker.com/docker-for-windows/install/). Note that the instructions for installing Docker Desktop on Windows 10 Home Edition are different from other versions of Windows 10.

Note that the above installation instructions highlight a minimum version or "build" that is required to be able to install Docker on your Windows 10 system. See [Which version of Windows operating system am I running?](https://support.microsoft.com/en-us/windows/which-version-of-windows-operating-system-am-i-running-628bec99-476a-2c13-5296-9dd081cdd808) for details of how to find out which version/build of Windows 10 you have.

If you are unable to follow the above instructions to install Docker Desktop on your Windows system, the final release of the deprecated Docker Toolbox version of Docker for Windows can be downloaded from the [releases page of the Docker Toolbox GitHub repository](https://github.com/docker/toolbox/releases). (Download the `.exe` file for the Windows installer). _Please note that this final release of Docker Toolbox includes an old version of Docker and you are strongly advised not to attempt to use this for any production use. It will, however, enable you to follow along with the lesson material._

> ## Warning: Git Bash
> If you are using Git Bash as your terminal on Windows then you should be aware that you may run
> into issues running some of the commands in this lesson as Git Bash will automatically re-write
> any paths you specify at the command line into Windows versions of the paths and this will confuse
> the Docker container you are trying to use. For example, if you enter the command:
> ```
> docker run alpine cat /etc/os-release
> ```
> Git Bash will change the `/etc/os-release` path to `C:\etc\os-release\` before passing the command
> to the Docker container and the container will report an error. If you want to use Git Bash then you
> can request that this path translation does not take place by adding an extra `/` to the start of the
> path. i.e. the command would become:
> ```
> docker run alpine cat //etc/os-release
> ```
> This should suppress the path translation functionality in Git Bash.
{: .callout}

#### Apple macOS

Ideally, you will be able to install the Docker Desktop software, following the
[Docker website's documentation](https://docs.docker.com/docker-for-mac/install/).
The current version of the Docker Desktop software requires macOS version 10.14 (Mojave) or later.

If you already use Homebrew or MacPorts to manage your software, and would prefer to use those
tools rather than Docker's installer, you can do so. For Homebrew, you can run the command
`brew install --cask docker`. Note that you still need to run the Docker graphical user interface
once to complete the initial setup, after which time the command line functionality of Docker will
become available. The Homebrew install of Docker also requires a minimum macOS version of 10.14.
The MacPorts Docker port should support older, as well as the most recent, operating system
versions (see the [port details](https://ports.macports.org/port/docker/details/)), but note that
we have not recently tested the Docker installation process via MacPorts.

#### Linux

There are too many varieties of Linux to give precise instructions here, but hopefully you can locate documentation for getting Docker installed on your Linux distribution. It may already be installed. If it is not already installed on your system, the [Install Docker Engine](https://docs.docker.com/engine/install/) page provides an overview of supported Linux distributions and pointers to relevant installation information. Alternatively, see:

 - [Docker Engine on CentOS](https://docs.docker.com/install/linux/docker-ce/centos/)
 - [Docker Engine on Debian](https://docs.docker.com/install/linux/docker-ce/debian/)
 - [Docker Engine on Fedora](https://docs.docker.com/install/linux/docker-ce/fedora/)
 - [Docker Engine on Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

### Verify Installation

To quickly check if the Docker and client and server are working run the following command in a new terminal or ssh session:
~~~
$ docker version
~~~
{: .language-bash}
~~~
Client:
 Version:           20.10.2
 API version:       1.41
 Go version:        go1.13.8
 Git commit:        20.10.2-0ubuntu2
 Built:             Tue Mar  2 05:52:27 2021
 OS/Arch:           linux/arm64
 Context:           default
 Experimental:      true

Server:
 Engine:
  Version:          20.10.2
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.13.8
  Git commit:       20.10.2-0ubuntu2
  Built:            Tue Mar  2 05:45:16 2021
  OS/Arch:          linux/arm64
  Experimental:     false
 containerd:
  Version:          1.4.4-0ubuntu1
  GitCommit:        
 runc:
  Version:          1.0.0~rc95-0ubuntu1~21.04.1
  GitCommit:        
 docker-init:
  Version:          0.19.0
  GitCommit:        
~~~
{: .output}

The above output shows a successful installation and will vary based on your system.  The important part is that the "Client" and the "Server" parts are both working and returns information.  It is beyond the scope of this document to debug installation problems but common errors include the user not belonging to the `docker` group and forgetting to start a new terminal or ssh session.

### A quick tutorial on copy/pasting file contents from episodes of the lesson
Let's say you want to copy text off the lesson website and paste it into a file named `myfile` in the current working directory of a shell window. This can be achieved in many ways, depending on your computer's operating system, but routes I have found work for me:
- macOS and Linux: you are likely to have the `nano` editor installed, which provides you with a very straightforward way to create such a file, just run `nano myfile`, then paste text into the shell window, and press <kbd>control</kbd>+<kbd>x</kbd> to exit: you will be prompted whether you want to save changes to the file, and you can type <kbd>y</kbd> to say "yes".
- Microsoft Windows running `cmd.exe` shells:
  - `del myfile` to remove `myfile` if it already existed;
  - `copy con myfile` to mean what's typed in your shell window is copied into `myfile`;
  - paste the text you want within `myfile` into the shell window;
  - type <kbd>control</kbd>+<kbd>z</kbd> and then press <kbd>enter</kbd> to finish copying content into `myfile` and return to your shell;
  - you can run the command `type myfile` to check the content of that file, as a double-check.
- Microsoft Windows running PowerShell:
  - The `cmd.exe` method probably works, but another is to paste your file contents into a so-called "here-string" between `@'` and `'@` as in this example that follows (the ">" is the prompt indicator):

        > @'
        Some hypothetical
        file content that is

        split over many

        lines.
        '@ | Set-Content myfile -encoding ascii

### SSH client

All attendees should have an SSH client installed.
SSH is a tool that allows us to connect to and use a remote computer, within a terminal window, as our own.
Please follow the directions below to install an SSH client for your system.

**Windows**

Modern versions of Windows have SSH available in Powershell. You can test if it is available by typing `ssh --help` in Powershell. If it is
installed, you should see some useful output. If it is not installed, you will get an error. If SSH is not available in Powershell, then
you should install MobaXterm as described below.

An alternative is to install MobaXterm from [http://mobaxterm.mobatek.net](http://mobaxterm.mobatek.net). You will want to get the Home edition (Installer edition). However, if Git Bash works, you do not need this.

**macOS**

macOS comes with SSH pre-installed, so you should not need to install anything.

**Linux**

Linux users do not need to install anything, you should be set!

## 4. Account on ARCHER2

Please sign up for your account on our HPC machine, [ARCHER2](https://www.archer2.ac.uk/), which will be available to
you for the duration of the course and for a few days afterwards, to allow you to
complete the practical exercises and put some of what you have learned into practice.

### Sign up for a SAFE account

To sign up, you must first register for an account on [SAFE](https://safe.epcc.ed.ac.uk/) (our service administration web application):

If you are already registered on the ARCHER or Tier-2 SAFE you do not need to re-register. Please proceed to the next step.

1. Go to the [SAFE New User Signup Form](https://safe.epcc.ed.ac.uk/signup.jsp)
2. Fill in your personal details. You can come back later and change them if you wish. _**Note:** you should register using your institutional or company email address - email domains such as gmail.com, outlook.com, etc. are not allowed to be used for access to ARCHER2_
3. Click “Submit”
4. You are now registered. A single use login link will be emailed to the email address you provided. You can use this link to login and set your password.

### Sign up for an account on ARCHER2 through SAFE

In addition to your password, you will need an SSH key pair to access ARCHER2. There is useful guidance on how
to generate SSH key pairs in [the ARCHER2 documentation](https://docs.archer2.ac.uk/user-guide/connecting/#ssh-key-pairs).
It is useful to have your SSH key pair generated before you request an account on ARCHER2 as you can add it when 
you request the account

1. [Login to SAFE](https://safe.epcc.ed.ac.uk)
2. Go to the Menu "Login accounts" and select "Request login account"
3. Choose the `ta049` project “Choose Project for Machine Account” box and click "Next"
4.  Select the *ARCHER2* machine in the list of available machines
5.  Click *Next*
6.  Enter a username for the account and an SSH public
    key
    1.  If you do not specify an SSH key at this stage, your default
        key will be used (if you have one). For users who had an ARCHER
        account, the default key will be your ARCHER SSH key.
    2.  You can always add an SSH key (or additional SSH keys) using
        the process described below.
7.  Click *Request*

Now you have to wait for the course organiser to accept your request to register. When this has happened, your account will be created on ARCHER2.
Once this has been done, you should be sent an email. _If you have not received an email but believe that your account should have been activated, check your account status in SAFE which will also show when the account has been activated._ You can then pick up your one shot initial password for ARCHER2 from your SAFE account.

### Log into ARCHER2

You should now be able to log into ARCHER2 by following the [login instructions in the ARCHER2 documentation](https://docs.archer2.ac.uk/user-guide/connecting/#ssh-clients).

## (Optional) Install Singularity on your local system

The Singularity part of this course will be undertaken on ARCHER2. If you do not wish to use ARCHER2 to run your Singularity images, you will need to install Singularity on your local system. _These instructions are optional and are not required to complete the course._

If you are running Linux and would like to install Singularity locally on your system, Singularity provide the free, open source [Singularity Community Edition](https://sylabs.io/singularity/). 

You will need to install various dependencies on your system and may then need to build Singularity from source code. Packages for some Linux distributions are made available for each release, see the [Singularity releases](https://github.com/sylabs/singularity/releases) on GitHub. If you have Linux systems knowledge and would like to attempt a local install of Singularity, you can find full details of the installation process in the [INSTALL.md](https://github.com/sylabs/singularity/blob/master/INSTALL.md) file within the Singularity repository. This file explains how to install the prerequisites and build and install the software. Singularity is written in the [Go](https://golang.org/) programming language and Go is the main dependency that you'll need to install on your system. The process of installing Go and any other requirements is detailed in the INSTALL.md file.

If you do not have access to a Linux system where you can build and install Singularity but you have administrative privileges on another system, you could look at installing a virtualisation tool such as [VirtualBox](https://www.virtualbox.org/) on which you could run a Linux Virtual Machine (VM) image. Within the Linux VM image, you will be able to install Singularity. Again this is beyond the scope of the course.

{% include links.md %}

{% comment %}
<!--  LocalWords:  myfile kbd links.md md endcomment
-->
{% endcomment %}
