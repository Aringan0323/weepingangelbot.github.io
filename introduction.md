---
title: Introduction
description: A brief overview of the project
layout: default
---

# Introduction:

If you have ever watched the beloved sci-fi television show Doctor Who, you already know exactly what this robot does! But if you have not seen the show, I will provide a brief explanation of the functionality of the robot.

Or goal for this project was to recreate the behavior of the Weeping Angel from Doctor Who. The Weeping Angel monster is a large stone statue of an angel-like creature which looks relatively inconspicuous at first glance. However, when one looks away from this statue, it will come to life and chase the victim down, sending it back in time when it reaches them. While inventing a time machine for this project proved to be a bit harder than we thought, we were able to implement the physical behavior of the Weeping Angel monster in the setting of a Gazebo simulation with a humanoid model and a Turtlebot3 Waffle simulated robot.

In the simulation, we have a Turtlebot3 Waffle robot with a camera on the font of it, and a fully mobile and animated humanoid model. The human model walks in a predifined path, while the robot follows it around the room. A ROS node subscribes to the image topic produced by the robot's camera, and processes it using a convolutional neural network to detect the position of faces and people in the image. If the processing node detects a person, but not a face in the robot's camera image it will publish cmd_vel topics to the robot that tell it to follow the person. If the node detects a face in the camera image, it will publish cmd_vel commands telling the robot to stop in place. If the robot detects no people or faces in the camera image, it will publish commands that tell the robot to wander around the map as if to search for new victims.

# Relevant Literature

- [Publishing and Subscribing to ROS topics](http://wiki.ros.org/ROS/Tutorials/UnderstandingTopics)
- [Neural Network Introduction](https://wiki.pathmind.com/neural-network)
- [FasterRCNN](https://arxiv.org/abs/1506.01497)
- [Fine Tuning a Neural Network](https://pytorch.org/tutorials/intermediate/torchvision_tutorial.html)
- [PID Controller](https://en.wikipedia.org/wiki/PID_controller#:~:text=A%20proportional%E2%80%93integral%E2%80%93derivative%20controller,continuously%20calculates%20an%20error%20value)
- [Importing a Human Model into Gazebo](http://gazebosim.org/tutorials?tut=actor&cat=build_robot)
