
*Note that this page is currently an outline and most of the content is not yet written.*

## Connectors

**Waterproof (external) Connections**

- Wire to Endcap (detachable): Fischers
- Wire to Endcap (not detachable): BlueRobotics penetrators (wetlink penetrators should be preferred over potted penetrators)
- Wire to Wire: Either use an epoxy filled block or waterproof heatshrink 

**Signal & Low Current**:

- Wire to Wire: JST SM
- Wire to Board: Molex KK 254
- Fallback (either): DuPont (use only when JST-SM or Molex KK 254 are not viable, recommended only for prototyping)

**Higher Current**

- Wire to Wire or Wire to Board: Powerpole (PP15-45 series)
- Wire to Wire: XT90 (use these only for connections directly to battery or where current larger than 45A is required)
- Wire to Screw Terminal: Heat shrink ring connectors


### DuPont Connectors

![](./img/dupont-connectors.jpg){: .center style="width:80%"}

- Wire to wire
- Wire to board when paired with standard 2.54mm pin headers
- Intended for signals not power (2A max per pin)
- Cheap and easy to get (kits easily found on Amazon)
- Moderately difficult to crimp
- Not keyed
- Male pins are easy to bend / break both when connected and when not connected
- Pair well with standard 2.54mm pin headers
- Work with breadboards
- Housings in two-row configurations are sold


### Molex KK 254 Connectors

![](./img/kk254-connectors.jpg){: .center style="width:80%"}

- Wire to board
- Intended for signals (4A max per pin, less depending on crimp pin selection)
- More expensive than DuPont connectors (but better)
- No kits sold, must buy individually from digikey / mouser
- Moderately difficult to crimp
- Keyed
- Male pins always on board. Only female crimps for wire.
- 2.54mm pin pitch, so compatible with DuPont connectors and standard pin headers if necessary
- Housings only in one-row configurations



### JST SM Connectors

![](./img/jstsm-connectors.jpg){: .center style="width:80%"}

- Wire to Wire
- Intended for signals (2A max per pin)
- Can find in kits on Amazon (harder to find than DuPont, but possible)
- Moderately difficult to crimp
- Keyed
- Latching
- Protected male pins (both when connected and not connected)
- Housings only in one-row configurations



### Anderson Power Powerpole Connectors (PP15-45 series)

![](./img/powerpole-connectors.jpg){: .center style="width:80%"}

- Wire to Wire or Wire to Board
- Intended for power (15, 30, 45 A)
- Expensive
- Easy to crimp
- Keyed
- Same housing / pin used on both sides of connection
- Custom configurations possible (custom size and key of connector block)
- Recommended for wire from 20 to 10 AWG


### XT90 Connectors

*Note that XT60 connectors are rarely used, but are generally the same idea (just lower current rating). XT60 connectors are only used on the battery chargers and should not be used on the robot itself.*

![](./img/xt90-connectors.jpg){: .center style="width:80%"}

- Wire to Wire
- Wire to Board *may* be possible, but not recommended.
- Soldered **not crimped**
- Somewhat difficult to solder (generally requires heatsink and large iron tip)
- Robust connectors
- Work well with larger gauge wire only (14-10 AWG)



### Heat Shrink Ring Connectors

*Note: There are variants of these sold that are "U" shaped (not a closed ring). These are not to be used on the robot as they easily come loose.*

![](./img/ring-connectors.jpg){: .center style="width:80%"}

- Wire to screw terminal
- Can be used wire to wire with a loose screw & nut, but **not** recommended.
- Easy to crimp
- Generally can handle the same current as any wire that can fit inside them



## PCB Headers

- Standard 2.54mm headers (right angle and vertical)
- KK 254 headers (right angle and vertical)
- Powerpole headers (right angle and vertical)


## Electronic Assembly

- PCBs
- Protoboard
- Breadboard (avoid on robot, if necessary hot glue EVERYTHING)


## Microcontrollers

Custom boards integrating microcontrollers should use TI's MSP430 series of MCUs. This family of microcontrollers integrates the required features and are generally powerful enough for our use cases. Additionally, NCSU's ECE department has an embedded systems course built around these microcontrollers, thus it helps align club operation with coursework.

If there is no compelling reason not to, TI's MSP430FR2355 is recommended. This chip integrates almost any peripheral that would be required, has many serial communication interfaces, and has more GPIO pins than would typically be used. The LQFT-48 package version of this chip is easy enough to hand solder as well.

If there is a compelling reason to select a different MSP430, this is permissable, however it should be attempted to use a chip that can be more easily hand soldered. Avoid QFN and BGA packages (or anything else with pads contained under the chip).


In cases where an MSP430 does not provide sufficient power for what is being designed, it is recommended to use an Arm architecture microcontroller. There are many vendors of these on the market (not a complete list):

- TI's MSP432 series
- TI's MSP-M0 series
- Microchip's SAM series
- ST Microelectronics STM32 chips
- Raspberry Pi RP2040
- Many NXP Semiconductors chips

When choosing a chip, make sure to also research the cost of a debug probe. For example, the STM32 series are compatible with low cost ST-Link debug probes.


## FPGAs

FPGAs supported by Vivado are preferred.


## IC Packages

Integrated circuits used on our boards should be hand solderable. Avoid QFN and BGA packages (or anything else with pads contained under the chip). This can be violated if absolutely necessary, however make sure there is an assembly plan.
