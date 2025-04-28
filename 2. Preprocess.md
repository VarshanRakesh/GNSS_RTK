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
