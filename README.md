# ControllingBrushlessMotorWithArduino

<h2>What is Brushless motors</h2>
<p>Instead of brushes and a commutator, these motors use electronic means (a drive circuit) to rotate the motor. </p>

<h2>How Does it Works</h2>
Before getting into the principle of the brushless mechanism, let’s first take a look at it’s components.<br>

This is commonly referred to as an electromagnet:


![alt text](https://github.com/DaleenSofyan/ControllingBrushlessMotorWithArduino/blob/main/Images/01.jpeg)



This will make the rotor start to spin as the permanent magnet experiences repulsion from the like-electromagnet and tries to align with an opposite permanent magnet on the stator.


![alt text](https://github.com/DaleenSofyan/ControllingBrushlessMotorWithArduino/blob/main/Images/02.jpeg)


Brushless ESCs need information on the current position of the rotor to be able to start the motor and choose a direction for the rotation.
Shorter frequencies allow a faster reaction time.
Furthermore, the Dshot protocol is different from the two others because it sends a digital signal instead of an analog signal.


<h2>The Circuit</h2>

![alt text](https://github.com/DaleenSofyan/ControllingBrushlessMotorWithArduino/blob/main/Images/03.jpeg)

<h2>Arduino Code for BLDC Motor Control</h2>

    /*
        Arduino Brushless Motor Control
     by Dejan, https://howtomechatronics.com
    */

    #include <Servo.h>

    Servo ESC;     // create servo object to control the ESC

    int potValue;  // value from the analog pin

    void setup() {
    // Attach the ESC on pin 9
    ESC.attach(9,1000,2000); // (pin, min pulse width, max pulse width in microseconds) 
    }

    void loop() {
    potValue = analogRead(A0);   // reads the value of the potentiometer (value between 0 and 1023)
    potValue = map(potValue, 0, 1023, 0, 180);   // scale it to use it with the servo library (value between 0 and 180)
    ESC.write(potValue);    // Send the signal to the ESC
    }


<h2>Resources</h2>
1. https://www.tytorobotics.com/blogs/articles/how-brushless-motors-work
2. https://www.automate.org/blogs/what-is-a-brushless-dc-motor-and-how-does-it-work
3. https://howtomechatronics.com/tutorials/arduino/arduino-brushless-motor-control-tutorial-esc-bldc/
