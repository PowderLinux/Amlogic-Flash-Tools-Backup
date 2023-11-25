# Amlogic-Flash-Tools-Backup
A repo for hosting a backup of Amlogic flash tools for Linux

##

### About:

Tools for Linux that can be used to flash stock firmware or custom roms on Amlogic brand Android tv boxes.

I found these on GitHub awhile back.. I did not make them- the only thing I made is the install guide..

The reason I am hosting these is because I dont remember the repos that I got them from.. (2 seperate repos)

##

### Versions:

#### aml-flash-tool-s905x4.zip

Use this version for newer boards. Ex: S905X4, S905Y4, etc.. Tool name = 'adnl_flash_tool.sh'

#### aml-flash-tool-s905x3.zip

Use this version for older boards. Ex: S905X3, S912, etc.. Tool name = 'aml-flash-tool.sh'

##

### How To Use:

1. Prepare your device by following the install guide below
 
2. Extract the zip for the tool version that you need

3. Open a terminal in the extracted directory

4. Run the flash tool

##

### Run/Flash Examples: 

#### S905X3 tool -
```
./aml-flash-tool.sh /path/to/your/firmware/firmware.img
```
#### S905X4 tool -
```
./adnl_flash_tool.sh -p /path/to/your/firmware/firmware.img
```

##

### Install Guide:

#### Install dependencies -
```
sudo apt install libusb-dev git parted lib32z1 lib32stdc++6 libusb-0.1-4 libusb-1.0-0-dev libusb-1.0-0 ccache libncurses5 pv base-files linux-base lib32ncurses6
```

#### Create udev rules - 
```
sudo nano /etc/udev/rules.d/70-persistent-usb-amlogic.rules
```

##### Copy/paste the following lines into the file - ***(NOTE: make sure you change OWNER="p0wder" to OWNER="yourusername")***
```
SUBSYSTEMS=="usb",ATTRS{idVendor}=="1b8e",ATTRS{idProduct}=="c003",OWNER="p0wder",MODE="0666",SYMLINK+="worldcup"
SUBSYSTEMS=="usb",ATTRS{idVendor}=="1b8e",ATTRS{idProduct}=="c004",OWNER="p0wder",MODE="0666",SYMLINK+="worldcup"
```
#### 

#### Reload rules -
```
sudo udevadm control --reload-rules
```

#### Done!

##

### Verify:


Plug in your Android box and verify everything was setup properly by using ```lsusb``` and/or ```ls -lla /dev```


With ```lsusb``` you are looking for a device labeled 'Amlogic'


And with ```ls -lla /dev``` you are looking for a device called '/dev/worldcup'


If you see both of those, then you are good to go and can proceed to run the flash script

##

### NOTES:

* The install guide applys to both S905X4 and S905X3 versions.

* Theres an INSTALL.sh script included that might work if you are on Ubuntu.. It didnt work when I tried it on Debian 11. The guide above should work fine on either one tho- you just might need to adjust the dependencies names.

* The aml_flash_tool.sh included with the S905X4 build is supposed work with older boards, but I had issues with it trying to flash a S905X3 board. The seperate S905X3 build version works fine tho.
  
##

### Credits:

Not me, and not trying to steal anyones work.. If you are one of the orignal devs, reach out and I will add you here if you want.

##
