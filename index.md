


## Introduction:

The Weeping Angels are a fictional monster originating from the popular British TV show, Dr Who, where these terrifying status monsters are a staple enemy. Our group’s goal was to recreate these monsters with robots using ROS. So how do Weeping Angels work? Weeping Angels in Dr Who are extremely fast beings that chase after people, but they can only move if no one is looking at them. Our robot is designed to do the same thing, follow a person and stop when they look at the robot. To achieve this end, we used person and facial recognition to track humans with a camera, and identify when someone is looking at the robot.


## Relevant Literature:

- Pytorch
- OpenCV

## Robot Description and Function:

The robot is the default configuration of a TurtleBot3 Waffle bot, it is a small flat robot consisting of 2 wheels to control the robot, on its top it contains both a LIDAR and RGB camera. The main functionality of this bot will be to recognize people and their faces, and then follow the person. If the robot detects that the person is facing the robot, the robot will come to a stop, and remain stopped till the person has turned away. While following the person, the robot should be able to avoid obstacles in its path and try to maintain visual contact with the person.
Due to limitations with tracking reliability and image processing runtime, the robot will maintain a set speed of 0.2 m/s when it is moving.


<iframe src="https://drive.google.com/file/d/1AMJsoFjG67R7mWGi57o4S_TQ9VjPxJQ5/preview" width="640" height="480" frameBoarder="0" allowFullScreen></iframe>
