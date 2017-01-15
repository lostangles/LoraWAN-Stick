# LoraWAN-Stick
PCB combining Atmega32u4, MTK3339 GPS module, and RN2903 LoraWAN module
This is rev 0; changes will probably need to be made once I get PCBs in and test them

OSHPark permalink: 
https://oshpark.com/shared_projects/INShZUhB

![Alt text](PCB.png?raw=true "PCB")


# Functionality
I wanted to make a single PCB that had some GPIO, communication interfaces, a module to transmit LoraWAN packets, and a way to get current location.  The LoraWAN stack is offloaded from the 32u4 and rests in a PIC microcontroller inside the RN2903.  This allows a simple interface of simply passing the payload from the 32u4 to the RN2903 without having to worry about the LoraWAN stack inside your project.

The LoraWAN-Stick incorporates the LiPo charging circuitry common to the Adafruit Feather line of dev boards, as well as follows the same pinout for attachment of Adafruit Featherwings.  Because both the RN2903 and GPS module use serial communications, serial communications with other nodes may be difficult; the GPS module uses the hardware UART, and communication to the RN2903 uses software serial.  From my experience, having multiple software serial interfaces tends to work in unexpected ways, and should probably be avoided without thorough testing.

# Pins
Pinout follows Adafruit Feather format as I wanted to be able to add compatability of Adafruit Featherwings to this project.
The 32u4 only has a single hardware UART, hard wired to the TX/RX of the GPS module.  These pins are broken out on the header.

The RN2903 is controlled by serial, but because the 32u4 has only a single UART, a software serial interface must be used.  The RN2903 is hardwired with its RX on pin 5 and TX on pin 10.  Reset for the RN2903 is hard wired to pin 6 and should be pulled high when not in reset state.  The RN2903 Pickit3 programming header is also broken out to update the firmware on the RN2903 directly.


# Bill Of Materials
https://github.com/lostangles/LoraWAN-Stick/blob/master/LoraWAN-Stick.xlsx

Total cost: $52.52



U3	RN2903-I/RM095	RN2903-I_RM095:XCVR_RN2903-I%2fRM095	Microchip
U2	ATmega32U4-AU	Housings_QFP:TQFP-44_10x10mm_Pitch0.8mm	
U1	FGPMMOPA6H	FGPMMOPA6H:FGPMMOPA6H	
P1	USB_OTG	Connect:USB_Mini-B	
R1	22	Resistors_SMD:R_0603_HandSoldering	
R2	22	Resistors_SMD:R_0603_HandSoldering	
U4	SPX3819	adafruit:adafruit-SOT23-5L	
R3	100k	Resistors_SMD:R_0603_HandSoldering	
C1	10uF	Capacitors_SMD:C_0603_HandSoldering	
C2	10uF	Capacitors_SMD:C_0603_HandSoldering	
C3	1uF	Capacitors_SMD:C_0603_HandSoldering	
D1	DIODESCH	Diodes_SMD:D_0805	
CN1	JST_2PIN-SMT	adafruit:adafruit-JST-PH-2-SMT	
C4	1uF	Capacitors_SMD:C_0603_HandSoldering	
SW1	SPST	open-project:SW_PUSH_SMD	
U5	MCP73831	arthurc:SOT23-5	
D2	LED-BAT	Diodes_SMD:D_0805	
R4	1k	Resistors_SMD:R_0603_HandSoldering	
R5	10k	Resistors_SMD:R_0603_HandSoldering	
C5	10uF	Capacitors_SMD:C_0603_HandSoldering	
R6	100k	Resistors_SMD:R_0603_HandSoldering	
R7	100k	Resistors_SMD:R_0603_HandSoldering	
C6	10uF	Capacitors_SMD:C_0603_HandSoldering	
JP3	PINHD-1X12	adafruit:adafruit-1X12	
JP1	CONN_01X16	Pin_Headers:Pin_Header_Straight_1x16	
JP2	PINHD-1X6	adafruit:adafruit-1X06	
ANT1	CON-SMA	misc:CON-SMA-EDGE	
D3	LED-RED	Diodes_SMD:D_0805	
R8	1k	Resistors_SMD:R_0603_HandSoldering	
D4	LED-POW	Diodes_SMD:D_0805	
R9	1k	Resistors_SMD:R_0603_HandSoldering	

# TODO 

Verify all functionality

Verify pin header compatbility

Add ICP header for 32u4

Verify software serial pins work correctly


