# GNSS_RTK

## The repository explains about the setting up GNSS-RTK using the Ardusimple SimpleRTK2b series of boards
### Introduction
We are setting up the GNSS base station at initial and make the base station to send correction messages through RFD radio modems.
The RFD modems send the data from base to rover in a certain net id and air data rate
The moving base receive the data from the base station and send to rover board along with a heading. we can get the GPS_FIX and orientation in rover board.

### Firmware Update on simplertk2b boards
From the below website 
> https://www.ardusimple.com/how-to-configure-ublox-zed-f9p/#elementor-toc__heading-anchor-4
Do
