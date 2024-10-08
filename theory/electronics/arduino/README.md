# Arduino

More info about Arduino https://www.arduino.cc

Arduino was not made makers, engineers, or hobbyist but for design students in Italy. It is a small programmable device that can add smarts to nonintelligent things. You can use an Arduino to run robots, create LED art, and even act as a handheld gaming console.

\
A microcontroller is a small computer that you can program by uploading a program or set of instructions. Microcontrollers are used to automate simple tasks, like controlling the temperature of your house or watering your lawn when it’s dry.

Unlike a computer, an Arduino can only store and run a single sketch at a time. The standard test sketch loaded onto an Arduino is a simple LED blink.



<figure><img src="../../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

**ATmega328 microcontroller**&#x20;

The square black chip in the middle of the board. It is the brain of the Arduino. Header pins The tiny metal legs on the microcontroller, which let you read input and send output. They are accessible through the four sets of black headers on either side of the Arduino. They are numbered and labeled for specific uses. The pins you’ll care about most are those labeled Digital (0–13), Analog In (A0–A5), and Power.

**Mini-USB port** \
This is how you send code to and communicate with the Arduino. You can also power your board using the USB port for most applications in this book. If an external power supply is needed, we’ll be sure to point it out.&#x20;

**Power LED**&#x20;

This LED is an indicator to show that the Arduino is powered on. If you ever have a short circuit on your board or a bad power connection, this indicator will not turn on.&#x20;

**TX/RX LEDs**&#x20;

These LEDs blink when data, such as code or numbers, is being passed back and forth between your Arduino and your laptop.&#x20;

**Onboard LED**&#x20;

13 A debug light. If you’re plugging your Arduino in for the first time, LED 13 should blink once per second. It’s connected to pin 13 on the Arduino.&#x20;

**External power jack**&#x20;

A barrel jack port next to the USB port. The Arduino takes 5 V of power, though you can safely supply the Arduino a voltage between 7 and 15 V without damaging your board. A chip on the Arduino scales this input voltage down to 5 V for the electronics and circuitry to work properly. Like all Arduino-compatible boards, you’ll program the RedBoard with the Arduino IDE.
