# ROCO222 coursework writeup
## DC MOTOR (buidling the prototype)
Our first task was to creat a brushed DC motor using the following materials 
- Cork
- Strong magnets 
- wooden board 
- paper clips
- nail
- screws and washers
- copper wire
- copper tape

First step was was drive a nail through the centre of the cork, so it acts as a turning axis, then we had to stick copper tape on one end of the cork with gaps to form a commutator in order for the polarity of the DC electricity to be flipped. Next step was to wind copper wire around the poles of the cork to make an armature coil, which was roughly 125 turns (using rougly 10m of wire), which resulted in a resistance of 7.3Ω. In oder the commutator to work we had to solder each end of the copper wire to each of the 2 copper tapes, so we sanded off the enamel of the wire and soldered it on. 

![Picture of motor](https://github.com/danstares/ROCO222/blob/master/Motor%20v1.jpg)

Then we had to mount the motor to the base, using 2 strong paper clips we bent it into an 'L' shape in order to hold the motor then secured it to the wooden board using washers and screws; additionally we used another set of clips and screws to creat a stand for the magnets to be on both sides of the motor, making sure the polarity of the magnets are opposite so they induce a magnetic field. Finally we had to give the whole thing power, which we did by using thick cables and snipping off the insulation, using the wires on the inside as brushes. After all that it was time to test it, setting the power supply to 12V on both ends we powered it up and with some fiddling and adjusting our prototype was finally working.

## DC MOTOR (improving design)
To improve the design and the functionalty of the motor, we added another set of armature coils to the cork, with the same ammount of turnings(125) and repeated the process of soldering on the ends of the wires, this time assing another set of 2 copper tapes as commutators. As for the brushes, we used more paper clips to secure it in place so we wouldnt have to hold it as the motor span. We powered it and this is the result. 

![video of motor](https://github.com/danstares/ROCO222/blob/master/DC%20MOTOR%20WORKING.mp4)

As you can see its working fine and spins rather fast! It was also rather stable.

We experimented with making more motors made of corks but non of these where as good as the proto type so we moved on, here are some of the new ones 

![Picture of other motors](https://github.com/danstares/ROCO222/blob/master/motorVarients.jpg)

We then started working on an improved design, we designed a new motor using a CAD software and printed it using a 3D printer. This design features a star-shaped body and 4 armature coils, as we thought this would increae its speed and funtionality.

![Picture of 'star motor'](https://github.com/danstares/ROCO222/blob/master/MotorV3.jpg)

Unfortunately this motor had numerous problems, the first was that the commutators didn't work due to too many individual bits of copper tape, which made soldering hard and also gave the commutator less contact points, so the brushes would skip past some commutators, making the motor usless essentially. So we scrapped the design and stuck with the original prototype. Here is a picture of itself.

![Picture of prototype](https://github.com/danstares/ROCO222/blob/master/motorv2.jpg)

## Incremental encoder

## Motor Control with arduino

## Stepper Motor

## Robotic Arm Mini Project
We started familiarising ourselves with the basics of the servo. We hooked up the servo to the Arduino Nano board, with a 5V supply and the PWM pin  to DigitalOut 9. We then loaded up Arduio IDE and got to coding for the servo, and used a simple repeating code to get it to rotate back and forth to creat a sinewave of 0.2 Hz, this is the repeating code used. 
``` 
digitalWrite(9, HIGH); 
delay(2);
digitalWrite(9, LOW); 
delay(78);
digitalWrite(9, HIGH); 
delay(2);
digitalWrite(9, LOW); 
delay(78);
``` 
We then advanced to controlling the servo with potentiometers, with the same wiring for the servo but plugging in the potentiometer to an analog port (0), starting off with coding just one, I added a potentiometer to the circuit, using a breadboard to connect the 5V VDD and Ground to the rails so that I can easily plug stuff in without jamming multiple wires in a single port on the Uno. Here is a bit of the code 
### Setup:
``` 
#include <Servo.h>
Servo Myservo;
int potpin = 0;
int val;
``` 
### Loop
``` 
myservo.attach(9);
{
val = analogRead(potpin);
val = map(val, 0, 1023, 0, 179); 
myservo.write(val1);
delay(1);
}
```



