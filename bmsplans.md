two potentials ICs:
BQ25185
BQ25306
tutorial https://www.youtube.com/watch?v=6-cEOdpa7dg&list=PLJJ-NKzzRQygLr5ta54anSxbbq5CFP0W2
the above tutorial uses the bq77915, which may be suitable. have to see if it supports 4V or 4.1V cutoff, and what low voltage threshholds it can do
 - yes it does, can do undervoltage from 1.2 to 3v and overvoltage from 3 to 4.575
The 77915 supports 3s.

The 77915 also implements active charging.

The way the 77915 implements overcurrent detection is with some sort of voltage transduction onto a pin, not sure which one.

It has a configurable threshold for cell balancing start, not sure what that means.

Also, we are using these Sriko cells https://srikobatteries.com/product/sodium-ion-18650-3-0v-1-3ah-3-90wh-20c-rechargeable-battery/ https://srikobatteries.com/wp-content/uploads/2023/12/18650-User-Manual.pdf

They have a low voltage cutoff of 2v and a high voltage cutoff of 4v. They have a capacity of 1200mAh.

They have a standard charge and discharge current of 650mA. However, they have a maximum charge current of 3.9A up to 3.95V and 2.6A up to 4V after that. Maybe we can do triple the standard charge current, 1950mA or 1.625C. This means we would get from 0 to 100% SOC in 37 minutes. We can test this method once we have the device constructed. For now we will program the BMS to charge at the standard charge current, 650mA.

The 77915 detects over- and undercurrent in discharge when the voltage across a certain resistor is below a threshold.  
It's configurable to recover from discharge overcurrent when the load is removed, after a timer, or both.

The 77915 detects over- or undervoltage of the cells by measuring it directly.
The 77915 is configurable to only drop for undervoltage when the load is removed.

Discharge overcurrent trip delay is configured by connecting a resistor between pins OCDP and VSS. If you connect a 10k resistor you have to flash the time to EEPROM.

Charge overcurrent is detected when the voltage across a resistor is too high relative to a threshold. 

The chip is configurable to use external balancing FETs but has internal capability up to 50mA balancing current.

The chip disables all charging and shuts down below 1V per cell (in 3S).

The charge and discharge FET rise/fall times are configurable with resistors.

We will need to configure load removal as a condition of undervoltage recovery, since our load is large. This means we need a 3.3MOhm resistor as R_{gs_chg}.

We can add RC filters to the current-sensing resistors for stability, sounds like it's not really necessary as our battery is very stable output V.

key electrical parameters:
3s configuration of 3.7V (2.0-4.0V) sodium-ion cells with 650mA per cell standard discharge current
standard charge current of 650mA
max charge current of 2.6A
max discharge current of 13A


okay we have to use the bq7790508 instead, this has correct cutoff voltages (ch/disch range)
it goes from 2V to 3.9V

to set OCD and OCC we need to choose resistors that will produce 50mV (OCD1) at our current setting, so since 0.050V = (0.65^2)r we use resistor value of 0.05/(0.65^2) = 0.118Ohm
