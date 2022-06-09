# ucb_chip_io
Modification of efabless' `chip_io` padframe with a library of pre-configured IO cells instead of the [caravel](https://github.com/efabless/caravel) harness.

## Library Info

A select number of cells is presented here under the `gds` folder. These include the following cells:

* `chip_io`: This is a direct copy of the `chip_io` padring from the caravel project. The GPIO cells however are referencing the modified `sky130_ef_io__gpiov2_pad_wrapped` cell included here.
* `chip_io_propel`: This is a modified version of `chip_io` for the PROPEL project, including several analog pads used in the `chip_io_alt` padring from caravel.
* `sky130_ef_io__gpiov2_pad_wrapped`: This is the modified version of the same cell from caravel. In this version of the cell, all the configuration pins not related to configuring IO cell direction are pre-tied accordingly to create a Digital I/O with Strong/Strong drive. This configuration disables the analog input capability of the IO cell as we have opted instead to use the dedicated analog IO cells for this purpose.
* `sky130_ef_io__gpiov2_pad_wrapped_input/output`: These are further modified versions of the GPIO cell pre-configured for input or output, with all relevant config pins pre-tied and only the IO cell chip-side input/output pin exposed. These can be placed interchangeably with the existing IO cells in the event a runtime-configurable IO cell is not necessary.
* `sky130_ef_io__analog_pad`: This is the analog pad used in the IO ring, which is just a short. This is the same analog pad used in the `chip_io_alt` padring provided in caravel with no modifications. The `wrapped` version of this cell contains additional ring slices to match the width of the GPIOv2 cell.
