# Observer
Observer is a device that measures the altitude, acceleration, rotation, and location of model rockets. 

As of March 10, 2020, Observer's schematic is incomplete. It uses the following chips:
-STM32L151C8T6A   (Processing)
-MPU-6050         (Rotation and low-acceleration measurements)
-LPS25HBTR        (Pressure-based altitude measurements)
-ADXL375          (High-acceleration measurements)
-GD25Q16CSIG      (Temporary data storage)

What might eventually happen:
-The addition of a micro-sd slot to transfer data once it is safe to do so (OR) the replacement of the GD25Q16CSIG chip with a higher-capacity chip and the addition of a USB port for pulling data from it
-The addition of a GPS module for transmitting coordinates during descent and after landing
-The addition of a Wireless module for transmitting GPS data to aid in recovering the rocket.
