# TSOP NOR Flash Programming Adapter for T48

This is an untested programming adapter for the T48 for programming already-soldered 29F160 chips on my <a href="https://github.com/MouseBiteLabs/ROM-Adapter-Boards/tree/main/29F160%20to%20UV%20EPROM">29F160 to UV EPROM Adapter board.</a> This *should* make it easy to reprogram the one or two flash chips on the adapters without having to desolder anything. I have not tested this yet, so consider this *experimental*. I will, of course, update the repo accordingly if my testing proves successful.

![image](https://github.com/user-attachments/assets/ca0ac701-bc50-4d48-a3e9-59ffad45ed8c)

![image](https://github.com/user-attachments/assets/d1044af2-7147-4e0c-a4b0-313e5c86717a)

All gerbers and source files can be found in this repo, as this project is fully open source. Please read all instructions associated with this board before assembling.

## Board Characteristics and Order Information

The zipped folder contains all the gerber files for this board. You can generally choose whatever thickness you want, but I usually stick to at least 1.0mm.

You can order this board on OSH Park here: https://oshpark.com/shared_projects/88i525Ij

Alternatively, you can use the zipped folder at any board fabricator you like. You may also buy the board from PCBWay using this link (NOT YET AVAILABLE) (disclosure: I receive 10% of the sale value to go towards future PCB orders of my own):

<a href="https://www.pcbway.com/"><img src="https://www.pcbway.com/project/img/images/frompcbway-1220.png" alt="PCB from PCBWay" /></a>

## Required Equipment

- You will need basic tools, like a soldering iron.
- You'll need an extra 2x8 2.54mm female-female IDC ribbon cable, like this one: https://www.digikey.com/short/b1q09p80
  - Alternatively, you can use DuPont breadboard female-female jumpers, like these: https://www.digikey.com/short/vm5d3m4h
- This programming adapter requires the <a href="https://xgecu.myshopify.com/products/100-original-xgecu-adp_f48_ex-1-tsop48-special-adapter-for-nor-flash-only-use-on-t48-tl866-3g-programmer">T48's XGecu TSOP adapter board</a> to be placed on the right socket (P1). This is because it has a proprietary EEPROM (U1) that communicates with the T48.
  - If you want, you can transfer over this EEPROM to *this* adapter board, along with R1 and C1 (a 4.7k resistor and 0.1uF capacitor); or you could simply piggy-back the TSOP adapter on P1, connect the ISP cable from J2 to the TSOP adapter, and keep the TSOP socket unused.
 
![image](https://github.com/user-attachments/assets/f7b6a95f-c792-407e-a06a-9ff653ec8c59)

## Supported Boards

P2 accepts the v2.0 version of the 29F160 to UV EPROM adapter boards. It does not support previous revisions.

![image](https://github.com/user-attachments/assets/2bbcacce-e956-432a-8211-3c4c94209bbe)

## How to Assemble and Use the Adapter

### Step 1: Assembly

- You will likely want to populate the right side of each row of pins first with male header pins (2.54mm), which need to have the longer sides sticking down below the board. This will be the rows of pins that go into the T48 programmer. Then, populate the left side of each row of pins with female header pins (2.54mm). This will be where the XGecu TSOP Adapter is housed. 

It's much easier to assemble it in this way, as you can see here:

![image](https://github.com/user-attachments/assets/fd6a3e54-3b02-4288-86d2-1a5d258fa9e5)

(Alternatively, you can use only one set of these pins with female socket headers that have longer pins so that you can place it in the T48 *and* connect the XGecu Adapter.)

- P2 and the /BYTE, /RP, and /WE pins (the ones located inside the P2 footprint) are populated with simple female header sockets (2.54mm).

![image](https://github.com/user-attachments/assets/998994d5-bc5e-41f5-8b59-76cbe5e37b08)

- J1 and J2 are populated with simple male header pins (2.54mm).

- SW1 and SW2 are SPDT switches: https://www.digikey.com/short/zvmm2dj3

![image](https://github.com/user-attachments/assets/96887395-2e98-4863-8a21-d07e988f2c7c)

- U1, R1, and C1 are discussed below. They are not required for operation, but may be harvested from the XGecu TSOP Adapter.

### Step 2: Connect XGecu TSOP Adapter and 29F160 to UV EPROM Board

With the programming adapter placed in the T48 (check polarity!), place the XGecu TSOP adapter into P1 on the left in the correct orientation. Then, connect one IDC cable from the T48's 16-pin socket to J1 (again, mind the polarity). Connect a second IDC cable from J2 to the XGecu TSOP adapter.

Finally, place the 29F160 to UV EPROM board in the left socket P2.

[TO DO: pic]

### Step 3: Configure the Switches

SW1 and SW2 are for correctly configuring the 29F160 UV EPROM board for programming.

If you are using just one 29F160 chip, place SW2 in the "1x NOR" setting. If you are using two, then place SW2 in the "2x NOR" setting.

When programming a 2x 29F160 board, your ROM files must be in 2MB (16Mbit) chunks. To program the first 29F160 with the first 2MB chunk, place SW1 in the "1ST" setting. To program the second, switch SW1 to the "2ND" setting. If you are only using 1x 29F160, this switch does nothing.

## Bill of Materials (BOM)

As far as the headers (male and female) go, there are plenty of places to get them from at better prices. I personally have drawers full of them, so I didn't need to buy any extra. But if you're looking for exact parts, you can use these. The only parts you may need to buy, if you have a stock of headers and jumper cables ready to go, are the EG1271 switches.

Please note that P1 has two different options, and Option A is a set of 2 separate part numbers (this is the option shown in pictures above in the assembly section with separate male and female headers). P2 has three separate part numbers to populate all of the pins with female sockets while being cost effective.

Also note that in breaking with tradition from my other repositories, I have *Digikey* links listed. This is simply because Mouser did not have an equivalent IDC cable that didn't cost like $10. You can find all the other parts on this list at Mouser as well.

| Reference     | Qty | Value/Part Number | Package                                   | Description                     | Source                                                                           |
| ------------- | --- | ----------------- | ----------------------------------------- | ------------------------------- | -------------------------------------------------------------------------------- |
| Cable (Opt A) | 1   | H3CCH-1606G       | 2x8, 0.1" Spacing                         | IDC Cable                       | [https://www.digikey.com/short/j5rt9349](https://www.digikey.com/short/j5rt9349) |
| Cable (Opt B) | 1   | 1950              | \-                                        | Jumper Wire F-to-F              | [https://www.digikey.com/short/5wr7q7fz](https://www.digikey.com/short/5wr7q7fz) |
| J1, J2        | 2   | 77313-818-16LF    | 2x8, 0.1" Spacing                         | 16 Position Header Pins, Male   | [https://www.digikey.com/short/13fhc19n](https://www.digikey.com/short/13fhc19n) |
| SW1, SW2      | 2   | EG1271            | 2x3 Pins                                  | SPDT Slide Switch               | [https://www.digikey.com/short/vj8nm90f](https://www.digikey.com/short/vj8nm90f) |
| P1 (Opt A)    | 2   | PPPC201LFBN-RC    | 20 Pins, 0.1" Spacing                     | 20 Position Header Pins, Female | [https://www.digikey.com/short/7rdtqfvp](https://www.digikey.com/short/7rdtqfvp) |
|               | 2   | PRPC020SAAN-RC    | 20 Pins, 0.1" Spacing                     | 20 Position Header Pins, Male   | [https://www.digikey.com/short/zpzj5p9h](https://www.digikey.com/short/zpzj5p9h) |
| P1 (Opt B)    | 4   | SSQ-110-03-G-S    | 10 Pins, 0.1" Spacing, 0.394" Post Length | 10 Position Header Pins, Female | [https://www.digikey.com/short/rvwzhn13](https://www.digikey.com/short/rvwzhn13) |
| P2            | 2   | PPPC201LFBN-RC    | 20 Pins, 0.1" Spacing                     | 20 Position Header Pins, Female | [https://www.digikey.com/short/7rdtqfvp](https://www.digikey.com/short/7rdtqfvp) |
|               | 1   | PPPC021LFBN-RC    | 2 Pins, 0.1" Spacing                      | 2 Position Header Pins, Female  | [https://www.digikey.com/short/bd5t98qm](https://www.digikey.com/short/bd5t98qm) |
|               | 1   | PPPC031LFBN-RC    | 3 Pins, 0.1" Spacing                      | 3 Position Header Pins, Female  | [https://www.digikey.com/short/p04ft8t8](https://www.digikey.com/short/p04ft8t8) |

## What's with U1, R1, and C1?

On the XGecu TSOP Programming Adapter, these 3 components are included. This is a proprietary EEPROM for communicating with the T48. I believe this is a form of copy protection. If you wish, you can transfer these components over to this board instead - this would remove the need of placing the XGecu adapter into P1. *(Maybe a clever person could reverse engineer the EEPROM by sniffing pins 5 and 6, which are the only two pins used on this chip)*

## What's with the P37/VCC and P29/GND/P18 Pins?

This is basically for helping me troubleshoot if I run into problems. One of the things I'm unsure of is if the T48 will throw an error if it detects the larger-than-normal load due to the extra circuitry on my TSOP adapter boards. 

Pin 37 on the T48 is connected to the VCC pin of the TSOP chip, but it is not directly connected to VCC itself, which is pin 14 of J1/J2. The jumper is there in case the TSOP board current limits the programmer with the extra circuitry on it. Though, that might cause other problems, so it is not hard-wired. Pin 18 and pin 29 are a similar case for VSS.

You can ignore these pins (unless I update the repo further to address them).

## Revision History

### v1.1 - Prototype II

- Disconnected pin 18 and pin 29 on P1 from VSS and connect to the proper pins on P2 instead
- Renamed board to be more general

### v1.0 - Prototype

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2025
