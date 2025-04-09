# GNSS_RTK

## The repository explains about the setting up GNSS-RTK using the Ardusimple SimpleRTK2b series of boards

### Introduction
- We are setting up the GNSS base station at initial using the budget board.
  [budget board](https://drive.google.com/file/d/1BCfeUO_d3VfTKhyv1hLUf-4cxIwgMuPJ/view?usp=sharing)
- Then Connecting RFD modems through UART to send RTCM correction data to rover.
  [RFD modem bundle](https://drive.google.com/file/d/13ibd_IgPIkQSamidDO5Xe9yXCAReV8D_/view?usp=sharing)
- The RFD modems send the data from base station to heading kit in a certain net id and air data rate
- The lite board receive the data from the base station and send to rover board along with a heading.
  This is the [lite board](https://drive.google.com/file/d/1u88w4nWhP7Q3zKQGI1OfgxTFqHJ6ganu/view?usp=sharing) and its fixed on top of rover board makes a [heading kit](https://drive.google.com/file/d/1lNw7_xqfe9rYd88Ts9wYZaOKLzkWChKY/view?usp=sharing)
- We can get the *GPS_FIX* and *Orientation* from the **USB GPS** port in the rover board

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
1. Connect the FTDI cable to the RFD modem for configuring RFD modems.
2. This is the photo of connecting RFD to *FTDI cable*. The 8 wires connector in the middle is the *900ux to 8 way socket cable*. Check with the colour combination of the *FTDI cable* and the *900ux to 8 way socket cable* is as per the below photo [RFD connections](https://drive.google.com/file/d/13ibd_IgPIkQSamidDO5Xe9yXCAReV8D_/view?usp=sharing) like the left most pin in the rfd is the *GND pin* and it should connected with the black colour wire of the *FTDI cable*.
3. I have set the RFD modems to below configurations
4. My configurations of the RFD modems [rfd configuration](https://drive.google.com/file/d/18Ow4NDiqd2Y3rOrZe9pQzE8ZL7ej17cq/view?usp=sharing).
5. Remove the *900ux to 8 way socket cable* from the rfd modem and connect it to the other modem and repeat the same steps from 1 to 4 to other rfd modem also.
6. The RFD configurations of the both modems should be same to make the communication properly.

#### Checking the communication has established perfectly
1. The RFD pins and description of the pins are attached here [RFD pins](https://drive.google.com/file/d/1_1pGPY-Zll1vpbcY_PLTCZBHFamawTuh/view?usp=sharing) and [pin description](https://drive.google.com/file/d/1SPAdANj01Gd1S9Tws-nG_HSz-fE_Nani/view?usp=sharing)
2. Dump a general *UART transmitter* code with a baud rate of 115200 in one of the arduino and then connect the *UART pins* of the RFD modem to *UART pins* of the Arduino as per below
   TX pin of RFD modem -> RX pin of Arduino
   RX pin of RFD modem -> TX pin of Arduino
   GND pin of RFD modem -> GND pin of RFD modem
3. Dump a general *UART receiver* code with the same baud rate in another arduino board and follow the same connections as per the step 2.
4. Check whether data is received in the receiver arduino in serial monitor. Set the serial monitor with the same baud rate to get the data received.
   
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
   - And **Save the configuration** file as per the website to save the configuration in the board permenantly
   - Follow the **Create a configuration file** section in the same website to update the changes you have made in the configuration of the board to an existing configuration file in the PC.

3. Connecting the RFD modem to the budget board to send the data over radio
   - Connect the **V Standard pin** of the RFD modem to **5V pin** of Arduino and **GND pin** of the Arduino to **GND pin** of the Budget Board
   - Connect the IOREF pin of the Budget board to 3.3V OUT pin so that the uart pins work on 3.3V power
   - Connect the TX pin of the RFD modem to the Budget board's TX2 pin and RX pin of the RFD modem to the Budget board's RX
  
### Errors faced when setting up base station
1. The base station is not changed to TIME or TIME/DGNSS mode
   ### Solution
   - On the top left of the U-center software select *view -> Message view*.
   - The message tab will get opened.
   - In the Messages tab go to  *UBX -> NAV -> PVT*
   - ![add photo of enabling the the column]

### Errors faced in common
1. During the firmware update faced a Exit code 2 error when updating firmware.  
    ``` 
    1.2 - Retry poll
   
    2.2 - Retry poll
   
    3.2 - Retry poll

    3.2 ERROR: Version poll failed.

    3.2 Firmware Update FAILED

    Firmware Update Utility has unexpectedly terminated

    Exit code (2)
    ```

   Solution
   - Connect the USB-B type cable to **USB GPS** port and not in **USB XBEE**.
   - If its not cleared then try the **Updating over USB** section in the video [How to update the firmware on u-blox GNSS receivers](https://youtu.be/lqZ1wTd9gKU?si=oB4lXuNcgepNKxc9).
