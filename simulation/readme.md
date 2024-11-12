# LTspice Simulation Files
## quick start
1. download LTspice from [Analog Devices](https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html)
2. clone this repository
3. open LTspice and open the `.asc` file you want to simulate
4. run simulation
5. use probe to check the result
## List
* LTC6752_linear_discharge.asc
  * for simulation of linear discharge charge to digital converter(QDC) circuit
  * use ADA4891 as pre amplifier
  * use LTC6752 as comparator
  * use current source as input signal
* LTC6752_TOT.asc
  * for simulation of time over threshold(TOT) charge to digital converter(QDC) circuit
  * use ADA4891 as pre amplifier
  * use LTC6752 as comparator
  * use current source as input signal
* LTC6752_TOT_withbuffer.asc
  * for simulation of time over threshold(TOT) charge to digital converter(QDC) circuit
  * use ADA4891 as pre amplifier
  * use LTC6752 as comparator
  * use current source as input signal
  * use buffer to drive the linear discharge 