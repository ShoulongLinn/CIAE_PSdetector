# SiPM readout electronics
## Detector
* there are 3 boxes
* each box have 2 layers scintillator, they are located in x,y direction.
* each layer have 10 modules, each module have 4 scintillator bars
* each scintillator bar have 1 SiPMs
* we have 3 * 2 * 10 * 4 = 240 Scintillator and SiPMs in total
## Basic connection
* each layer connect to one FEE and FPGA board
* each FEE and FPGA board have 64 channels,but we only use 40 channels
* each box have 2 FEE and FPGA board
* The FEE and FPGA board get CLK from DAQ and use LVDS send data to DAQ
* One DAQ get 3 boxes data and send to PC
* we can set the coincidence mode and coincidence window in DAQ by configure the switch on the board

<img src="Top.drawio.svg" width=100%>

## SiPM board
* each SiPM board have 4 SiPMs
* each SiPM have 2 signal output, one is positive, one is negative
* SiPM board get HV from connector

<img src="Sipmboard.drawio.svg" width=100%>

## Connector board
* each connector board connect to 10 SiPM board
* connector get the cathode signal from SiPM board and send to FEE board
* connector get the anode signal from SiPM board but send it to GND
* connector get the HV from FEE board and send it to SiPM board

<img src="Connector.drawio.svg" width=100%>

## FEE (front end Electronics)
* each FEE board have 64 channels, we use 40 channels
* FEE get the cathode signal from connector board, get the HV from DC Voltage source.
* FEE get discharge signal from FPGA board and send the pulse to FPGA board

<img src="FEE.drawio.svg" width=100%>

## FPGA board
* each FPGA board have 64 channels, we use 40 channels
* FPGA get the pulse from FEE board and use inner LVDS comparator compare the pulse with threshold, and get the digital signal
* we can adjust the threshold by change the register of DC/DC circuit in FPGA board. usually we set the threshold to 0.2V
* FPGA get the CLK from DAQ board and send the data to DAQ board
* all parameters and feature can be find at "discharge_time_digitalize.v" file

<img src="FPGAboard.drawio.svg" width=100%>

## DAQ (Data Acquisition)
* each DAQ board can get data from 16 FPGA board but now we only use 6 FPGA board
* DAQ board get the data from FPGA board, send CLK to FPGA board, compress data and send to PC by UART
* we can set the coincidence mode and coincidence window in DAQ by configure the switch on the board

<img src="DAQ.drawio.svg" width=100%>
