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

Have a look at this video to see how to set them up:
For more information : http://motion.cs.illinois.edu/RoboticSystems/Kinematics.html
