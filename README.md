# Jetson-Nano-Self-Driving-Car
   This is a project which uses deep Convolutional Neural Networks to steer a self driving car. It is powered by Jetson Nano and Arduino UNO.


<p align="center">
  <img width="300" height="275" src="https://user-images.githubusercontent.com/34810513/79965877-38c59100-84aa-11ea-9d23-f7f33091443c.jpeg">
</p>


   Neural networks are universal function approximators which can be used for different kinds of problems(Classification, Regression, Segmentation, etc). In this self driving car prototype, I have used regression(I have tried classification too but regression is the way to go) to predict the steering angle of a car by using the video feed of the path as input to the neural network. Use this GitHub Repo to help build your own Self Driving Car. You can also alter the code slightly to use a car with Ackerman Steering and Servo Motors instead of using the classic Line Follower styled Chassis that I have used. With that being said, lets get started.


## The Self Driving Car Concept

   This self driving car is a robot with four wheels powered by Arduino UNO, a Motor driver, a LIPO battery, 4 motors and wheels. The intelligent operations are carried out by NVIDIA's Jetson Nano board, which is a single board computer with GPU cores and CUDA support. The Jetson board processes the images obtained in real time from a web camera and feeds them into a Neural network with convolutional and fully connected layers. The neural network performs regression to predict the steering angle of the car and the angle is used to control the speed of the wheels of the robot, which makes it turn left, right or forward.

   To understand this, consider a computer game where a user can drive a car by pressing the arrow keys. In order for an AI to drive the car, it should be able to predict the key to be pressed and the duration for which the key should be pressed based on the steering angle. To do this, it obtains a screen shot of the game for every fraction of a second and passes it through a neural network. The neural network predicts the steering angle at that instant and the AI presses the appropriate key. This keeps the car at the center of the road as shown below.

<p align="center">
  <img width="325" height="200" src="https://user-images.githubusercontent.com/34810513/79974333-c3ac8880-84b6-11ea-8b67-1ee88e75583c.jpeg">
</p>

   Instead of making the AI drive the car in a computer game, we use real world data obtained from a robotic car prototype. The AI processes the real world feed and keeps the prototype at the center of the lane.

## Components And Connections

We used the following components to build our prototype:
 
 1) Eagle high discharge LIPO Battery (11.1V, 35C) - 1 pc.
 2) IC-7805 regulators - 4pcs.
 3) L298N motor driver module - 1 pc.
 4) 300 RPM Motors - 4 pcs.
 5) Arduino UNO - 1 pc.
 6) NVIDIA Jetson Nano board - 1 pc.
 7) I-Ball Web Camera - 1 pc.
 8) Metal Chassis - 1 pc.
 9) Wheels - 4 pcs.
 10) Wires and Jumper Cables - as per required.
 11) Metal spacers - 4 pcs
 12) Perf Board - 1
 
 #### Custom regulator circuit
 
   The Jetson Nano board is a troublesome board. There are 2 major ways through which you can power the board. The first method is to use a 10W micro USB mobile charger and power the board through its micro USB port. Though this is handy and quick, it is not the best way to power the board. Although we can make the project portable using powerbanks, the board automatically switches off when the pwoer drawn by it exceeds 10 Watts. This makes it virtually impossible to use it for projects like our self driving car. Thus, the DC barrel Jack of Jetson Nano can be used to power the board. To do so, a small jumper should be fit into Jetson's J48 pins(For more info visit: https://www.jetsonhacks.com/2019/04/10/jetson-nano-use-more-power/). Once this is ready, we have to power the Jetson board using the LIPO battery. The LIPO battery is powerful and allows high current discharge. However, it supplies a voltage of 11V which will damage the board. This is why we need the 4 regulator ICs each IC has a maximum current rating of 1.5A. Thus connecting 4 of them in parralel lets us draw around 4 Amps of current with a voltage of 5V(20 Watts). This Acts as a stable power supply which can be used in our project.

<p align="center">
<img width="275" height="250" src="https://user-images.githubusercontent.com/34810513/79977737-5f8cc300-84bc-11ea-94d3-12505b291ee8.jpg">
<img width="275" height="250" src="https://user-images.githubusercontent.com/34810513/79977923-b5616b00-84bc-11ea-901e-10539c5d49f6.jpeg">
<img width="275" height="250" src="https://user-images.githubusercontent.com/34810513/79978174-14bf7b00-84bd-11ea-8610-51e7a5e3629b.jpeg">
</p> 

<p align="center">
  The custom regulator circuit. a) Circuit Diagram (Left) b) Top View (Center) c) Bottom View (Right)
</p>

#### Circuit

   Once the custom regulator circuit is ready, it is time to build the complete circuit. Use the circuit diagram shown below to make the connections. In addition to this, connect Motors 3 and 4 in parallel with motors 1 and 2 respectively. The spacers can be elevate the position of the Jetson board which makes it easier to fit all the components onto a small chassis. Feel free to tinker with the design.
   
<p align="center">
  <img width="580" height="640" src="https://user-images.githubusercontent.com/34810513/79979248-d925b080-84be-11ea-9f89-b81b1eadd50b.jpeg">
</p>






