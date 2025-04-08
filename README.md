# GNSS_RTK

## The repository explains about the setting up GNSS-RTK using the Ardusimple SimpleRTK2b series of boards

### Introduction
We are setting up the GNSS base station at initial and make the base station to send correction messages through RFD radio modems.
The RFD modems send the data from base station to heading kit in a certain net id and air data rate
The moving base receive the data from the base station and send to rover board along with a heading. we can get the GPS_FIX and orientation in rover board.

### Prerequirements for setting up GNSS RTK

#### Download U-center 
Download u-center from their official website [U-Center](https://www.u-blox.com/en/product/u-center) and not U-center 2.

#### Configure the RFD Modems
1.  Donwload RFD tools software
- Download the RFDTools-V2.67.zip file from their website [RFD tools](https://files.rfdesign.com.au/tools/)
- extract the file in the separate foler
- Go into the folder and select the file RFD900ToolsSetup.msi and start to install.
2.  Configuring the RFD modem
- Connect the FTDI cable to the RFD modem as per said in the below video and select the COM port and set the baud rate to 115200 to connect with the modem.
- Refer the [Video 1](https://youtu.be/TnN78LqlCzo?si=U4I7gOx1L1zwx_7K) and [Video 2](https://youtu.be/lN28v68aL_Y?si=z5eiWCXBblHVjgfc) for configuring RFD modems.
- I have set the RFD modems to below configurations
- My configurations of the RFD modems ![rfd](https://github.com/user-attachments/assets/59c83083-9d58-4ba6-b050-ba52968d61f9)


### Firmware Update on all of the three simplertk2b boards
1. Connect the Simplertk2b budget board to GNSS Survey antenna using the cable given. Refer the **GPS/GNSS Antenna** section to setup the antenna in the website [User Guide: simpleRTK2B Budget](https://www.ardusimple.com/user-guide-simplertk2b-budget/#elementor-toc__heading-anchor-11).
2.  Connect the the USB-B type cable to USB GPS port in the board and other end to the PC.
3.  Open the U-center and connect the budget board with the suitable COM port and set the baud rate to 115200.
4.  From the website [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-4) go to **firmware version check** section download the **Version 1.32**. Extract the file in separate folder.
5.  And follow the **Firmware update** section to update the firmware and cross check that the version updated correctly with the **Firmware version check** section found in the same website.

### Configuring the Budget board as base station
1. Download the base station file for the FW 1.32 version
   
### Errors faced
#### During the firmware update
_ Exit code 2 error when updating firmware. ![Exit Code 2](https://github.com/user-attachments/assets/265a4965-c2ab-4ddb-9ff9-58feac1f88eb)
- Connect the USB-B type cable to USB GPS and not in USB XBEE
- If its not cleared then try the **Updating over USB** section in the video [How to update the firmware on u-blox GNSS receivers](https://youtu.be/lqZ1wTd9gKU?si=oB4lXuNcgepNKxc9).
