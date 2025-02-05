---
draft: false
title: Meshtastic
description: Creating a meshtastic ecosystem for the end of the world.
date: 2025-02-05T20:26:17.912Z
preview: he other day, my good friend George Costakis brought up his interest in Meshtastic, a 915MHz comms network. Meshtastic had been floating around my periphery for a while, and the idea of joining a node network that could bridge my house to George's sounded pretty cool. Cue my hyperfixation!
tags:
    - meshtastic
categories: []
---
{{< figure src="/blog/social-preview-1200x630.png" alt="" width="100px" >}}

The other day, my good friend George Costakis brought up his interest in Meshtastic, a 915MHz comms network. Meshtastic had been floating around my periphery for a while, and the idea of joining a node network that could bridge my house to George's sounded pretty cool. Cue my hyperfixation!

# Hands On
At first, I overnighted a Heltec V3 just to play with. It became very clear, almost immediately, that the all-in-one kits for $20 are pretty much worthless without additional parts.

{{< figure src="/blog/71S1LboANBL._AC_SX679_.jpg" alt="" width="100px" >}}

The antenna was too weak, and the case it came with didn't house the battery, but that’s fine. It let me get my hands on the hardware and get an idea of what I needed.

That led to my idea of the following build-out: one base station and two GPS nodes (one for me and one for my partner). These would be invaluable in case of a disaster where we’re unable to text each other—we could easily pull up the Meshtastic app and see where we are on a map. On the more mundane side of things, there's a shopping center near our house that is a complete signal dead spot, and we would still be able to text each other.

After researching different models (ESP32 vs. nRF52840), I decided my priority was affordability. My Amazon-purchased Heltec V3 could serve as my base station, and the Heltec Trackers (basically a V3 with GPS) would work as in-car communicators.

# The Base Station
{{< figure src="/blog/large_display_b572ae2b-bbaf-42d6-8c3a-84f2a6c5b974_816502.webp" alt="" width="100px" >}}
### Hardware List
- [Heltec v3](https://www.amazon.com/dp/B0DGTBL2VW?ref=ppx_yo2ov_dt_b_fed_asin_title&th=1)
- [Alfa AOA-915-5ACM](https://store.rokland.com/products/alfa-aoa-915-5acm-5-dbi-omni-outdoor-915mhz-802-11ah-mini-antenna-for-lora-halow-application)
- [UFL(IPEX/IPX) Mini PCI to N-Female Bulkhead Pigtail Cable Extension](https://store.rokland.com/products/uflipex-ipx-mini-pci-to-n-female-bulkhead-pigtail-cable-extension-rg178?_pos=1&_sid=f702443ea&_ss=r)
- [Project Box](https://www.amazon.com/QILIPSU-150x150x90mm-Universal-Waterproof-Electrical/dp/B083JSQZYP?ref_=ast_sto_dp&th=1)

For the base station I'm going to use my already purchased Heltec v3. This build is pretty simple, I'm going off of the [reccomended antennas](https://meshtastic.org/docs/hardware/antennas/) on the meshtastic website.

I'm going to re-use the LiPo battery that came with the Heltec v3 kit, but if I were ordering from scratch I would get the same Li-Ion battery I'm using in the mobile unites.

Everything is going to go into the project box, I will drill a couple holes, one for power in, and the other for antenna out, and then I'm going to put this on the roof of my house. Very simple home station that will allow a large signal for any communication in town.

# The Mobile Units
{{< figure src="/blog/20231018_223857.webp" alt="" width="100px" >}}
### Hardware List
- [Heltec Tracker (915mhz model)](https://www.aliexpress.us/item/3256805495189423.html)
- [LINX ANT-916-CW-HW-SMA Antenna](https://www.mouser.com/ProductDetail/TE-Connectivity-Linx-Technologies/ANT-916-CW-HW-SMA?qs=PKuFCuYbGOfeZQiEfd4fWA%3D%3D)
- [Samsung 35E 18650 3500mAh 8A -Protected Button Top Battery](https://www.18650batterystore.com/products/samsung-35e-protected)
- [Heltec Wireless Tracker case for Meshtastic by Tony G on Printables](https://www.printables.com/model/616628-heltec-wireless-tracker-case-for-meshtastic)

As I mentioned before, I decided to go with the Heltec Tracker since it was affordable and included a GPS chip.

Instead of using LiPo, I will be using the Samsung 18650 battery with built-in protection (important for when it's left in a car). I’m a little unsure about this part, and I’m buying this specific model because Tony G’s design is centered around it. I’m not exactly sure how it’s wired into the board, but I’ll find out as soon as it arrives.

The antenna is one I’m familiar with—it’s something we DITs have been using on set for our 915MHz control boxes (Spudnik, BitBox, TeeHee).

I can't wait for the parts to come in! Building these little devices is incredibly easy, and having some peace of mind when living near fire country and in an earthquake zone will be well worth the ~$40 per unit.