# Observer
Observer is a device that measures the altitude, acceleration, rotation, and location of model rockets. 

As of June 24, 2022, Observer's schematic is complete-ish but untested. It uses the following chips:
- SAMD21G18   (Processing)
- USB-C port (data transfer
  + Protection IC (can be omitted) 
- ISM330         (Rotation and low-acceleration measurements)
- BMP390        (Pressure-based altitude measurements)
- ADXL375          (High-acceleration measurements)
- Micro SD card      (Temporary data storage)
- Ublox MAX M8     (GPS)
  + External LNA
- RFM97C         (LoRa Radio tranceiver)
- PCA9685PW     (LED driver, used as motor driver.)

Future changes (maybe):
-Change the pogo pin pads to headers for easier debugging, and the JTAG pads to
a full JTAG connector.
-Change the logo on the back of the PCB because I won't be using it for the TARC 
competition anymore. 
-Remove the USB-C anti-static protection IC, because it costs money and is most
likely useless.
-Remove a lot of decoupling caps, because I don't really need them
-Find a better way of controlling the servo motors, maybe through connecting them
to GPIO and using a level shifter

**Notes:**

As of June 24th, 2022 the design has not been fully validated. I don't have a 
JTAG debugger and I can't get one right now, so I cant upload a bootloader to upload
code over USB. From what I can tell the voltages look fine and the power management 
works perfectly, but I have not been able to test anything else. Plus, since most of
the schematic is based on reference designs, I see no reason why things *shouldn't*
work. 

To build this for myself I substituted the ISM330 with its non-industrial variant, the
LSM6DSO32. In retrospect I realize that the ISM330 was overkill, and using the LSM6DSO32 
makes the secondary high-g accelerometer redundant in most use cases, since the LSM6 can
already go up to 32G. So, if you're looking to build this for yourself, just get the LSM6
and skip the ADXL375, it will save you ~12 bucks. 

More retrospect: the LNA is probably also not very useful, since when used with
rockets the GPS basically has clear view of the sky with very little blocking the signal, 
apart from maybe the rocket casing, but that's insignificant. If you're building this for yourself, 
you can omit the LNA, but MAKE SURE you change the schematic and board layout so that 
the gps module connects directly to the u.fl connector. The GPS will not work otherwise. 
The LNA also has some really fine pitch pins, so the risk of shorting contacts 
is pretty high. So be careful!

As for the name, 'observer' is staying for now since I can't really think of anything
else. Suggestions would be much appreciated! 

This project is licensed under the GNU General Public License v3.0.
Please use responsibly. Any military use is forbidden, unless approved by the 
creator (me). 
