We are using these Sriko cells https://srikobatteries.com/product/sodium-ion-18650-3-0v-1-3ah-3-90wh-20c-rechargeable-battery/ https://srikobatteries.com/wp-content/uploads/2023/12/18650-User-Manual.pdf

They have a low voltage cutoff of 2v and a high voltage cutoff of 4v. They have a capacity of 1200mAh.

They have a standard charge and discharge current of 650mA. However, they have a maximum charge current of 3.9A up to 3.95V and 2.6A up to 4V after that. Maybe we can do triple the standard charge current, 1950mA or 1.625C. This means we would get from 0 to 100% SOC in 37 minutes. We can test this method once we have the device constructed. For now we will program the BMS to charge at the standard charge current, 650mA.

key electrical parameters:
3s configuration of 3.7V (2.0-4.0V) sodium-ion cells with 650mA per cell standard discharge current
standard charge current of 650mA
max charge current of 2.6A
max discharge current of 13A

What FET to use?
i would like to use a nice one to flex. but i wont, because that's not cool.
I'll use some that can deliver 400mA constant current and stop 26A (since these cells can deliver that much at inst. max discharge).
Maybe i'll use ao3400a FET

so, i ultimately decided not to use any TI chip and just do it all with an STM32. It shouldn't be too hard since it's just three cells, overcurrent, overvoltage in charge, undervoltage in discharge
you have to measure the current in and out of the cells, and the easiest way to do this is with a current sensing resistor for each cell. problem is you need to amplify the voltage drop before handing it to ADC; some methods are to use op amps, or the INA219 from TI that does the whole thing and shoots it over i2c. (you need one INA for each measurement...)
