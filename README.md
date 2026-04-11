# sodiumFlashlight
documenting my work in creating a 3s 18650 sodium battery powered LED flashlight

# Charging
it's harder to find information on sodium ion cell charging behavior. It's likewise hard to find charge controllers and BMS chips that are suitable for sodium cells' lower discharge and charge thresholds. The Sriko cells in particular have a safe discharge threshold near 2.0V, which is dangerously low for lithium cells. They also have a 4.0V charge cutoff voltage, which means a charge controller for my project should ideally cut them off below the common lithium charge cutoff voltage of 4.2V. However, since sodium ion battery chemistry is generally more thermally stable than lithium, it's unclear how important this truly is. For my purposes, it's important to know how much discharge capacity is left below the common lithium discharge threshold of 2.5V and how the cells will be damaged if regularly charged to 4.2V. It's basically clear that the batteries will still be safe when overcharged regularly, but not whether they'll last long.

After that, i can decide if i can use an off the shelf BMS or have to design one using a BMS IC. It's unclear again which BMS ICs could be used for this purpose, as they will not all have the same flexibility; some may have adjustable charge/discharge cutoff voltages, currents, etc and some may not.

I considered using a TP4056 for this project, but the charge cutoff voltage is too high.
