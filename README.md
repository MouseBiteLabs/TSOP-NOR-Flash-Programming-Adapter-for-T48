# 29F160 to UV EPROM T48 Programming Adapter

This is an untested programming adapter for the T48 for programming already-soldered 29F160 chips on my <a href="https://github.com/MouseBiteLabs/ROM-Adapter-Boards/tree/main/29F160%20to%20UV%20EPROM">29F160 to UV EPROM Adapter board.</a> This *should* make it easy to reprogram the one or two flash chips on the adapters without having to desolder anything. I have not tested this yet, so consider this *experimental*. I will, of course, update the repo accordingly if my testing proves successful.

![image](https://github.com/user-attachments/assets/6a33cf20-7599-4ebf-8782-d6f4dd1de0be)

![image](https://github.com/user-attachments/assets/c77ecf35-aa9b-4f76-a0aa-aa6b0ef8f1e3)

This programming adapter requires the T48's TSOP adapter board to be placed on the right socket (P1) because it has a proprietary EEPROM (U1) that communicates with the T48. If you want, you can transfer over this EEPROM to *this* adapter board, along with R1 and C1 (a 4.7k resistor and 0.1uF capacitor); or you could simply piggy-back the TSOP adapter on P1, connect the ISP cable from J2 to the TSOP adapter, and keep the TSOP socket unused.

P2 accepts the v2.0 version of the 29F160 to UV EPROM adapter boards. It does not support previous revisions.

![image](https://github.com/user-attachments/assets/2bbcacce-e956-432a-8211-3c4c94209bbe)

## Revision History

### v1.0 - Prototype

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2025
