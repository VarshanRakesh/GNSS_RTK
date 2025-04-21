### Setting up Simplertk2b Budget Board as a Heading kit Rover board:
1. Updating the firmware
   - After configuring the lite board on the top, remove the lite board from the top of the rover board.
   - Disconnect the USB-B type cable from **USB XBEE** port and connect it to the **USB GPS** port on the rover board at the bottom.
   - Connect the GNSS antenna to the both boards of the heading kit
   - ![rover antenna](https://github.com/user-attachments/assets/391f0f85-e813-491c-8885-e8c61fab1f5b)
   - Open the U-center and connect the rover board with the suitable COM port and set the baud rate to 115200. refer **Connect to u-center** section in [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-4).
   - Download the firmware from the [FW Version 1.32](https://drive.google.com/file/d/1vGNgYuJrV6BfyxmUxkQAvwy2_Sb4ySH0/view?usp=sharing).
   - Or firmware can also found in [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-4) go to **Firmware version check** section download the **Version 1.32**. Extract the file in separate folder.
   - And follow the **Firmware update** section to update the firmware and cross check that the version updated correctly with the **Firmware version check** section found in the same website.
  
2. Loading the configurations as rover of the heading kit
   - Download the rover configuration file for the FW 1.32 version from the [add rover configuration file].
   - Before loading the configuration files recheck that you are uploading the correct file. uploading an incorrect file might lead to problems
   - To load the configuration to the rover board refer the **Load a configuration file** section in [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-6)
   - And follow **Save the configuration** section in the [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-6) to store the configuration to the board permenantly.
   - Follow the **Create a configuration file** section in the same website to update the changes you have made in the configuration of the board to an existing configuration file in the PC.

3. Configuration file not available
   - If the configuration file has not available, download the **rover board configuration** file in the [Rover board configuration](https://drive.google.com/file/d/1-d5m3nyiv6EF2fXdvWtEuJJczOBV59ue/view?usp=sharing)
   -Or you can download the same from the **For 1hz** section, the file besides **On the budget board** in the [simpleRTK2B+heading hookup guide](https://www.ardusimple.com/simplertk2heading-hookup-guide/). Right click on the file and select **save it as** option to save in the browsed folder.
   - On the top left of the U-center software select **view -> Message view**.
   - ![rover messages view](https://github.com/user-attachments/assets/c22de780-be3e-490a-80e5-4749cf096cfe)
   - The message tab will get opened.
   - Go to UBX and under it double click the CFG.
   - ![drover ubx](https://github.com/user-attachments/assets/f1130286-128d-4ddb-b274-4a1913d5eb9f)
   - And check whether the PVT and RELPOSNED message enabled.
   - ![drover pvt relpos](https://github.com/user-attachments/assets/fe421d9c-a6d3-4c74-bcad-fcf28e1a7a5d)
   - Go to **UBX->CFG->RATE** and change the frequency from 1 hz to 10 hz by reducing the 1000 ms to 100 ms time period.
   - ![bottom rover rate](https://github.com/user-attachments/assets/72ad045d-4e6b-48bb-86f4-1bac4cab913b)
   - Click the **send** button.
   - Now save the configuration by **UBX-CFG-CFG** tab and select the save configuration button and click **send** button.
   - ![bottom rover save 1](https://github.com/user-attachments/assets/64f4a669-94c5-4089-be41-431cc518a871).
   - And follow **Save the configuration** section in the [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-6) to store the configuration to the board permenantly.
   - Follow the **Create a configuration file** section in the same website to update the changes you have made in the configuration of the board to an existing configuration file in the PC.

4. Connecting the RFD modem to the heading kit to receive the data over radio
   - Connect the **V Standard pin** of the RFD modem to **5V_OUT** pin of Budget board and **GND pin** of the RFD modem to **GND pin** of the Budget Board
   - Connect the IOREF pin of the Budget board to **3V3_OUT** pin so that the uart pins work on 3.3V power
   - Connect the **TX pin** of the RFD modem to the lite board's **RX pin** and **RX pin** of the RFD modem to the lite board's **TX pin**
   - The same is done below for the reference
      
     ![rfd modem to heading kit](https://github.com/user-attachments/assets/14015897-b7d5-45f0-bba4-22a47cd1061f)

   - After all connections are made in rover the no_rtk led starts to blink and turned off on both of the board within few minutes.

### Errors faced when setting up heading kit
1. If the no rtk led blink on top of the lite board
   ### Solution
   - Configure the lite board first and then the rover board of the heading kit.
   - Confirm the configuration file you have loading is related to the board you're using. And don't mistakenly load the rover's configuration file to the lite board and vice versa.
   - Satellites view might be the cause of this problem.
   - Check whether the wires are working properly.
2. If the the 3D/FLOAT or 3D/DGNSS/FLOAT is in the FIX mode of the right side of the U-center app and no 3D/FIXED or 3D/DGNSS/FIXED appeared
   ### Solution
   - The U-center software shows 3D/FLOAT or 3D/DGNSS/FLOAT and the **no_rtk** led blinks. Wait for a 5 mins to the fix mode changed from 3D/FLOAT or 3D/DGNSS/FLOAT to 3D/FIXED or 3D/DGNSS/FIXED and the **no_rtk** led stops blinking. 
   - if the **no_rtk led** is glows solid, Check whether the TX of the RFD modem is connected to the TX2 of the budget board and RX of the RFD modem is connected to the RX2 of the budget board
   - verify whether the **IOREF** pin is connected to the **3V3_OUT** pin in both the base station and heading kit.
   - And check all of the connections done as per the photos and suitable configurations is loaded to the suitable boards.
   - If no_rtk led glows solid and shows 3D/DGNSS/FLOAT fix mode of the U-center software even after all these steps follow the debugging steps to check data is sending from the base station.

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
  
2. During the loading from file or saving the configuration to file will facing the timeout error
   ![timeout error](https://github.com/user-attachments/assets/d6c4c091-3a6d-4895-8316-bf5accd167a2)
   Solution
   - Connect the USB-B type cable to **USB GPS** port and not in **USB XBEE**.
   - It might be a permission issue Try the following steps one by one two times.
   - Load the configuration with different baud rate.
   - disconnect the com port in the software before removing the cable and connect it again.
   - Try it with different com port with and try again with the different baud rate, try to use the another cable.
   - At final it shows the successfully loaded message.
   - ![load save success](https://github.com/user-attachments/assets/679932b9-ee97-4611-8931-a8a3936c51ec)
   - So that you can proceed further.

### Known errors
1. In ros driver We tried running the ublox driver [GitHub - KumarRobotics/ublox: A driver for ublox gps](https://github.com/KumarRobotics/ublox) to get gps data in ros system. While launching the node I get this error “ERROR: txbuf alloc”. The baudrate is set to 115200.
   Support from forum
   - In ubx-cfg-nmea I change the verbose channel to 16 channel receiver.
     [add photo]
   - At the top-level GSV there you can Right Click to Disable (Child) Messages
     [add photo]
     and we got the final screen as without satellites visibility messages since these messages are not needed for the rover to operate.
     ![final screen after disable satellite visibility](https://github.com/user-attachments/assets/219cf9a5-53ca-4736-9ebf-35d4a8c2f41f)

