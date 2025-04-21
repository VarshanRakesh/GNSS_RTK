## The repository explains about the setting up GNSS-RTK using the Ardusimple SimpleRTK2b series of boards

### Introduction
- We are setting up the GNSS base station at initial using the budget board. This is the Budget board

  ![simplertk2b budget board](https://github.com/user-attachments/assets/b807ac37-eae4-4cc2-8e28-fef1fd5fbf99)
- Then Connecting RFD modem through UART to send RTCM correction data to rover. This is the RFD modem
  
  ![RFD868ux-IND-front__final__15890](https://github.com/user-attachments/assets/4a53a70a-9866-4807-a62a-9a0e2c1457cc)

- The RFD modems send the data from base station to heading kit in a certain net id and air data rate which will be set previously.
- The lite board receive the data from the base station and send to rover board along with a heading.
  
  ![Simplertk2b lite board](https://github.com/user-attachments/assets/e7f0cacd-eeb9-4d08-a664-d0d6a03a9588)
- The lite board fixed on top of rover board makes a heading kit

  ![Simplertk2b heading kit](https://github.com/user-attachments/assets/58be5a0c-ab2e-406e-9e24-eb5bf64ed94e)
- We can get the **GPS_FIX** and **Orientation** from the **USB GPS** port in the rover board

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
5. 2 x USB-B type cables
6. 1 x [RFD868ux-IND Modem Bundle](https://store.rfdesign.com.au/rfd868ux-ind-modem-bundle-hs-8517-62-00-90/)
7. Enough amount of M-F and F-F jumper wires
8. Check whether all the products available as per the product links

### Preprocess

#### Configure the RFD Modems
1. Connect the FTDI cable to the RFD modem for configuring RFD modems.
2. This is the photo of connecting RFD to **FTDI cable**. The 8 wires connector in the middle is the **900ux to 8 way socket cable**. Check with the colour combination of the **FTDI cable** and the **900ux to 8 way socket cable** is as per the photo

![RFD connection for configuration](https://github.com/user-attachments/assets/90f7dc57-12ab-4e51-95fe-c59e86349595)  

like the left most pin in the rfd is the **GND pin** and it should connected with the black colour wire of the **FTDI cable**.
4. I have set the RFD modems to below configurations  
5. My configurations of the RFD modems 

   ![My RFD configurations](https://github.com/user-attachments/assets/63b74cba-377e-444d-9d1d-3558e8c2ea4a)

6. Remove the **900ux to 8 way socket cable** from the rfd modem and connect it to the another modem and repeat the same steps from 1 to 4 to other rfd modem also.
7. The RFD configurations of the both modems should be same to make the communication properly.

#### Checking the communication has established perfectly
1. The RFD pins and description of the pins are attached here

   ![Rfd_pins](https://github.com/user-attachments/assets/4fcf9f51-e921-42a2-b6e9-429dfd42b9db)
   
   and
   
   ![Rfd_pins_description](https://github.com/user-attachments/assets/d739b9fe-79fe-4e73-87a6-c7af716d7cfc)
   
3. Dump a general **UART transmitter** code which is below                                                                                            
      ```
    void setup() {
    Serial.begin(115200);  // Set your desired UART baud rate
    }

    void loop() {
    // Dummy RTCM-like binary message (starts with 0xD3, length 0x13)
    uint8_t rtcmMessage[] = {
    0xD3, 0x00, 0x13,      // Header: preamble + length (19 bytes)
    0x3E, 0xF0,            // Message Number (1005 example)
    0x00, 0x00, 0x00, 0x00, 0x00,             // Station ID, IOD
    0x20, 0x00, 0x00, 0x00, 0x00, 0x00,       // ECEF X
    0x20, 0x00, 0x00, 0x00, 0x00, 0x00,       // ECEF Y
    0x20, 0x00, 0x00, 0x00, 0x00, 0x00,       // ECEF Z
    0xAB, 0xCD, 0xEF                          // Fake CRC
    };

    Serial.write(rtcmMessage, sizeof(rtcmMessage)); // Send binary message

    delay(1000); // Wait a bit before sending again
    }
   ```
  with a baud rate of 115200 in one of the arduino  without connecting the TX pin and RX pin.
4. Then, connect the **UART pins** of the RFD modem to **UART pins** of the Arduino as per below
   
5. ![rfd_debugging](https://github.com/user-attachments/assets/e1702fe5-083a-4902-823a-82548155d44a)
   
   - **V Standard pin** of RFD modem -> **5V pin** of Arduino
   - **TX pin** of RFD modem -> **RX pin** of Arduino
   - **RX pin** of RFD modem -> **TX pin** of Arduino
   - **GND pin** of RFD modem -> **GND pin** of RFD modem
   and disconnect the transmitter arduino board.

7. In another arduino make the connection as per below because of the wires are twisted and header is added.
8. ![rfd modem to receiver arduino](https://github.com/user-attachments/assets/d2ffea63-6fec-487c-a5aa-92bb290c28fa)
9. Dump a general **UART receiver** code with the same baud rate in another arduino board without connecting the TX and RX pin
10. Here is the **UART receiver** code
   ```
     void setup() {
     Serial.begin(115200);  // For Serial Monitor
     Serial.println("Ready to receive RTCM binary data...");
     }

     void loop() {
      while (Serial.available()){
      uint8_t byteReceived = Serial.read();

      // Print as 2-digit HEX
      if (byteReceived < 0x10) Serial.print("0");
      Serial.print(byteReceived, HEX);
      Serial.print(" ");
      }
    }
   ```
11. Now connect the transmitter board with RFD modem connected to TX and RX pin and next connect the receiver board with RFD modem connected to TX and RX pin.
12. When you open the serial monitor of the transmitter arduino you may find this data
13. ![rfd transmitter serial](https://github.com/user-attachments/assets/285c71c1-a6ba-41ca-bea3-87cee9c8f350)
14. Since write() function doesn't print data on serial monitor you can't verify it in serial monitor of the transmitter arduino.
15. But if you have checked the data on the receiver side you can find the RTCM message which sent from the transmitter.
16. ![rfd receiver serial](https://github.com/user-attachments/assets/4c9b51f8-43a0-4669-8085-28d02da4b0f7)
17. Check whether data is received in the receiver arduino in serial monitor. Set the serial monitor with the same baud rate to get the data received.
18. If no data found in the transmitter arduino and receiver arduino or check the wiring or change the baud rate or change the COM port or close and open the serial monitor or finally change the code
