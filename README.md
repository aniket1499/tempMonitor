# A μC based Room Temperature Monitoring System

Monitoring the temperature of a computer server room is a critical task to ensure the performance of the server is not disturbed by excessive room temperature. We designed and implemented a microcontroller-based room temperature monitoring system using Atmel AT89C51 microcontroller and National Semiconductor's LM35 temperature sensor. The system is equipped with an electronic alarm system. The experiment results show that our system works as expected. The system raises an alarm when the room temperature is above threshold, which is 28°C.

Generally, the daily computer server room's temperature is affected by several factors such as, the server room size, number of server inside the room, and the room's air conditioning system. Nevertheless, a system that capable to warn the server administrator regarding the server room temperature will be very useful in case of there is any excessive temperature.

# Background
## AT89C51 Microcontroller
![8051 Block Diagram](https://aninditadhikary.files.wordpress.com/2011/01/8051blockdiagram.png?w=712)

  The AT89C51 provides the following standard features: 4K bytes of Flash, 128 bytes of RAM, 32 I/O lines, two 16-bit timer/counters, a five vector two-level interrupt architecture, a full duplex serial port, on-chip oscillator and clock circuitry. In addition, the AT89C51 is designed with static logic for operation down to zero frequency and supports two software selectable power saving modes. The Idle Mode stops the CPU while allowing the RAM, timer/counters, serial port and interrupt system to continue functioning. The Power-down Mode saves the RAM contents but freezes the oscillator disabling all other chip functions until the next hardware reset.
  
  ## LM35 Temperature Sensor
  
  ![LM35 Sensor](http://i.imgur.com/1oBVcy1.png)
  
  The LM35 is a temperature sensor, whose output voltage is linearly proportional to the Celsius temperature. This sensor has linear output and low output impedance make it easy for connecting it to the readout circuitry [2]. Three pins, +Vs, GND, and Vout are defined for the sensor. When used as a basic temperature sensor (2°C to 150°C), any change in temperature by 1°C will be converted to 10 mV or the output voltage (Vout) = 0 mV + 10 mV/°C.
  
  ## ADC 0804
  ![ADC 0804](http://www.circuitstoday.com/wp-content/uploads/2012/09/adc0804-pinout.png)
  
  ADC0804 is an 8 bit successive approximation analogue to digital converter from National semiconductors. The features of ADC0804 are  differential analogue voltage inputs, 0-5V input voltage range, no zero adjustment, built in clock generator, reference voltage can be externally adjusted to convert smaller analogue voltage span to 8 bit resolution etc. The pin out diagram of ADC0804 is shown above.
  
  The voltage at Vref/2  (pin9)  of ADC0804 can be externally adjusted  to convert smaller input voltage spans to full 8 bit resolution. Vref/2 (pin9) left open means input voltage span is 0-5V and step size is 5/255=19.6V. Have a look at the table below for different Vref/2 voltages and corresponding analogue  input voltage spans.
  
  ![table](http://1.bp.blogspot.com/-Cm5-xRz7kwc/Te-m7NFvsrI/AAAAAAAADC8/NHn58EJapGk/s400/ADC0804%2BChip%2Bstep%2Bsize%2Bcalculation%2BADC0804%2Bhas%2Bresolution%2Bof%2B8%2Bbits.jpg)
  
  We've connected pin9 to 1.28V to match the step size of ADC to that of the LM35 Senor(10 mV).
  
  **Dout = Vin / step size** 
  Where Dout is digital data output in decimal, Vin = analog input voltage and step size (resolution) is the smallest change. 
  
  >I've uploaded the complete C program, feel free to 
  >reach out to me if you've any questions. I've also uploaded
  > Proteus simulation files, so you can have a better understanding
  >of the project.
  
  ### Hers's a screen grab from my simulations.
  ![monitorSim](https://github.com/aniket1499/tempMonitor/blob/master/screenGrab.png?raw=true)
  
  You'll find a high quality version [here.](https://github.com/aniket1499/tempMonitor/blob/master/monitorSim.BMP) 
