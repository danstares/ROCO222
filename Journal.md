# ROCO222 Lab Journal
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
To measure the speed of the motor, we had to build a motor encoder, which consisted of an IR LED and an IR phototransistor. With the given cicuit diagram and a few resistors, we began to solder together the encoder circuit, with the LED and the phototransistor facing each other. For the encoder to pick up information, we palced a disc with a spacing cut into it, similar to the shape of pac-man. we fitted the disc onto the end of our working motor and secured the encoder to the base of the board. we then entered the simple code given and tested out the encoder. Unfortunately it was not working as we wished, the encoder ay have had a bad soldering job, but we decided to move on as time was paramount.

![picutre of motor with disc](https://github.com/danstares/ROCO222/blob/master/MotorWithDisc.jpg)
![picture of encoder](https://github.com/danstares/ROCO222/blob/master/Encoder.jpg)

## Stepper Motor
We were given a hybrid stepper motor, we attached the Arudiono shield and plugged in the 4/6 wired needed for the encoder, 2 for power and ground and the other 2 for the 2 poles of the coils acting as magnets. For the code, we used the example code
```
digitalWrite(12, HIGH);
digitalWrite(9, LOW); 
analogWrite(3, 255); 
delay(3000);
digitalWrite(9, HIGH); 
delay(1000);
//backward @ half speed
digitalWrite(12, LOW); 
digitalWrite(9, LOW);
analogWrite(3, 123); 
delay(3000);
digitalWrite(9, HIGH);
delay(1000);
```
This basically turned on one coil at a time, syncronising on-and-off with the other coil so the permanent magnet in the middle can attraact them and cause the motor to spin.

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
### Loop:
``` 
myservo.attach(9);
{
val = analogRead(potpin);
val = map(val, 0, 1023, 0, 179); 
myservo.write(val1);
delay(1);
}
```
After loading the code we tested it out with a potentiometer and it functioned well, despite the resolution of the potentiometer being quite low, which resulted in slight jiggles. After confirming it works, we then coded for another potentiometer, adding in additional lines and labeling each different potentiometer and servo. 

After this we had to design our very own robotic arm using a CAD software, we decided to go for a small arm as it would reduce the time it took to 3D print, after some design considerations we came up with this, with the stl files included

![robotarm](https://github.com/danstares/ROCO222/blob/master/Robotic%20Arm.jpg)
![arm stl](https://github.com/danstares/ROCO222/blob/master/Arm.stl)
![crane arm stl](https://github.com/danstares/ROCO222/blob/master/Crane%20Arm.stl)
![body stl](https://github.com/danstares/ROCO222/blob/master/Main%20Body.stl)

However the base wasnt heavy enough to handle the movement, so we had to hold it down to the table as the servos were gyrating.

## Controlling Robotic Arm with ROS
To do this, we first had to boot up Ubunto, as ROS is only functional on Linux. We plugged in our servo motors into our Nano board and used the following code to test if it works
```
void loop() {
for (pos = 0; pos <= 180; pos += 1) {
// in steps of 1 degree
myservo.write(pos);
delay(15);
}
for (pos = 180; pos >= 0; pos -= 1) {
myservo.write(pos);
delay(15);
```
This proved to be successful so we moved on to the nodes for ros on the terminal, We first had to start up roscore by typing in "roscore" into the terminal, after that we typed in "rviz" to initiate the program so we can visualise it, but the arduino IDE needed some add-ons or else the code would not work in conjunction with ROS, so using the terminal we installed the rosserial client and thus Arduino IDE was functional with ROS. Next was to control the servos with terminal commands, this can be achieved by coding as following 
```
#include <ros.h>
#include <std_msgs/UInt16.h>
#include <Servo.h>

using namespace ros;

NodeHandle nh;
Servo servo;

void cb( const std_msgs::UInt16& msg){
servo.write(msg.data); // 0-180
}

Subscriber<std_msgs::UInt16> sub("servo", cb);

void setup(){
nh.initNode();
nh.subscribe(sub);

servo.attach(9); //attach it to pin 9
}

void loop(){
nh.spinOnce();
delay(1);
}
```
Analysation of code: the line "Subscriber<std_msgs::UInt16> sub("servo", cb);" essentially subscribes the servo to a node we are working on, allowing the terminal to be linked to the servo control.

Now by calling the rostopic pub command we were able to move our servo with just a terminal, although this proved to be very clunky and adding more servos would mean to code did not scale well, with tons of lines being added, so we looked to control it with RVIZ.

We first had to download the sample .urdf file, which we stored in a directory of /project/Models,
![sample urdf](https://github.com/danstares/ROCO222/blob/master/arm%20in%20rviz.png)

This allowed us to load the file onto rviz using the command "rosparam set robot_description" in conjunction with "rosrun robot_state_publisher robot_state_publisher", which links it to rviz and "rosrun joint_state_publisher joint_state_publisher _use_gui:=true" which pulled up a slider bar that controls the servos. We then designed ourn robotic arm onto the urdf file, by some good old fashioned trail and error by measuring the arm and typing it in the file, the urdf file is complete

![urdf](https://github.com/danstares/ROCO222/blob/master/urdf.PNG)

Loading up the nodes once more we adjusted the sliders and it was fully functional, with the origins of the pivot points where we wanted them, here is a video of it functioning

![vid of rviz](https://github.com/danstares/ROCO222/blob/master/rosControl.mp4)

As you can see there are 2 sliders for each servo and both are working fine.




