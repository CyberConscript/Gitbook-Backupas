# Programming

When writing sketches in Arduino, you need to be very specific with the words, punctuation, and capitalization you use. These elements are part of a programming language’s syntax.

<figure><img src="../../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

Both setup() and loop() have the type void because they do not return any values.

The name of every function includes a set of parentheses. These parentheses are where you pass parameters to the function. Parameters are values that a function needs to do its job. Neither setup() nor loop() needs parameters, but you’ll use some functions in later projects that do need them.



Pins

Pins 0–13 on the Arduino are considered general-purpose input/output (GPIO) pins. They can be used as either inputs or outputs, and pinMode() allows you to tell the Arduino how you plan to use a digital pin. You do this by passing two parameters. The first is the pin number, and it can range from 0 to 13. The second parameter is the pin configuration.



```
int led_red = 0; // the red LED is connected to Pin 0 of the Arduino
int led_yellow = 1; // the yellow LED is connected to Pin 1 of the Arduino
int led_green = 2; // the green LED is connected to Pin 2 of the Arduino

void setup() {
  // set up all the LEDs as OUTPUT
  pinMode(led_red, OUTPUT);
  pinMode(led_yellow, OUTPUT);
  pinMode(led_green, OUTPUT);
}

void loop() {
  // turn the green LED on and the other LEDs off
  digitalWrite(led_red, LOW); 
  digitalWrite(led_yellow, LOW);
  digitalWrite(led_green, HIGH);
  delay(2000);    // wait 2 seconds
  
  // turn the yellow LED on and the other LEDs off
  digitalWrite(led_red, LOW);   
  digitalWrite(led_yellow, HIGH);
  digitalWrite(led_green, LOW);
  delay(1000);   // wait 1 second
  
  // turn the red LED on and the other LEDs off
  digitalWrite(led_red, HIGH);  
  digitalWrite(led_yellow, LOW);
  digitalWrite(led_green, LOW);
  delay(3000);  // wait 3 seconds        
}
```



## Functions

```
void setup()
{
pinMode(13, OUTPUT);
}
void loop()
{
blink(13, 1000);
}

void blink(int pinNumber, int delayTime)
{
digitalWrite(pinNumber, HIGH);
delay(delayTime);
digitalWrite(pinNumber, LOW);
delay(delayTime);
}
```
