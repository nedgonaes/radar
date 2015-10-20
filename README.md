# radar
gui for CS 5422 radar project

You should edit the variable MAX_RANGE so that the radar screen shows
interesting results.  In other words, although the range finder has a
maximum range of 5000mm, if most of your objects are a couple of cm
away, shorten the range to a few cm so that you it's easier to see
what's going on in the interesting region where there are actual
objects.

You may also need to adjust the portName variable on line 25, especially
if you have multiple devices connected to your machine.  You can either
adjust the index into the Serial.list(), or you can find the string name
for the serial port you are using (see tools>port setting in
the arduino IDE).

In order to run this, you need to download the Processing IDE from 
https://processing.org/.  Then load your sketch onto the arduino and start the
radar moving.  Then open and run this code in the Processing IDE.  It should
connect to the serial port that the arduino is sending data to, and display
the data on the screen.

To test if you've got it set up right, the following arduino sketch should send
data to the serial terminal that should be readable by the gui.  In particular
it should look as if there is an object 2000mm away all the way around.

int i = 0;
int inc = 1;

void setup() {
    Serial.begin(9600);
}

void loop() {
    delay(100);
    if (i == 180)
        inc = -1;
    if (i == 0)
        inc = 1;

    Serial.print(i);
    i += inc;
    Serial.print(",");
    Serial.println(2000);
}

This was adapted from http://howtomechatronics.com/arduino-radar/.
