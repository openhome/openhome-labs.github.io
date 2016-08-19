---
layout: content-no-sidebar
title: Raspberry Pi
header : Get the OpenHome Player for Raspberry Pi now!
weight: 10
parent: use
---
{% include JB/setup %}

> Download OpenHome Player for your Raspberry Pi

**OpenHome Player for Raspberry Pi** is an inobtrusive media streamer which sits in your system menu allowing you to stream high quality digital audio from your network servers and internet streaming services to your Raspberry Pi board.
The application runs on Raspberry Pi in GUI mode as a GTK application, or if you don' want a GUI version, you can download the headless version which runs straight from the commandline.

# Installation instructions

<div style="text-align:center" markdown="1">

![](/images/download.png)

<a href="http://builds.openhome.org/releases/openhome/piplayer.sh" download>Download __OpenHome Player for Raspberry Pi__</a>

<a href="http://builds.openhome.org/releases/openhome/piheadless.sh" download>   or __OpenHome Player (Headless) for Raspberry Pi__</a>
</div>

If you prefer to download the Player via a terminal, simply type the following into your terminal window:

``` wget http://builds.openhome.org/releases/openhome/piplayer.sh
```

or

``` wget http://builds.openhome.org/releases/openhome/piheadless.sh
```
The application is distributed as a Linux shell executable which handles installation of the OpenHome Player and all dependencies to get you up and running with minimum effort. Simply download the script, open a terminal and run the script. You may need to add executable permission to the file. Once the installation is complete, you can run the Player from the commandline by typing:

``` openhome-player
```

To stream audio to the Player, use your OpenHome controller (eg Linn Kazoo or Bubble DS) to find your Player on the network. The player will use the same name as the Pi board it is running on. Select the Player as the current renderer, choose some tracks to play and you're ready to go!

# Features

The platform contains a number of repositories covering build tools, networking, audio pipeline and reference applications. These repositories are described in the table below.

| Feature | Description |
|---------------|---------------|
| Audio formats    | MP3, AAC, WMA, FLAC, ALAC, OGG Vorbis |
| Audio quality    | 24-bit, up to 192kHz    |
| Internet Radio    | TuneIn    |
| Streaming Services    | Qobuz, Tidal |
| Multi-room    | Yes    |
| Managed Playlists    | Yes    |


# Requirements
- Raspbian (jessie)
- 20MB free storage space
- 16MB RAM
- external DAC board (for hi quality audio - onboard DAC is very poor)
