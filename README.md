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

With the replacement 8212 installed, still no video or sync output, the data bus was now more active but one of the data lines was loaded down to near 0V all the time.
There are many chips that could cause this, I decided to remove the 8251 uart chips first as I thought they would not stop the firmware running.  No change to the data bus.

Next chip removed was the 8155 PIA chip, this fixed the data bus fault but the CRTC chip didnt seem to get initialised.  I ordered another 8155 chip.  After replacing it the data bus was still ok and there was more activity on the address and data buses.

I replaced the 8251 Uart chips one at a time and found 2 of them were also faulty, dragging down the data bus!  With these replaced the firmware seemed to be running with address and data busses looking similar to the first terminal.

There was still no video or sync output, I checked the clock to the CRTC chip and it was bad just like in the first terminal.
Replaced U14 and clock was back.  

Aditionally there was a signal 



 
    

  

  
    
