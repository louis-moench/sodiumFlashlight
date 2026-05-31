# sodiumFlashlight
documenting my work in creating a 3s 18650 sodium battery powered LED flashlight

# why sodium?
a few years ago at my university something happened, what specifically i am not sure, involving student lithium-ion projects that spooked some people. sodium-ion is a similar technology with lower fire potential and hence is suitable for experimentation in a less tightly controlled environment (i.e. educational settings). it makes sense to at least have the option to use sodium in these contexts.

# Charge controller and BMS
it's harder to find information on sodium ion cell charging behavior. It's likewise hard to find charge controllers and BMS chips that are suitable for sodium cells' lower discharge and charge thresholds. The Sriko cells in particular have a safe discharge threshold near 2.0V, which is dangerously low for lithium cells. They also have a 4.0V charge cutoff voltage, which means a charge controller should ideally cut them off below the common lithium charge cutoff voltage of 4.2V. Desplite the fact that sodium ion battery chemistry is generally more thermally stable than lithium, independent informal experiments suggest that sodium cells degrade heavily when repeatedly overcharged beyond 4.0V.

Off the shelf BMS chips are either nonconfigurable or not configurable to the ideal voltage range of a sodium 18650. Charge controllers are the same. Thus it is necessary to implement a charge controller and BMS for sodium battery chemistry's ideal conditions. the STM32 is an industry ready platform available with the multiple analog-digital converters necessary to monitor multiple cell voltages and currents.
