# edison getting started


## Where to buy

Buy Edison + Mini breakout board here:

https://www.electronic-shop.lu/EN/products/154100

Getting started guide for mini breakout board:
http://www.intel.com/support/edison/sb/CS-035344.htm

General docs about Edison:
http://www.intel.com/support/maker/edison.htm

Edison hardware guide:
http://download.intel.com/support/edison/sb/edisonbreakout_hg_331190006.pdf

Connecting Edison:

--> Console on J3
--> Power on J16


## Connect to the Intel® Edison Board

At a terminal window:

    ls /dev/tty.*

In the list of connected devices, look for a device that contains cu.usbserial or tty.usbserial

Type

    screen /dev/xx.usbserial-XXXXXXXX 115200 -L

User: "root", password <enter>

### Flash with update:
https://communities.intel.com/docs/DOC-23193

http://www.intel.com/support/edison/sb/CS-035180.htm

I try with the alternate method since no Edison drive is shown on my Mac:

#### Alternate Flashing Method
Install Homebrew by running the command
type/run: ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
Install dfu-util, coreutils, and gnu-getopt
type/run:

    brew install dfu-util coreutils gnu-getopt

Download and extract Edison Image (Step 1 and 2 need to be done only once on the MAC OS X host)
Extract the contents of the pre-built Edison image
In your terminal change to the directory where you extracted the linux image.  
Run the flashall script and then plug usb cable into board
type/run:

    ./flashall.sh

Note:
If this is shown:

    Found Runtime: [xxxx:yyyy] ver=0099, devnum=6, cfg=1, intf=3, alt=0, name="UNKNOWN", serial="UNKNOWN"
    Did you plug and reboot your board?
    If yes, please try a recovery by calling this script with the --recovery option


Edit flashall.sh and put [xxxx] and [yyyy] on the lines with params

    USB_VID=
    USB_PID=

Note:
The script can take up to 5 minutes to complete the flashing

If you get a "resource busy" message try recover your screen session:

    lsof | grep usbserial

and then

    screen -x [your screen session id]

### Configure

Configure name:

    configure_edison -n

Configure password:

  configure_edison -p

Configure wifi:

    configure_edison -wifi

One the wifi AND password are:wq configured, you can see the IP of your edison:

    ifconfig

And login via WIFI and SSH:

  ssh root@[your ip here]

## Bluetooth guide

http://download.intel.com/support/edison/sb/edisonbluetooth_331704004.pdf

Enable bluetooth

    connmanctl enable bluetooth

## Links
Installing Debian Ubilinux on the Edison:
https://learn.sparkfun.com/tutorials/loading-debian-ubilinux-on-the-edison
