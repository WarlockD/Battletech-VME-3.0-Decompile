# Battletech-VME-3.0-Decompile

Right now I don't have much.  Someone dumped the server software used to manage the pods and after taking a look at it it seems the pods just have network boot roms on them and load software right from this server.  I suspect they have about 32megs of ram from the low quality pictures but they also must have some static ram in there.

The pods of 2.0, 2.5, and 3.0 all seem to have diffrent memory maps as well.  I started work on just the 2.0 but then had a fear that the 3.0 are completely diffrent.  I am also in the process of finding what compiler they used.  I have figured out some basic things like memory management and where serial ports are but beyond that not much else.

Right now I am in the process of making a Mame emulator bit.  I just found out it has a DSP (either for sound or 3D), so because of that I just threw up my hands and going to see if I can just boot the bloodly thing by guessing the ports in mame.

There is a picture of the AROSE card.  AROSE was Apples idea to put a 68k chip on a nubus card and have that run stuff.  (Network stacks etc).  On one hand it makes sense that you would want this lower end cpu handle stuff like the tcp/ethernet stack.  Hell adaptec has been doing this for years on the pc using a z80 for thier SCSI cards.  On the other hand that damn card can get FULL BUS ACCESS to the mac itself.  The good news about this odd ball ARCNET card is it looks like a carbon copy of the Apple Ethernet NB card witch is an AROSE card itself.  Diffrent chip for the network though but it uses the same TI bus arbertrators.  Need to copy the rom from the one I have and see if I can make a makehift device for mame.

However, all the software does is upload the roms, the mapes and settings for the games.  Its just easier to figure out a new program for that.

What else...  Oh right the "amega 500" problem.  The pods don't run off the amega 500.  IT just uses an amega 500 board, somehow connected to the main board, to handle the secondary display.  In 3.0 it has some kind of custom sound board? ugh.  Hell, all the controls in the pod?  Seperate snoflake board that is connected to the main processing board, luckly, by serial port with a easy to emulate protocol.  The opcodes the main board is running a 68020 with floating co processor.  TMS34010 (maybe a 020, not sure yet), an ADP-21020 DSP and two serial ports. 

Ok, just some info where the roms go just so I can check latter
"ROM3_0"				                   020FFFE4
"BattleTech_68020_Res"	02AC0000
"R.BIN3_0"			                   02AE0000
"BattleTech_TI_Res"					02B00000
"btAudio.dld"		                 02D00000
"AMIGA3_0"			                400003e4
"btsecond3_0"		              40010400
"DEVELOPMENT"		            02FFFF00
"Go_Address"		               02100000

Also there is some kind of script interpeter in there?  It looks like you can download an entire "arena" That being just a big flat map with a bunch of random things on the ground.  Again, this is all just notes I am typing because I get distracted easly.

I put this up in case anyone wants to take a more serious crack at it.  Honestly, with mame being as advanced as it is, it shouldn't be to hard to get something up.