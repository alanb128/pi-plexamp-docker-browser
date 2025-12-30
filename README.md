# Headless Plexamp 
This is a combination of two pre-made containers working together:

- [plexamp-docker](https://github.com/anatosun/plexamp-docker) by user anatosun, a containerized version of Headless [Plexamp](https://www.plex.tv/plexamp/)
- the balena [Browser Block](https://github.com/balena-io-experimental/browser), a pre-built container image that provides a hardware-accelerated Chromium web browser for devices running balenaOS

With this combination, you can have plexamp running on a Raspberry Pi, outputting the audio via the headphone jack or an attached DAC. The UI will be output via the HDMI jack courtesy of the browser block for display on a wall TV or other such device.

<img src="tv_headless.jpg">

## Setup

Either use this compose file with regualr Docker on a Pi, or (better yet) use [balenaCloud](https://www.balena.io/) and [push this project](https://docs.balena.io/learn/getting-started/raspberrypi4-64/nodejs/) to your device or use the button below.

[![balena deploy button](https://www.balena.io/deploy.svg)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/alanb128/pi-plexamp-docker-browser/)

This project was tested on a Pi 4 with 2GB of RAM, but should run fine on a Pi 5.

After deploying this app to your device, do the following:

- change the "Define device GPU memory in megabytes." setting in the device configuration to at least 64MB
- add a device variable called `PLEXAMP_CLAIM_TOKEN` with a value of your calim token
- add a device variable called `PLEXAMP_PLAYER_NAME` with a name for your player
- add a device variable called `LAUNCH_URL` with the IP of your device and port, for example `192.168.1.192:32500`
- optionally add a device variable called `KIOSK` with a value of `1` to disable the tabs and URL from the display

## Use

You'll need to boot the device with an HDMI monitor attached so it gets detected by the browser block. Unfortunately headless Plexamp as of this writing still requires you to log in every time you boot/open a browser, so you may need to temporarily attach a mouse/keyboard. (Attach the USB devices before boot so they are detected.)


