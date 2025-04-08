# GNSS_RTK

## The repository explains about the setting up GNSS-RTK using the Ardusimple SimpleRTK2b series of boards
### Introduction
We are setting up the GNSS base station at initial and make the base station to send correction messages through RFD radio modems.
The RFD modems send the data from base to rover in a certain net id and air data rate
The moving base receive the data from the base station and send to rover board along with a heading. we can get the GPS_FIX and orientation in rover board.

### Requirements for setting up GNSS RTK

#### Download U-center 
Download u-center from their official website [U-Center](https://www.u-blox.com/en/product/u-center) and not U-center 2.

#### Configure the RFD Modems
##### Donwload RFD tools software
- Download the RFDTools-V2.67.zip file from their website [RFD tools](https://files.rfdesign.com.au/tools/)
- extract the file in the separte foler
- Go into the folder and select the file RFD900ToolsSetup.msi for intallation.
##### Configuring the RFD modem
- Connect the FTDI cable to the RFD modem as per said in the below video and select the COM port and set the baud rate to 115200 to connect with the modem.
- Refer the [Video 1](https://youtu.be/TnN78LqlCzo?si=U4I7gOx1L1zwx_7K) and [Video 2](https://youtu.be/lN28v68aL_Y?si=z5eiWCXBblHVjgfc) for configuring RFD modems.
- I have set the RFD modems to below configurations
- My configurations of the RFD modems ![]

### Firmware Update on simplertk2b boards  
- From the below website  
> https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-4
- In this website go to **firmware version check** section download the **Version 1.32**. Extract the file in separate folder.
- And follow the **F
