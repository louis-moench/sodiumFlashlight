# sodiumFlashlight
documenting my work in creating a 3s 18650 sodium battery powered LED flashlight

# why sodium?
sodium-ion is a similar battery chemistry to the ubiquitous lithium ion with lower fire potential and hence is suitable for experimentation in a less tightly controlled environment than lithium (i.e. educational settings). it makes sense to at least have the option to use sodium in these contexts. when you don't absolutely need the maximum possible power density, and safety and fire risk would be a headache with lithium, sodium should be available.

# Charge controller and BMS
it's harder to find information on sodium ion cell charging behavior. It's likewise hard to find charge controllers and commercially available BMS chips that are suitable for sodium cells' lower discharge and charge thresholds. The Sriko cells i have at my university in particular have a safe discharge threshold near 2.0V, which is dangerously low for lithium cells. They also have a 4.0V charge cutoff voltage, which means a charge controller should ideally cut them off below the common lithium spec of 4.2V. Desplite the fact that sodium ion battery chemistry is generally more thermally stable than lithium, independent informal experiments suggest that sodium cells degrade heavily when repeatedly overcharged beyond 4.0V.

Off the shelf BMS chips are either nonconfigurable or not configurable to the ideal voltage range of a sodium 18650. Charge controllers are the same. Thus it is necessary to implement a charge controller and BMS for sodium battery chemistry's ideal conditions. the STM32 is an industry ready platform available with the multiple analog-digital converters necessary to monitor multiple cell voltages and currents.
