# Mathematical-models-


How to Calculate a Robot's Forward Kinematics ?

Calculating kinematics is a cornerstone skill for robotics engineers. But, kinematics can sometimes be a pain (e.g. understanding the difference between forward and inverse kinematics).

Even though I had learned  and I am still learning the theory of kinematics in university, it wasn't until I had calculated various kinematic solutions for  robots until I participated to Smart Methods company for industry robots and autonomus system , because I was not calculating kinematics every day I had to go back to my notes to remind myself how to do it every time .

Step 1: Get a pencil and paper

It can be tempting to jump straight for your computer when starting with a new robot. However, even if the robot looks like a "standard" 6R manipulator (the most common robot type) I always sit down with a pencil and paper to draw out the kinematic diagram.

This simple task forces you to carefully consider the actual physical configuration of the robot.

There are various ways to draw a kinematic chain. Pick whichever style you prefer.I favor simple cylinders for the revolute joints and lines for the links, as shown in the image. Do a Google Image Search for "kinematic diagram" and see some of the different styles available.

As you draw, work out which way each joint moves and draw this motion as double-ended arrows onto the diagram.

![image](https://user-images.githubusercontent.com/86304831/128053183-454d25e1-4063-4bfa-8b1a-942e55fba3bd.png)



Step 2: Figure out your axes
The next key step is to draw the axes onto each joint. The DH approach assigns a different axis to each movable joint.
If you set up your axes correctly then working with the robot will be easy. 


The two important axes to work out are:

Z-axis — The z-axis should lie on the axis of rotation for a revolute joint or axis of extension for a prismatic joint.
X-axis — The x-axis should lie along the "common normal", which is the shortest orthogonal line between the previous z-axis and the current z-axis .


Alternatively, you can use the "right hand rule".


The right hand rule
A quick and easy way to remember the direction of your y-axis is to follow the right hand rule. 

To use it, hold out your right hand in front of you, sticking out your thumb, index finger, and middle finger at 90 degrees to each other. Each finger then corresponds to an axis:

Thumb = z-axis. 
Index finger = x-axis. 
Middle finger = y-axis.
By orienting your thumb and index finger to follow the z and x axis of the robot joint, your middle finger will naturally fall into the direction of the y-axis. 

Step 3: Remember your end effector
ROBOTIQ-3-FINGER-DH-PARAMETERS

The goal of calculating the Forward Kinematics is to be able to calculate the end effector pose from the position of the joints.

Most Forward Kinematic tutorials will generalize the end effector as a single distance from the final joint. This is fine for a simple "open-close" gripper. However, as modern grippers are often more complicated than this, it's worth considering how the end effector operates.

For example, the Robotiq 3-Finger Adaptive Gripper has a few different gripping modes. Each mode will correspond to a slightly different desired end effector pose. If you want to pinch the object between its fingers, this will require a different distance than if you wanted to wrap the fingers around the object. 

You should always consider the end effector carefully when formulating the kinematic model.

Step 4: Calculate the DH parameters
Denavit-Hartenberg (DH) parameters are often required to enter the robot model into a simulator and start performing any sort of analysis on it.

The best way to visualize the DH parameters is to watch the video I already included above.

The DH parameters break down each joint of the robot into four parameters, each taken with reference to the previous joint. They are calculated in reference to the "common normal" described above. Note that if the previous z-axis intersects the current z-axis, which is often the case, the common normal has a length of zero.

d - the distance between the previous x-axis and the current x-axis, along the previous z-axis.
θ - the angle around the z-axis between the previous x-axis and the current x-axis.
a (or r) - the length of the common normal, which is the distance between the previous z-axis and the current z-axis
α - the angle around the common normal to between the previous z-axis and current z-axis.
Go through each joint on your drawing and write down the DH parameters for each joint. Each joint should have one value which is a variable, representing the actuated joint. 



Step 5: Combine parameters into a whole robot
The final step is to combine all of your DH parameters into an entire robot. There are two ways :

The first way: Create your own solver

The "purist" method of using the DH parameters is to "roll your own" Forward Kinematic solver using your favorite programming language. 

Once you have your DH parameters for each joint, you can use this method to code it into a Forward Kinematics solver:

1- Find a library in your programming language which allows you to do matrix multiplication. Alternatively, code your own using the methods in this list. 
2- For each joint of the robot, populate a new 4 x 4 matrix with the following values:
Forward_Kinematics_Matrix

3- Multiply all of the matrices together, starting with the first joint all the way up to the end effector.
4- The final T vector will contain the position of the end effector. The R matrix will contain the orientation of the end effector. 
If you just want to try this out with some values, without coding your own solver, you can use this handy online tool to create a worked example of a complete robot from its DH parameters.


The second way:Use existing libraries

A far more effective way to calculate Forward Kinematics, once you've got your DH parameters, is to use an existing library.

There are loads of kinematic software libraries and many of them do far more than just calculate Forward Kinematics. Most of them include Inverse Kinematic solvers, dynamics, visualization, motion planning and collision detection, to name just a few features. These libraries will transform your DH parameters into matrices, which are then multiplied together to calculate the relationship between joint positions and end effector pose.

Some good development libraries include Robotics Library, Orocos Kinematics and Dynamics Library, ROS MoveIt, OpenRave, RoboAnalyzer, and the Matlab Robotics Toolbox.



For more information : http://motion.cs.illinois.edu/RoboticSystems/Kinematics.html
