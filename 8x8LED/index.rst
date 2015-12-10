Wiring an 8x8 LED Matrix
########################

Some of the projects I offer use a Kingsbright TC23-11HWA 8x8 LED matrix I
picked up years ago for about $3.00 each. These are simple devices with
somewhat complex wiring.

The data sheet for this device is available here:

    * :download:`TC23-11HWA.pdf`

The annoying thing about this display is how the pins are laid out. There are
two rows of eight pins on each side of the device, but the ordering of the pins
is not obvious at all. To use the device, you will need to plug it into two
breadboards. There are different ways to do this, but for my eample, we will
connect the two breadboards together (they are dsigned to do thi), and plug the
LED mextrx into the two boards. We will just have enough room to do the wiring,
but will need a bunch of jumper wires to set this up.

..  note::

    The safest way to wire up electronics circuits is to write up a connection
    list that details every connection you need to make with jumper wires.
    Check off lines in that list as you make connections to make sure
    everything is wired correctly. Then run through the list agian and check it
    twice befroe you apply power to things. Improperly wired circuits can
    destroy devices, or Arduinos if not done correctly. If in doubt, ask for
    help!


Here is the layout of the pins on the 8x8 LED:

..  csv-table:
    :header:    Pin, LED

    1, R5
    2, R7
    3, C2
    4, C3
    5, R8
    6, C5
    7, R6
    8, R3
    9, R1
    10, C4
    11, C6
    12, R4
    13, C1
    14, R2
    15, C7
    16, C8

The pins numbered 1-8 are found on the side of the device with the part number
showing, numbered fro left to right. SPi the part around 180 degrees, and the
pins are numbered 9-16 from left to right on that opposite side. This is ahown
in the data sheet.


Port Assignments
****************

We need a total of 16 output pins on the Arduino to drive this beast. Eight
pins will be used to decide what rows to send current through. We will program
a "1" on any output pin we want to light up. The column where the individual
LED is to light up will be selected by outputing a zero on that column line,
while all other column lines are set to one.

Current flows from the "1" (5V) to the "0" (0V, or "ground") through one lED
causing it to light up. 

If we placed a "0" on any other column lines at the same time, more that one
LEDs on that row would light up, but that is not how we will normally control
this device.

Instead, we will set up a loop that writes all "1"s to the column pins, and
sends a "0" to one column pin at a time. While that column is "selected" we
will write out eight values on the row pcontrol port. Where there is a "1" in
that data value the corresponding LED will light up. Next time through the loop
the same thing will happen on the next column and so on. By spinning through
this loop over and over fast enough, your eye will be fooled into thinking thet
the LEDs are all on all the time, but that is just a magical illusion your eyes
make happen! COol!

We can decide what pattern to display on each column by setting up a data array
of values to load, then fetching the right bytefor each column in tha loop. Any
pattern you can create in those 64 biLEDs can be created. If you want to
animate the display, all you need to do it jump to the right spot in a data
array for the starting column of the pattern you want moving across the display
and let it fly! The coding gets more complex as you do this, but it is not
extremely difficult.






