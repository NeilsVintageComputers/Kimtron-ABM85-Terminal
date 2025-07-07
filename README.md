# KIMTRON ABM85 TERMINAL

![2025-02-02 18 52 28](https://github.com/user-attachments/assets/56a30531-d393-4a27-bc05-2e4bf46a24ba)

I aquired 2x ABM85 terminals, one without the keyboard, both not working.
- Terminal 1
 
  The first one I worked on had no video or sync outputs and very little activity on the address and data buses.
  
  I removed the eproms from both machines and read the contents, they had data that didnt show any bit faults and the eproms from both read the same though one Char rom sometimes read incorrectly.
  
  Next to check was the 2114 ram chips, I removed them and tested in my Pegasus computer, all were faulty!
  
  With the ram replaced there was now normal looking activity on the address and data bus, but still no video or sync output.
  
  I discovered the clock signal to the CRTC chip was badly deformed, replaced U14 74LS163, clock now ok but still no video or sync output.
  
  I decided that as the board seemed to be running firmware that maybe the 8275 CRTC chip was faulty. Seeing as I had 2 terminals I decided to swap in the other 8275 chip, no change!
  
  At this time I rechecked all I could think of with the same conclusion that the 8275 was likely faulty. I was stumped!
  
  After it sat untouched for a couple of months I found the 8275 chips for sale on Aliexpress and ordered a few.
  
  When the chips arrived I fitted one and was pleasantly supprised that it burst into life!  Both of my terminals had faulty 8275 CRTC
 chips!

  One down, one to go.........

  
- Terminal 2

After finaly repairing the first terminal I was more optimistic when starting on the second one.

With the 8275 replaced with a tested Aliexpress chip I checked the ram chips, once again all were faulty!  

Then powered it up,no video or sync output, I looked for normal bus activity as seen on the first board, the firmware only ran for a short time before all activity stopped!

After many restarts and measurements with the scope I noted the data bus signals looked pretty bad, I suspected the 8212 bus interface chip. 
Unfortunately this wasnt socketed and I didnt want to risk damaging the working chip from the other terminal so I ordered another one and put the board aside until it arrived.

With the replacement 8212 installed, still no video or sync output, the data bus was now more active but some of the data lines were loaded down to near 0V all the time.
There are many chips that could cause this, I decided to remove the 8251 uart chips first as I thought they would not stop the firmware running.  No significant change to the data bus.

Next chip removed was the 8155 PIA chip, this fixed the data bus fault that I had seen but still no video or sync outputs.  I ordered another 8155 chip.  After replacing it the data bus was still ok and there was more activity on the address and data buses than I had seen before.

I reinserted the 8251 Uart chips one at a time and found 2 of them were also faulty, dragging down the data bus!  With these replaced the firmware seemed to be running with address and data busses looking similar to the first terminal.

There was still no video or sync output, I checked the clock to the CRTC chip and it was bad just like in the first terminal.
Replaced U14 and clock was back.  

Aditionally there was a signal at the video output but no sync outputs.  Measured the sync outputs at the CRTC pins and found both present, a great sign showing the board was basicaly running but the sync signals were not getting to the output terminals.

At this stage I decided I needed to reverse engineer the video output circuits from the CRTC chip to the sync output terminals, this took hours of tracing out every pin of every connected IC, the resultant schematic is in the documentation folder.  

From this it didnt take long to diagnose U11 as the problem, once replaced syncs were restored and at last there was now video on the screen!

The video had a strange fault, evident in the photo that shows a blank screen (with raster lines showing), in the first column of dots of each character.  In inverse mode (at the bottom of the screen) the first column of dots is missing!  

All bits other than bit D0 were observed to be coming out of the Char Gen Eprom, maybe D0 is the problem as one of the char gen eproms did read intermittently in my eprom programmer.  Replaced with a copy of the other working eprom, fault still there!
I dumped the char gen eprom and worked out that the LH column is D7, but needed more information to find how this gets from the char gen eprom to the video shift register.

This was going to be hard to track down without a schematic so I spent many hours reverse engineering the circuit from the Char Gen Eprom to the video shift register.  This schematic is also in the documentation folder.

The resultant schematic showed the D0 pin is not used, a red herring.  However with a schematic at hand it didnt take long to find the problem which was a faulty U15 in the character attribute circuit.  With this replaced correct video was displayed on the crt!!!

So now I had video on the screen, next step was to connect the keyboard and test the terminal.
No data came out!

I had already replaced the uart chip so removed the 1488 and 1489 and tested them, both were faulty!
Decided to replace the uart and driver chips together in case one was blowing up the other. 
I removed the 8251, 1488, and 1489 chips from the printer channel to use in the main channel, but when tested the 1488 in this channel was faulty as well.

I ordered some replacement 1488/1489 chips which fixed the final problem with the terminal!!!!!
I havent tested the printer channel but will probably never use it.

Time for a beer :)










 
    

  

  
    
