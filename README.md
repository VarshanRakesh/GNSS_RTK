# GNSS_RTK

## The repository explains about the setting up GNSS-RTK using the Ardusimple SimpleRTK2b series of boards

### Introduction
- We are setting up the GNSS base station at initial using the budget board and make the base station.
  
- Then Connecting RFD modems through UART to send RTCM correction data to rover.

The RFD modems send the data from base station to heading kit in a certain net id and air data rate
The moving base receive the data from the base station and send to rover board along with a heading. we can get the GPS_FIX and orientation in rover board.

### Prerequirements for setting up GNSS RTK

#### Software Requirements
1. Download U-center software
   - Download u-center from their official website [U-Center](https://www.u-blox.com/en/product/u-center) and not U-center 2.

2. Donwload RFD tools software
   - Download the RFDTools-V2.67.zip file from their website [RFD tools](https://files.rfdesign.com.au/tools/)
   - Extract the file in the separate folder
   - Go into the folder and double click the file RFD900ToolsSetup.msi and start to install.

#### Hardware Requirements
1. 1 x [Simplertk2b budget Board](https://www.ardusimple.com/product/calibrated-survey-gnss-multiband-antenna-ip67/)
2. 1 x [GNSS Survey Antenna and its cable](https://www.ardusimple.com/product/calibrated-survey-gnss-multiband-antenna-ip67/)
3. 1 x [Simplertk2b heading Kit](https://www.ardusimple.com/product/simplertk2b-heading-basic-starter-kit-ip67/)
4. 2 x [Ground Plate for GNSS antenna](https://www.ardusimple.com/product/ground-plate-for-gnss-antenna/)
5. 3 x USB-B type cables
6. 1 x [RFD868ux-IND Modem Bundle](https://store.rfdesign.com.au/rfd868ux-ind-modem-bundle-hs-8517-62-00-90/)
7. Enough amount of M-F and F-F jumper wires
Check whether all the products available as per the product links

### Preprocess
#### Configure the RFD Modems
- Connect the FTDI cable to the RFD modem as per said in the below video and select the COM port and set the baud rate to 115200 to connect with the modem.
- Refer the [Video 1](https://youtu.be/TnN78LqlCzo?si=U4I7gOx1L1zwx_7K) and [Video 2](https://youtu.be/lN28v68aL_Y?si=z5eiWCXBblHVjgfc) for configuring RFD modems.
- I have set the RFD modems to below configurations
- My configurations of the RFD modems ![rfd](https://github.com/user-attachments/assets/59c83083-9d58-4ba6-b050-ba52968d61f9)

### Setting up Simplertk2b Budget Board as a Base station:
1. Update the firmware
- Connect the Simplertk2b budget board to GNSS Survey antenna using the antenna cable given. Refer the **GPS/GNSS Antenna** section to setup the antenna in the website [User Guide: simpleRTK2B Budget](https://www.ardusimple.com/user-guide-simplertk2b-budget/#elementor-toc__heading-anchor-11).
- Connect the the USB-B type cable to **USB GPS** port in the board and other end to the PC.
- Open the U-center and connect the budget board with the suitable COM port and set the baud rate to 115200.
- From the website [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-4) go to **Firmware version check** section download the **Version 1.32**. Extract the file in separate folder.
- And follow the **Firmware update** section to update the firmware and cross check that the version updated correctly with the **Firmware version check** section found in the same website.

2. Loading the configurations as base station
- Download the base station file for the FW 1.32 version from the [add Base station configuration file]. Right click the file and select save as and save it in a separate folder.
- Before loading the configuration files recheck that you are uploading the correct file. uploading an incorrect file might lead to problems
- Load the configuration to the budget board referring the **Load a configuration file** section in [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-6)
- And save the configuration file as per the website to save the configuration in the board permenantly
- 

### Errors faced when setting up base station
1. The base station is in 3D mode and not changed to TIME or TIME/DGNSS mode
   ### Solution
   - On the top left of the U-center software select *view -> Message view*.
   - The message tab will get opened go to *Messages -> UBX -> NAV -> PVT*
   - ![add photo of enabling the the column]

### Debugging the 

### Errors faced in common
1. During the firmware update faced a Exit code 2 error when updating firmware.
   1.2 - Retry poll

   2.2 - Retry poll

   3.2 - Retry poll

   3.2 ERROR: Version poll failed.

   3.2 Firmware Update FAILED

   Firmware Update Utility has unexpectedly terminated

   Exit code (2)

   Solution
   - Connect the USB-B type cable to **USB GPS** port and not in **USB XBEE**.
   - If its not cleared then try the **Updating over USB** section in the video [How to update the firmware on u-blox GNSS receivers](https://youtu.be/lqZ1wTd9gKU?si=oB4lXuNcgepNKxc9).
