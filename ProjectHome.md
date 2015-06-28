**What's New? March 22, 2015: _This project has moved to Github! Update your links to https://github.com/GreyGnome/PinChangeInt . This is the final update here on this website, for the latest information go to Github._

Also, I'm considering deprecating this library in favor of a new one that encompasses all interrupt types. Please take my survey at https://www.surveymonkey.com/s/CJVMX3P . Thanks!**

Latest version: Go to Github.

(Note: As of March 22, 2015, Google lost the Wiki pages when I migrated to Github. It will take me some time to recreate them.)

The PinChangeInt library implements Pin Change interrupts for the Arduino environment.  This library was designed for the Arduino Uno/Duemilanove/Mega 2560/Mega ADK.  It will likely work with other ATmega328- or ATmega168-based Arduinos; it has been reported to work just fine on the Nano. It will not work on ARM-based Arduinos, but then, attachInterrupt() is a complete solution there.

What are Pin Change interrupts?  The ATmega328p processor at the heart of the Arduino has two different kinds of interrupts: “external”, and “pin change”.  There are only two external interrupt pins, INT0 and INT1, and they are mapped to Arduino pins 2 and 3.  These interrupts can be set to trigger on RISING or FALLING signal edges, or on low level.  The triggers are interpreted by hardware.

On the other hand the pin change interrupts can be enabled on any or all of the Arduino's signal pins.  They are triggered equally on RISING or FALLING signal edges, so it is up to the interrupt code to set the proper pins to receive interrupts, to determine what happened (which pin?  ...did the signal rise, or fall?), and to handle it properly.  Furthermore, the pin change interrupts are grouped into 3 “port”s on the MCU, so there are only 3 interrupt vectors (subroutines) for the entire body of 20 pins.  This makes the job of resolving the action on a single interrupt even more complicated.  The interrupt routine should be fast, but complication is the enemy of speed.  The PinChangeInt library is designed to handle the Arduino's pin change interrupts as quickly and reasonably as possible.

Version 1.4 (and later) puts all the code in the .h file, to allow the programmer to configure it through their sketch for minimum ram usage.  In earlier versions, it must be configured through the PinChangeIntConfig header file instead.

See the Wiki pages for more information.