---
title: Technical Overview
layout: default
---

# Robot Description and Function:
The robot is the default configuration of a TurtleBot3 Waffle bot, it is a small flat robot consisting of 2 wheels to control the robot, on its top it contains both a LIDAR and RGB camera. The main functionality of this bot will be to recognize people and their faces, and then follow the person. If the robot detects that the person is facing the robot, the robot will come to a stop, and remain stopped till the person has turned away. While following the person, the robot should be able to avoid obstacles in its path and try to maintain visual contact with the person.Due to limitations with tracking reliability and image processing runtime, the robot will maintain a set speed of 0.2 m/s when it is moving.

# Person/Facial Recognition

# Model Training and Deployment

## Training

## Deployment

# Person Following

The robot achieves its ability to follow a person by using a centroid. The centroid designates the central point of a person in an image. By comparing the location data of the centroid to the image, we can get a value that represents the horizontal position of the person being followed relative to the robot. We achieved this by comparing the x-axis offset of the centroid to the center point of the camera image. With this offset determined, we can convert this offset into an angular velocity that will steer the robot in the direction of the person. This method of steering provides quite reliable results if calibrated correctly, this is due to how the steering is based off the centroid offset from the center. This naturally causes the steering values to adjust in strength based on the person’s location, as the farther from center the person is from the robot camera, the higher the offset value and thus higher the steering strength.

# Object Avoidance

The robot achieves object avoidance by using the sensor data from the Wafflebot’s builtin LIDAR sensor. The object avoidance code works by first splitting the 360 degree LIDAR data into 3 parts: front, left, and right. These cones, size of which are adjustable, help determine if an object is blocking the robot’s path and which direction for the robot to turn. The code does this by comparing the minimum distance values of each cone. First to determine if there are obstacles in the robot’s path warrants the need to turn, if so it will then determine how hard it needs to steer and in which direction. We get the direction by getting the difference between the minimum values of the left and right LIDAR cones. This is based on the assumption that the side that has the largest minimum distance value will be the side in which the robot has the most room to maneuver away in.  This difference comparison yields us a positive or negative integer, whose sign is used to determine the direction of turn and whose magnitude is used to determine the strength of steering.

The steering code, however, is not entirely separate from the Person following code. Since both the object avoidance and the person following both output an angular velocity value, we can combine both values together to achieve a tandem effect. This is where the object avoidance will keep the robot from a collision, while the person following  will compensate to maintain visual contact with the person. Though in an ideal system these two values would always be working together, this is not always the most effective case. Due to strange obstacle geometry, the person’s movement, or changes in terrain, the code will ignore the person following steering value in situations where safe object avoidance has failed, and the robot needs to turn aways quickly to avoid collision.

# Importing a Human Model into Gazebo

Importing a human model into Gazebo plays a major part in the project as we needed to find a way to compensate for the lack of access to physical components. Due to the COVID 19 Pandemic, we were limited in our ability to test our code, so the solution to this was to do all our testing in simulation. To this end we importanted a human model with walking animations into a Gazebo world to replace the need for an actual human figure. This is not to say that we did not do actual tests to see if our human recognition code worked on real life people, but the need to a 3-dimensional world for our robot to operate in meant that the human model was needed in Gazebo to properly test out robots.

Importing a human model into Gazebo is achieved by importing a .dae model into Gazebo as an actor, and assigning it the animation set embedded in the .dae model. For the human model, we used the standard walking model native to the Gazebo ecosystem, as it was the most stable and least expensive model. The walking model can be described as a bald, middle aged, cocasian man wearing a dark green shirt and dark green sweatpants.
