


## Introduction:

The Weeping Angels are a fictional monster originating from the popular British TV show, Dr Who, where these terrifying status monsters are a staple enemy. Our group’s goal was to recreate these monsters with robots using ROS. So how do Weeping Angels work? Weeping Angels in Dr Who are extremely fast beings that chase after people, but they can only move if no one is looking at them. Our robot is designed to do the same thing, follow a person and stop when they look at the robot. To achieve this end, we used person and facial recognition to track humans with a camera, and identify when someone is looking at the robot.


## Relevant Literature:

- Pytorch
- OpenCV

## Robot Description and Function:

The robot is the default configuration of a TurtleBot3 Waffle bot, it is a small flat robot consisting of 2 wheels to control the robot, on its top it contains both a LIDAR and RGB camera. The main functionality of this bot will be to recognize people and their faces, and then follow the person. If the robot detects that the person is facing the robot, the robot will come to a stop, and remain stopped till the person has turned away. While following the person, the robot should be able to avoid obstacles in its path and try to maintain visual contact with the person.
Due to limitations with tracking reliability and image processing runtime, the robot will maintain a set speed of 0.2 m/s when it is moving.


## Person/Face Recognition:

## Model Training and Deployment:

### Training:

### Deployment:

## Person Following:

## Object Avoidance:

The robot achieves object avoidance by using the sensor data from the Wafflebot’s builtin LIDAR sensor. The object avoidance code works by first splitting the 360 degree LIDAR data into 3 parts: front, left, and right. These cones, size of which are adjustable, help determine if an object is blocking the robot’s path and which direction for the robot to turn. The code does this by comparing the minimum distance values of each cone. First to determine if there are obstacles in the robot’s path warrants the need to turn, if so it will then determine how hard it needs to steer and in which direction. We get the direction by getting the difference between the minimum values of the left and right LIDAR cones. This is based on the assumption that the side that has the largest minimum distance value will be the side in which the robot has the most room to maneuver away in.  This difference comparison yields us a positive or negative integer, whose sign is used to determine the direction of turn and whose magnitude is used to determine the strength of steering.
	The steering code, however, is not entirely separate from the Person following code. Since both the object avoidance and the person following both output an angular velocity value, we can combine both values together to achieve a tandem effect. This is where the object avoidance will keep the robot from a collision, while the person following  will compensate to maintain visual contact with the person. Though in an ideal system these two values would always be working together, this is not always the most effective case. Due to strange obstacle geometry, the person’s movement, or changes in terrain, the code will ignore the person following steering value in situations where safe object avoidance has failed, and the robot needs to turn aways quickly to avoid collision.


## Importing a Human Model into Gazebo:

## Stretch Goals:

## Limitations:

## Teamwork:

## Final Thoughts on Project


<iframe src="https://drive.google.com/file/d/1AMJsoFjG67R7mWGi57o4S_TQ9VjPxJQ5/preview" width="640" height="480" frameBoarder="0" allowFullScreen></iframe>
