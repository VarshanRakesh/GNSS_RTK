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
