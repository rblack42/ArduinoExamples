Arduino Example Code
####################

This repository contains a number of Arduino example projects I use in my
Computer Architecture class at ACC (`cosc2325 <http://www.co-pylit.org/courses/cosc2325/index.html>`_. These projects do not use the Arduino IDE<
but do use the compiler installed inside that IDE. This approach makes it easy
to experiment with example Arduino code set up for the IDE< or stand-alonf C or
assembly language projects. 

The included Makefile system current builds properly on Windows 7, Windows 10, Ubuntu Linux and Mac OS-X systems with the Arduino IDE (icurrently version 1.6.6) installed.

Prerequisites
*************

Make sure the following tools are available on your systemi, and run from the command line:

    * ``make`` - to build projects

    * ``avr-gcc`` -  C compiler for AVR chips

    * ``avrdude`` - loads hex files on the Arduino

    * ``avr-objcopy`` - needed by build system

    * ``avr-objdump`` - to produce listing files

Instructions on setting up systems with these tools, and other development tools, can be found on my website at http://www.cop-ylit.org/General.


