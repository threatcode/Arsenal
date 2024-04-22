---
title: Using the Raspberry Pi Imager software to write Kali Raspberry Pi Images
description:
icon:
author: ["steev",]
---

An additional option for writing Kali Raspberry Pi images to either a MicroSD card or USB device is to use the [Raspberry Pi Imager software](https://raspberrypi.com/software/) which is available for Windows, macOS, and Linux.

{{% notice info %}}
At this time we do **NOT** support the "Advanced" menu for setting options for customizing your Raspberry Pi. Please consult the [documentation](/docs/arm/) for your specific Raspberry Pi device for setting up the Wi-Fi network.
{{% /notice %}}

Once you have downloaded the software and installed it, simply run the software and you should be presented with the following screen:

![](images/rpi-imager-main.png)

- - -

From here we will click the button that says `Choose OS` and then scroll down and choose `Other specific-purpose OS`:

![](images/rpi-imager-choose-os.png)

- - -

And then from this list choose `Kali Linux`:

![](images/rpi-imager-choose-os-other-specific.png)

- - -

From here you choose whichever Kali Raspberry Pi image you want to write, and it will take you back to the main screen of the application:

![](images/rpi-imager-choose-kali.png)

- - -

Now click on `Choose Storage` and the software should only let you choose from removable devices on your machine:

![](images/rpi-imager-choose-storage.png)

- - -

Once that is done, simply click the `Write` button:

![](images/rpi-imager-write.png)

- - -

Once you have clicked the `Write` button, the software will start downloading the image, then write it to the removable storage device that you have chosen. It will verify the SHA256 checksum, and then verify that they also match after writing. Once it tells you that it is complete, you can plug the storage device into your Raspberry Pi and boot up the Raspberry Pi.

You should be able to [log in to Kali](/docs/introduction/default-credentials/).
