# Rpizerow2usbgadget
## Raspberry Pi Zero W 2 USB GADGET (+HEADLESS)

To install Raspbian OS headlessly on your Raspberry Pi Zero W 2 without using an external keyboard or monitor, follow this step-by-step guide. This method allows you to connect your Raspberry Pi via a USB OTG cable to a mobile device or PC and eliminates the need for an internet connection to access SSH or VNC.

## PROS
- No need for an internet connection for SSH or VNC access to your Raspberry Pi.
 - Lightweight headless build.
  - Can connect to mobile devices using an OTG cable.
## CONS
- When connected to a computer as an Ethernet device via USB, internet sharing must be enabled on your PC for the Raspberry Pi to access the internet.
 - Wireless modules can't be used when connected as an Ethernet device via USB.
  - Don't do that if you needn't.
## REQUIREMENTS
 - Raspberry Pi Zero W 2 (I think work same as other RPI)  
  - USB-Micro USB Cable (OTG CABLE)  
   - MICROSD CARD with ADAPTER (SDHC card example)
    - PC for initial setup.
## INSTALLATION
1. Format Your SD Card

First, format your MicroSD card using an SD card formatting tool. This will ensure your card is ready for the OS installation.
![Format your SD card.](https://imgur.com/GPGGNql.png) 

Steps:

    -Insert your MicroSD card into your PC.
    -Open the formatting tool and select your MicroSD card from the device list.
    -Choose the Quick Format option and start the formatting process.
    
2. Download and Install Raspberry Pi Imager

Next, you'll need to install the official Raspberry Pi Imager on your PC to flash the Raspberry Pi OS onto the MicroSD card.
    
 - [Download](https://www.raspberrypi.com/software/) Official Raspberry Pi Imager

Steps:

    Install and launch the Raspberry Pi Imager.
    Select the Operating System option and choose Raspberry Pi OS (other).
    Then, choose Raspberry Pi OS Lite (32-bit).
3. Flash the SD Card
Use the Raspberry Pi Imager to flash the OS to your MicroSD card.

Steps:

    In Raspberry Pi Imager, choose the Raspberry Pi OS Lite image.
    Select your MicroSD card as the storage device.
    Click Write to begin flashing the OS.
  - [Download](https://www.raspberrypi.com/software/operating-systems/) Raspberry PI OS LITE

  - Select Custom Images then choose your LITE OS tar.

![images](https://i.imgur.com/mdoBRk0.png)

4. Configure for Headless Mode (Enable SSH and Wi-Fi)

After flashing the OS, you’ll need to enable SSH and configure Wi-Fi directly on the MicroSD card.

Steps:

    Eject and reinsert the MicroSD card into your RPi.
    Navigate to the boot partition of the SD card.

Enable SSH:

    Create an empty file named ssh (without any extension) in the root directory of the boot partition. This enables SSH on the Raspberry Pi.

Configure Wi-Fi:

    Create a file named wpa_supplicant.conf in the same directory and add the following content:

Bash:
```
country=YOUR_COUNTRY_CODE
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
    
network={
ssid="YOUR_WIFI_SSID"
psk="YOUR_WIFI_PASSWORD"
key_mgmt=WPA-PSK
}
```
Replace YOUR_COUNTRY_CODE with the appropriate code for your location (e.g., US for the United States).
Replace YOUR_WIFI_SSID and YOUR_WIFI_PASSWORD with your Wi-Fi network credentials.

5. Connect Your Raspberry Pi

    Insert the MicroSD card into your Raspberry Pi Zero W 2.
    Connect your Raspberry Pi to your PC or mobile device using the OTG cable.

6. SSH into Your Raspberry Pi

You can now SSH into your Raspberry Pi from your PC without needing an internet connection.

Steps:

    Open a terminal (on Linux/macOS) or use an SSH client like PuTTY (on Windows).
    Run the following command:

Bash:

    ssh pi@raspberrypi.local

The default username is pi and the default password is raspberry.
7. (Optional) Enable Internet Sharing

If you need to provide internet access to your Raspberry Pi while it's connected as an Ethernet device, you'll need to enable internet sharing on your PC.

    Windows: Go to Network and Sharing Center, and enable internet sharing for the Ethernet connection associated with your Raspberry Pi.
    macOS: Open System Preferences > Sharing, and enable Internet Sharing for your Raspberry Pi's connection.

And you're done!

Now your Raspberry Pi is set up in headless mode, and you can SSH into it without external monitors or keyboards.
