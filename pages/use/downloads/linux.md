---
layout: content-no-sidebar
title: Ubuntu
header : Get the OpenHome Player for Ubuntu now!
weight: 10
parent: use
---
{% include JB/setup %}

> Download OpenHome Player for Ubuntu

**OpenHome Player for Ubuntu** is an inobtrusive media streamer which sits in your system menu allowing you to stream high quality digital audio from your network servers and internet streaming services to your Ubuntu PC.
The application runs on Ubunutu in GUI mode as a GTK application.

# Installation instructions

<div style="text-align:center" markdown="1">

![](/images/download.png)

<a href="http://builds.openhome.org/releases/openhome/linux/openhomeplayer.sh">Download __OpenHome Player for Ubuntu__</a>
</div>

If you prefer to download the Player via a terminal, simply type the following into your terminal window:

```[/home/penguin]: wget http://builds.openhome.org/releases/openhome/linux/openhomeplayer.sh
```

The application is distributed as a Linux shell executable which handles installation of the OpenHome Player and all dependencies to get you up and running with minimum effort. Simply download the script, open a terminal and run the script. Once the installation is complete, you can run the Player from the commandline by typing:

```[/home/penguin]: openhomeplayer
```

To stream audio to the Player, use your OpenHome controller (eg Linn Kazoo or Bubble DS) to find your Player on the network. The player will use the same name as the Ubuntu PC it is running on. Select the Player as the current renderer, choose some tracks to play and you're ready to go!

# Features

The platform contains a number of repositories covering build tools, networking, audio pipeline and reference applications. These repositories are described in the table below.

| Feature | Description | 
|---------------|---------------|
| Audio formats    | MP3, AAC, WAV, FLAC, OGG Vorbis    |
| Audio quality    | 24-bit, up to 192kHz    |
| Internet Radio    | TuneIn    |
| Streaming Services    | Qobuz, Tidal |
| Multi-room    | Yes    |
| Managed Playlists    | Yes    |


# Requirements
- Ubuntu 12.x
- 20MB free storage space
- 16MB RAM

