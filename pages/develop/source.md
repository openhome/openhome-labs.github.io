---
layout: content-no-sidebar
title: Getting Started
header : Getting started with OpenHome
weight: 20
parent: develop
---
{% include JB/setup %}

# Get the source

OpenHome is an OpenSource platform hosted on GitHub at the [openhome](https://github.com/openhome) project page.

The platform is built from a number of repositories covering build tools, networking, audio pipeline and Player applications. These repositories are described in the table below.

| Component | Features | Repository | 
|---------------|---------------|---------------|
| Dev tools    | Build configuration tools    | [ohdevtools](https://github.com/openhome/ohdevtools)    |
| ohNet    | A modern cross-platform UPnP networking stack    | [ohNet](https://github.com/openhome/ohNet)    |
| ohPipeline    | The OpenHome Audio Pipeline    | [ohPipeline](https://github.com/openhome/ohPipeline)    |
| ohPlayer    | OpenHome Players for PC, Mac, Linux and Raspberry Pi    | [ohPlayer](https://github.com/openhome/ohPlayer)    |


## Repository and source setup
---------------------------
Before building, clone ohdevtools (https://github.com/openhome/ohdevtools.git) into the same parent directory as ohPlayer.

```[zak]: git clone https://github.com/openhome/ohdevtools.git
[zak]: git clone https://github.com/openhome/ohPlayer.git
```

### Using Pre-built Components

OpenHome can fetch pre-built dependencies for ohNet and ohPipeline from the OpenHome build server.

To fetch dependencies, run

```[zak]: go fetch --all```

or

```[zak]: go fetch --all --debug```

depending on your build requirements.
App dependencies will be downloaded to the ohPlayer/dependencies directory.


## Configuring your build environment

### Windows

On __Windows__, ensure that you have the following tools installed:

- Microsoft Visual Studio 2013
- InnoSetup  (<http://www.jrsoftware.org/isinfo.php>)
- git
- perl

### OSX (Mac)

On __OSX__, ensure that you have the following tools installed:

- XCode 7.x or higher
- git
- perl

### Linux (Ubuntu 12.x and Raspbian (wheezy))

On __Ubuntu__ and __Raspbian__ the toolchain setup is rather more complex than other platforms.

install compiler dependencies

```sudo apt-get update
sudo apt-get install gcc-4.8 g++-4.8 ```

set up gcc alternates; we need gcc4.8

```sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.6 20
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.8 50
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.6 20
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.8 50```

install audio and UI dependencies

```sudo apt-get install gtk+-3-dev libnotify-dev notify-osd libasound2-dev```

install package maker

```sudo apt-get install ruby-dev
sudo gem install fpm```


## Building the application

### Windows

Open the ohPlayer solution in Visual Studio 2013 and build release or debug variants

```ohPlayer/Win32/OpenHomePlayer.sln```

The solution will build a windows tray application.

The installer generation process employs the Inno Setup 5 tool - <http://www.jrsoftware.org/isinfo.php>
The actual download was 'isetup-5.5.5.exe'.

All defaults were chosen during application installation including the installation of the optional pre-processor extensions..
To create the installer, compile the installer script, OpenHomePlayerInstaller.iss, as follows:

```iscc /dMySrcDir="C:\<src folder>" OpenHomePlayerInstaller.iss```

Where <src folder> identifies the parent folder of the installer (Win32Installer) and application source (Win32) folders.

'setup.exe' will be generated in the Win32Installer folder.

### OSX

Open the Player Xcode project and build release or debug variants.

```ohPlayer/osx/openhomeplayer.xcodeproj```
   
The project will build a system menu aplication.


### Linux

make the project
```cd ohPlayer/linux```

```make ubuntu     // release build```

or

```make raspbian   // release build```

or

```DEBUG=1 make ubuntu   // debug build```

or

```DEBUG=1 make raspbian // debug build```

or

```make ubuntu-install     // build and install locally```

or

```make raspbian-install   // build and install locally```


generate a debian package for distribution

```./GeneratePkg.pl --platform=raspbian --application=openhomeplayer --version=0.1.2.3```

generate an installer package

```./GeneratePkg.pl --platform=raspbian --application=openhomeplayer --version=0.1.2.3 --installer```

Cross-compilation is not yet supported. OpenHome Players must be built on the target platform at present.
The project will build a GTK menubar application.
