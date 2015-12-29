---
layout: content-no-sidebar
title: Overview
header : OpenHome - A Developer's Overview
weight: 10
parent: develop
---
{% include JB/setup %}

## OpenHome Architecture

The OpenHome platform comprises full Renderer and ControlPoint stacks which are based on UPnP services but both extended and simplified to provide a richer, more robust and interoperable environemnt for networked audio playback.

OpenHome builds on the foundation of the ohNet cross-platform UPnP networking library, implementing a full audio pipeline engine through the ohPipeline module which. ohPipeline provides a plugin architecture for codecs, audio sources and audio drivers with flexible routing and caching of pipeline data to ensure seamless playback.
The diagram below shows the major architectural components of the platform.

<div style="text-align:center" markdown="1">

![OpenHome Architecture](/images/oh-arch.png)

</div>


### ohPipeline

ohPipeline is a portable software audio pipeline with the following key features:

| Feature | Description |
|---------|-------------|
| Audio Formats | FLAC, MP3, ALAC, WAV, AAC, Vorbis, WMA |
| Sample Rates | from 7.35kHz to 192kHz, in 44kHz and 48kHz families |
| Bit depth | 8, 16, 24 bit |
| Channels | 1 to 8 |
| | |
| Playlist Source | Store a playlist of hundreds or even thousands of tracks on device, playing these without requiring further interaction from a control point. |
| | |
| Songcast Sender | Share your audio stream with an unlimited number of other players |
| Songcast Receiver | Listen to the same audio stream as another device, in exact synchronisation with that device and all other receivers. |
| | Supports all audio resolutions, up to and including 24-bit / 192kHz |
| | "Clock pulling" architecture guarantees that playback starts then remains synchronised between all devices |
| | |
| Radio | Supports internet radio stations, podcasts and listen again. Includes integration to the popular TuneIn service, allowing users to setup personalised presets from a list of all worldwide internet stations. |
| | |
| UPnP:AV | Presents the standard UPnP Media Renderer network services for use with basic control points. |
| | |
| Physical Inputs | Playback of popular analogue and digital inputs - HDMI, SPDIF, TOS, Analogue, etc. |
| | |
| Airplay | Receive an audio stream via Apple’s Airplay protocol. |

### System Requirements

RAM: 16MB standard; 4MB possible

ROM: 8MB standard; 2.5MB possible (if Radio and Airplay sources are omitted)

### Integration

Integrating OpenHome into your product involves a small number of tasks.

- Driver. This pulls decoded audio samples from ohPipeline’s audio pipeline and is responsible for feeding them into the host’s audio hardware at the appropriate rate.
- Mutes. Optionally mute audio hardware around changes in audio sample rate or bit depth.
- OS compatibility layer. Threading and socket abstractions. Many standard platforms are available with ohNet, including
        Linux (x86, x64, ARM)
        Windows (x86, x64)
        Mac (x86, x64)
        Embedded (using FreeRTOS and lwIP). Big and little endian ports exist. 
- R/W Store. At a minimum, this can simply provide a set of string literals that are determined at design time. If runtime user configuration is supported, this should also provide a means to persist and restore (string) key / (binary) value pairs.
- Application. This will initialise the UPnP stack, set up UPnP and media player objects and configure the required input sources, codecs etc. You will also need to implement a driver for the audio output, and provide read/write storage for persistent configuration properties.


The platform also provides additional capabilities including:

- On-device UPnP service
- On-device web UI to access these configuration values
- Desktop/mobile app to detect media players and display their configuration page. 

