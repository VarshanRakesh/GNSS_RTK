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

