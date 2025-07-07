# KIMTRON ABM85 TERMINAL

![2025-02-02 18 52 28](https://github.com/user-attachments/assets/56a30531-d393-4a27-bc05-2e4bf46a24ba)

I aquired 2x ABM85 terminals, one without the keyboard, both not working.
- Terminal 1
- 
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
- 

 
    

  

  
    
