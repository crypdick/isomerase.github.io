---
layout: post
title: Getting Immersed VR setup on Ubuntu
---

In my quest to perfect my "road warrior" setup, I have been experimenting with coding in VR. I have been using the Immersed VR app on my Quest 3 headset to create a virtual workspace. Unfortunately, the official Immersed documentation is not very clear on how to get Immersed VR setup on Ubuntu. Here are the steps I took to get it working. I would like to credit [this blog post by Alexandre Souza](https://devevangelista.medium.com/immersed-linux-life-bc2e2661c7aa) for pointing me in the right direction, my contribution is porting the steps to Ubuntu Linux.

Steps:
* Follow the instructions on the [Immersed VR website](https://immersedvr.com/) to install the Immersed VR app on your headset and on Linux ([download page here](https://immersed.com/download)).
* Install the required dependencies:

```bash
sudo apt install v4l2loopback-dkms v4l2loopback-utils
```

* Create a file to start the v4l2loopback service at boot:

```bash
sudo vim /etc/systemd/system/v4l2loopback.service
```

Here are the settings I used for the service file, based on the aforementioned blog post. The device is set to `/dev/video9` to avoid conflicts with other devices.

```bash
[Unit]
Description=v4l2loopback

[Service]
ExecStart=/bin/modprobe v4l2loopback video_nr=9 card_label="ImmersedVR" exclusive_caps=1
ExecStop=/bin/rmmod v4l2loopback
Type=simple
RemainAfterExit=yes

[Install]
WantedBy=default.target
```

* Enable the service:
    
```bash
sudo systemctl enable v4l2loopback
```

* Start the service:

```bash
sudo systemctl start v4l2loopback
```

* Update the `~/.ImmersedConf` file to use the new device:

```bash
# before:
# "CameraDevice": "/dev/video0"
# after:
"CameraDevice": "/dev/video9"
```

* Run the ImmersedVR AppImage:

```bash
chmod +x Immersed-x86_64.AppImage
./Immersed-x86_64.AppImage
```

On my machine, the app will display a "Virtual camera device is not found at /dev/video0" error, even though we set the config file to use `/dev/video9`. I just click "OK" and the app correctly uses the `/dev/video9` device.

Another tip is that you can create virtual monitors, even if you don't have a physical monitor connected. This is natively supported by the Immersed app on Windows/Mac, but for Linux you need to use a tool like `xrandr` to create a virtual monitor. [This blog post by Craig Wardman](https://www.craigwardman.com/blog/creating-additional-monitors-in-immersed-for-linux) explains how to do it.