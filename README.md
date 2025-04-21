### Setting up Simplertk2b Budget Board as a Base station:
1. Update the firmware
   - Connect the Simplertk2b budget board to GNSS Survey antenna using the antenna cable given. Refer the **GPS/GNSS Antenna** section to setup the antenna in the website [User Guide: simpleRTK2B Budget](https://www.ardusimple.com/user-guide-simplertk2b-budget/#elementor-toc__heading-anchor-11).
   - Connect the the USB-B type cable to **USB GPS** port in the board and other end to the PC.
   - Open the U-center and connect the budget board with the suitable COM port and set the baud rate to 115200.
   - Download the firmware from the [FW Version 1.32](https://drive.google.com/file/d/1vGNgYuJrV6BfyxmUxkQAvwy2_Sb4ySH0/view?usp=sharing).
   - Or you can find the firmware in their official website [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-4) go to **Firmware version check** section download the **Version 1.32**. Extract the file in separate folder.
   - And follow the **Firmware update** section to update the firmware and cross check that the version updated correctly with the **Firmware version check** section found in the same website.

2. Loading the base station configurations on the budget board.
   - Download the base station file for the FW 1.32 version from the [add Base station configuration file].
   - Before loading the configuration files recheck that you are uploading the correct file. uploading an incorrect file might lead to problems
   - Load the configuration to the budget board referring the **Load a configuration file** section in [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-6)
   - Go to View > Messages View
   - ![base station message view](https://github.com/user-attachments/assets/1cf4463a-9c48-4568-9c6d-1f2858e926c3)
   - In message view go to UBX-CFG-TMODE3 and select Mode 1 – Survey-in
   - ![base station cfg](https://github.com/user-attachments/assets/d971613f-5dc3-41f8-9690-1bc66a019fba)
   - ![base station set time and accuracy](https://github.com/user-attachments/assets/257ee693-ea4e-46fc-9871-4987eaf0e3cd)
   - Set Minimum Observation Time and Required Position Accuracy, default values are a good start.
   - I have set my observation time to 0 seconds and 0.5m accuracy.
   - Be careful to don’t put a required accuracy too low because you may never reach it.
   - Click Send button.
   - Go to View > Messages View > UBX-NAV-SVIN
   - ![base station nav](https://github.com/user-attachments/assets/77b9fdaf-92c1-4664-85c4-9869ddf9ff9d)
   -  check whether the **Status** is successfully finished, **mean position valid** parameter shows yes, ECEF X, ECEF Y, ECEF Z values got and right side pane show **fix mode** to **TIME or TIME/DGNSS**.
   - ![base station survey in tab](https://github.com/user-attachments/assets/d8f8d5cb-c771-48f2-9b51-6e46faf166f8)
   - Then note the ECEF X, ECEF Y, ECEF Z values to the notepad.
   - Now Go to View > Messages View > UBX-CFG-TMODE3 and select Mode 2 - Fixed mode.
   - ![base station fix mode](https://github.com/user-attachments/assets/d9008159-d161-4704-b102-9fc0a802fc41)
   - Copy and paste the ECEF X, ECEF Y, ECEF Z values to X, Y, Z respectively and set the accuracy to 0.5m.
   - Click Send button.
   - And follow **Save the configuration** section in the [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-6) to store the configuration to the board permenantly.
   - Follow the **Create a configuration file** section in the same website to update the changes you have made in the configuration of the board to an existing configuration file in the PC.

3. Configuration file not available
   - If the configuration file has not available, download the **base configuration** file for the FW 1.32 version in [Base station configuration](https://drive.google.com/file/d/1pdjuG0cN3bo1yQ5i_762ryBFAblOVWsm/view?usp=sharing) or it's also available from the **Examples of configuration file** section in their official website [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-9).
     ![downloading base station configuration](https://github.com/user-attachments/assets/e2c499a5-1bc1-4e96-95db-28e91d0d35c2)
   - Before loading the configuration files recheck that you are uploading the correct file. uploading an incorrect file might lead to malfunctions.
   - Load the configuration to the budget board referring the **Load a configuration file** section in [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-6)
   - On the top left of the U-center software select **view -> Message view**.
   - The message tab will get opened.
   - ![base station message view](https://github.com/user-attachments/assets/6caf81e6-df4b-45f2-a4eb-7ac45118f940)
   - Go to View > Messages View > UBX-CFG-TMODE3 and select Mode 1 – Suvey-in
   - ![base station cfg](https://github.com/user-attachments/assets/9b5ab99f-ed6b-4481-ba66-0c83df54ee36)
   - Set Minimum Observation Time and Required Position Accuracy, default values are a good start.
   - ![base station set time and accuracy](https://github.com/user-attachments/assets/f6743e32-636d-47ef-9b2b-b04eb6a601cb)
   - I have set my observation time to 0 seconds and 0.5m accuracy. 
   - Be careful to don’t put a required accuracy too low because you may never reach it.
   - Click Send button.
   - Go to View > Messages View > UBX-NAV-SVIN
   - ![base station nav](https://github.com/user-attachments/assets/77b9fdaf-92c1-4664-85c4-9869ddf9ff9d)
   -  check whether the **Status** is successfully finished, **mean position valid** parameter shows yes, ECEF X, ECEF Y, ECEF Z values got and right side pane show **fix mode** to **TIME or TIME/DGNSS**.
   - ![base station survey in tab](https://github.com/user-attachments/assets/d8f8d5cb-c771-48f2-9b51-6e46faf166f8)
   - Then note the ECEF X, ECEF Y, ECEF Z values to the notepad.
   - Now Go to View > Messages View > UBX-CFG-TMODE3 and select Mode 2 - Fixed mode.
   - ![base station fix mode](https://github.com/user-attachments/assets/d9008159-d161-4704-b102-9fc0a802fc41)
   - Copy and paste the ECEF X, ECEF Y, ECEF Z values to X, Y, Z respectively and set the accuracy to 0.5m.
   - Click Send button.
   - Now go to View > Messages View > UBX-CFG-MSG and select the **F5-05 RTCM 3.3 1005** and ensure its only enabled in **UART 2** checkbox.
   - ![base station 1005](https://github.com/user-attachments/assets/8925be7b-1dc6-4fc2-8921-20d6e5e27c8b)
   - ![base station set 1005](https://github.com/user-attachments/assets/1025df98-559f-4f86-9d09-d4e9bb6cc319)
   - First to disabling the MSM4 messages and then enable MSM7 messages to connect with the rover which have MSM7 messages
   - Select the **F5-4A RTCM 3.3 1074** and disable in all checkboxes including UART 2 and USB checkbox and click send.
   - ![base station set 1074](https://github.com/user-attachments/assets/15e1f034-1f3a-43fa-a50e-e683da2677fd)
   - Select the **F5-54 RTCM 3.3 1084** and disable in all checkboxes including UART 2 and USB checkbox and click send.
   - ![base station set 1084](https://github.com/user-attachments/assets/c5bdfbfa-2f06-4856-9ee7-b94e5bf13e45)
   - Select the **F5-5E RTCM 3.3 1094** and disable in all checkboxes including UART 2 and USB checkbox and click send.
   - ![base station set 1094](https://github.com/user-attachments/assets/4dbb8dcf-e0e6-4867-9965-185dbbb7c3d8)
   - Now enabling the MSM7 messages.
   - Select the **F5-4D RTCM 3.3 1077** and ensure its only enabled in UART 2 and click send.
   - ![base station set 1077](https://github.com/user-attachments/assets/19341e90-f9e2-4533-86d0-4c8db3c4efa8)
   - Select the **F5-57 RTCM 3.3 1087** and ensure its only enabled in UART 2 and click send.
   - ![base station set 1087](https://github.com/user-attachments/assets/2c808814-eb83-4ea2-bea8-3ed6ebe7a924)
   - Select the **F5-61 RTCM 3.3 1097** and ensure its only enabled in UART 2 and click send.
   - ![base set 1097](https://github.com/user-attachments/assets/4470149c-4534-4213-9527-c089d6504275)
   - Select the **F5-E6 RTCM 3.3 1230** is only enabled in UART 2 and click send.
   - ![base set 1230](https://github.com/user-attachments/assets/7d8d6527-65a2-482e-937a-16e79c5ee308)
   - Now go to **View > Messages View > UBX-CFG-PRT** and change the target parameter to 2 - UART2.
   - ![base station port](https://github.com/user-attachments/assets/4c5b2178-2850-4307-aa76-a862d34bd2d4)
   - Change the **Protocol in** parameter to none.
   - Change the **Protocol out** parameter to 5 - RTCM3.
   - Set the baud rate to 115200 and then click send.
   - ![base station port value](https://github.com/user-attachments/assets/ba19358c-2b14-40fe-aebc-8935531d2ac7)
   - Now go to **View > Messages View > UBX-CFG-RATE** and let the time source to be in 1 - GPS time.
   - ![base station rate](https://github.com/user-attachments/assets/ec15f905-b0a6-4e9b-b207-3eeec0f24a1a)
   - Set the **measurement period** to 100 [ms] to make the frequency to 10 hz and click send.
   - ![base station rate value](https://github.com/user-attachments/assets/d31deed8-3b29-4301-ae1d-2d3ffb3ba136)
   - Go to **UBX-CFG-CFG** and save the configurations.
   - ![base save 1](https://github.com/user-attachments/assets/b3d0ed5f-2ade-4fdf-bcdd-836a3a7aba44)
   - On left top of the U-center app select the **Receiver > Action > Save config** to store the changes made in the board permenantly to the board.
   - ![base station save 2](https://github.com/user-attachments/assets/da2916e1-ce43-43f3-a194-02a3abd95d5a)
   - Wait till more than 2 to 3 hours to get the **TIME or TIME/DGNSS mode**.

4. Connecting the RFD modem to the budget board to send the data over radio
   - Connect the **V Standard pin** of the RFD modem to **5V_OUT** pin of Budget board and **GND pin** of the RFD modem to **GND pin** of the Budget Board
   - Connect the IOREF pin of the Budget board to **3V3_OUT** pin so that the uart pins work on 3.3V power
   - Connect the **TX pin** of the RFD modem to the Budget board's **TX2 pin** and **RX pin** of the RFD modem to the Budget board's **RX2 pin**
   - The same is done below for the reference.
     
     ![RFD to Gnss receiver connection](https://github.com/user-attachments/assets/ca8878b5-2687-4d59-820e-4115fc0404e1)
   
### Errors faced when setting up base station
1. If the base station is not changed to TIME or TIME/DGNSS mode
   ### Solution
   - On the top left of the U-center software select **view -> Message view**.
   - The message tab will get opened.
   - ![base station message view](https://github.com/user-attachments/assets/3bbc621b-69e9-4f27-9fc4-0b6de5ef5ef5)
   - In the Messages tab go to  **UBX -> NAV -> PVT** and select the column and enable it
   - ![base ubx nav pvt](https://github.com/user-attachments/assets/c1c9f46c-c439-46c6-bd00-4da1a5285d0e)
   - In right side of the app the **fix type** column changed to TIME or TIME/DGNSS mode.
     
### Setting up Simplertk2b Lite Board as a Heading kit moving base:
1. Updating the firmware
   - Before configuring the rover board at the bottom, we should configure lite board on the top.
   - Fix the lite board on top of the rover board as per the below photo.
     
     ![Simplertk2b heading kit](https://github.com/user-attachments/assets/96cdb716-ac18-4500-a675-4b64526b06ba)
     
   - Connect the antenna to the SMA connector of the both top lite board and bottom rover board.
   - Connect the the USB-B type cable to **USB XBEE** port in the board and other end to the PC.
   - Open the U-center and connect the lite board with the suitable COM port and set the baud rate to 115200.
   - Download the firmware from the [FW Version 1.32](https://drive.google.com/file/d/1vGNgYuJrV6BfyxmUxkQAvwy2_Sb4ySH0/view?usp=sharing).
   - Or the firmware can also found in the website [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-4) go to **Firmware version check** section download the **Version 1.32**. Extract the file in separate folder.
   - And follow the **Firmware update** section to update the firmware and cross check that the version updated correctly with the **Firmware version check** section found in the same website.
  
2. Loading the configurations as Moving base of the heading kit
   - Download the moving base for the FW 1.32 version from the [add moving base file].
   - Before loading the configuration files recheck that you are uploading the correct file. uploading an incorrect file might lead to problems
   - To load the configuration to the lite board refer the **Load a configuration file** section in [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-6)
   - And follow **Save the configuration** section in the [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-6) to store the configuration to the board permenantly.
   - Follow the **Create a configuration file** section in the same website to update the changes you have made in the configuration of the board to an existing configuration file in the PC.

3. Configuration file not available
   - If the configuration file has not available download the **lite board configuration** file in the [moving base configuration](https://drive.google.com/file/d/17MkmwKJANRGKc4dVwS4mvsxehgPvbiTg/view?usp=sharing).
   - Or you can download the same from the **For 1hz** section, the file besides **On the lite board** in the [simpleRTK2B+heading hookup guide](https://www.ardusimple.com/simplertk2heading-hookup-guide/). Right click on the file and select **save it as** option to save in the browsed folder.
   - On the top left of the U-center software select **view -> Message view**.
   - The message tab will get opened.
   - ![base station message view](https://github.com/user-attachments/assets/c564d676-8c07-4c56-8af2-942eec433fb7)
   - Double click the UBX and under UBX double click the CFG.
   - ![rover ubx](https://github.com/user-attachments/assets/b8cd1dba-a454-495f-8bab-9711391cdf0d)
   - ![rover ubx cfg](https://github.com/user-attachments/assets/f39849ca-ac06-4b15-8b64-221dedde35ff)
   - Go to **UBX-CFG-RATE** and change the frequency from 1 hz to 10 hz by reducing the 1000 ms to 100 ms time period.
   - ![rover rate](https://github.com/user-attachments/assets/8a9fbb5c-e871-4837-a1bf-98d601c983ad)
   - Click the **send** button.
   - Now save the configuration by **UBX-CFG-CFG** tab and select the save configuration button and click **send** button.
   - ![rover save](https://github.com/user-attachments/assets/650671cd-3801-4c89-92e9-85478597b05f)
   - And follow **Save the configuration** section in the [How to configure u-blox ZED-F9P](https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-6) to store the configuration to the board permenantly.
   - Follow the **Create a configuration file** section in the same website to update the changes you have made in the configuration of the board to an existing configuration file in the PC.

### Errors faced when setting up lite board in heading kit as moving base
1. This is the half of the heading kit configuration so we check for errors once the Rover board configurations got completed.
   
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

