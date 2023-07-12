---
title: Corne Keyboard
categories: Self-host
---

# Resources
- [Wireless Corne Keyboard Full Build From Scratch](https://youtu.be/MBV2Vrizpe0)
- [Wireless Corne Review](https://youtu.be/wTMcH7u-vu0)
- [Corne Github](https://github.com/foostan/crkbd)
    - Gerber file under [releases](https://github.com/foostan/crkbd/releases)
- [Wireless Corne EIGA](https://youtu.be/hXohJwatIpA)
- [A Tiny, Ultra-Affordable Keyboard You Can Build Yourself!](https://youtu.be/JqpBKuEVinw)
- [Wireless Corne Keyboard Perfected](https://youtu.be/YlZPnh9cbQU)
- [How to Build a Wireless Corne Keyboard](https://youtu.be/FJgvi7WShxY)
- [Corne MX 3.0 Keyboard build guide](https://reallifeprogramming.com/corne-mx-3-0-keyboard-build-guide-9b5c7eff4178)
    - Explains step by step where to get gerber file, parts, and assembly
- [Sofle Keyboard - sourcing parts](https://josefadamcik.github.io/SofleKeyboard/sourcing_parts.html)
- [Case](https://www.printables.com/model/347524-corne-keyboard-case/files)
- [Soldering battery](https://docs.nicekeyboards.com/#/nice!nano/getting_started)

# Parts
- [X] [PCB](https://www.diykeyboards.com)
    - Purchasing PCB from a seller, purchasing through PCBWay or jlcpcb is too expensive due to shipping costs and minimum board ammount
- [X] [OLED Display](https://www.amazon.com/gp/product/B079BN2J8V/ref=ppx_yo_dt_b_asin_title_o00_s01?ie=UTF8&psc=1)
- [X] 2x [nice!nano](https://typeractive.xyz/products/nice-nano)
- [X] [SMD Diodes](https://www.amazon.com/gp/product/B09TKVYJL6/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1)
- [X] [Kailh hotswap sockets for MX](https://www.amazon.com/gp/product/B0BVH6M5FP/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)
- [X] [Flux](https://www.amazon.com/gp/product/B07B53LNGX/ref=ppx_yo_dt_b_asin_title_o01_s01?ie=UTF8&psc=1)
- [X] [Tweezers](https://www.amazon.com/gp/product/B00JS42110/ref=ppx_yo_dt_b_asin_title_o01_s01?ie=UTF8&psc=1)
- [X] [Keys](https://www.amazon.com/dp/B07X3VLF89?psc=1&ref=ppx_yo2ov_dt_b_product_details)
- [X] [Battery](https://www.amazon.com/dp/B09WK8Y183?psc=1&ref=ppx_yo2ov_dt_b_product_details)
- [X] [Key Caps](https://www.amazon.com/gp/product/B06VWBV3Q7/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)

# Roadblocks
- Ripped a pad off of a PCB, had to buy a new set
- Soldered the Nice! Nano headers on the wrong side, had to painstakingly de-solder and re-solder headers on correct side
- PCB I purchased didn't come with a battery header or pads for a switch. My plan right now is to direcly solder battery to the Nice! Nano and inline a small power switch
- I wasn't able to find the correct headers or pins for the Nice! Nano so it sits higher that it's supposed to, as a result, the usb-c port is blocked by the top part of the case, I had to cut the case in order to expose the usb-c port
- Microcontroller got bricked
    - Bought an ST-Link
    - Tried to follow [this guide](https://nicekeyboards.com/docs/nice-nano/troubleshooting/) but ran into issues
    ```
    WARNING: interface/stlink-v2.cfg is deprecated, please switch to interface/stlink.cfg
    Info : auto-selecting first available session transport "hla_swd". To override use 'transport select <transport>'.
    Info : The selected transport took over low-level target control. The results might differ compared to plain JTAG/SWD

    nRF52 device has a CTRL-AP dedicated to recover the device from AP lock.
    A high level adapter (like a ST-Link) you are currently using cannot access
    the CTRL-AP so 'nrf52_recover' command will not work.
    Do not enable UICR APPROTECT.

    force hard breakpoints
    Info : clock speed 1000 kHz
    Error: open failed
    ```
    - Tried to use [STM32 ST-Link utility](https://www.st.com/en/development-tools/stsw-link004.html?dl=U9VsvLy1NvbAKrKkpaO%2BWw%3D%3D%2CTfkFiGHZMH4B1b0dD8ZEIFgAYlEdFHFLcpqtAEsmJH%2BDrsV6CnsN%2BpWTPcQHW3%2FaTfsGONgXQXaBmFDm6E7fS9m3kHjoS9jSfFHzuDBjt8oxLz54gO%2BfmYym24r2IF4oVnsLYT7oWc8Lo%2F8XsTnKsloJNTY8hCk33y5uFbp7j7zvF1PFxlTjCNtn4sZMRpLuM5RQl%2FXVAps1GIPNygK4GPDOoWW5xSAtgCpLFMn6TPZWe2j6ul7XBpKNOdAT6e94k8T0M13JFKLBfQJ8A5sj%2FekhznStPJNvqWsSk2e6sOPdgyT3XEag87WHpGXvbaZj#overview) but wasn't able to connect successfully
    - Might try using an IDAP-Link, according to [this post](https://devzone.nordicsemi.com/f/nordic-q-a/14672/unable-to-connect-to-nrf51822-with-openocd-and-stlink-v2-via-swd) someone was having the same issues of not being able to connect to the microcontroller and it was suggested to use the IDAP-Link instead of the ST-Link
    #### Resources
    - [Low Level Learning Debugging with OpenOCD](https://youtu.be/_1u7IOnivnM)
    - [Flashing STM32 with ST-Link](https://youtu.be/1cleO3mHjWw)
    - [ST-Link Flashing windows](https://youtu.be/NAWpqNjOGlc)

# What I Learned
- Overall it was an interesting project, I'm still debating on if I want to make a keyboard again from scratch or not. It was tedious at times but I learned a lot and had fun making it. It was definitly an interesting experience. Now that I've done it once, I think if i do it again it will be a lot easier. Once I learn this 42-key layout i want to try to downsize to a 36-key layout but thats way in the future. Still need to make some modifications to the layout as I use it more.