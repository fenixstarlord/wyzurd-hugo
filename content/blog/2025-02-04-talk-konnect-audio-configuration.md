---
draft: true
title: Talk Konnect Audio Configuration
description: ""
date: null
preview: ""
tags: []
categories: []
---
### /boot/firmware/config.txt
`# Enable audio (loads snd_bcm2835)
dtparam=audio=on
audio_pwm_mode=2
dtoverlay=audremap,pins_23
`

### ~/.asoundrc
`    pcm.!default {
        type asym
        capture.pcm "mic"
        playback.pcm"speaker"
    }
    pcm.mic {
        type plug
        slave {
            pcm"hw:1,0"
        }       
    }
    pcm.speaker {
        type plug
        slave {
            pcm"hw:0,0"
        }
    }
`