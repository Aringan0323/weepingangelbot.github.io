---
title: Reflections
description: Our process towards the final product
layout: default
---

# Limitations

For the most part the final product presented operates exactly how we expected it. Improvements can be achieved through further calibration of the Object avoidance code, and a potential addition of a person location memory, so that if the robot loses sight of the person, it can smartly relocate them.

However, the project faces major hardware limitations. Though the person/facial recognition and object avoidance codes work as intended, the runtime of the person/facial recognition code causes significant lag in the simulation. As of now, the only way for us to gather reasonable results is to slow down the simulation to 1% speed compared to real time. Though this is mostly a hardware limitation, as testing of the code on computers outside of the virtual environment for which we simulated on, garners us equal, if not better, results in real time as opposed to .1% time.

In order to have the program to run in real time, it would be necessary to run the person/facial detection model on a GPU during runtime. The model used has over 5 million parameters and would benefit significantly from the parellelization that GPUs have to offer. Running the model on an Nvidia RTX 2070 super achieves a frame rate of roughly 15-20 frames per second, which would be ideal for this project.

# Teamwork

## Contributers

### Nathan Cai

- Created and deployed world and launch files to include the Cafe setting and human model in the Gazebo simulation.
- Wrote the node that subscribes to the person centroid and face topics published by the detector and implements the behavior of the Weeping Angel in the turtlebot.
- Recorded and edited the video presentation for this project.
- Contributed to this website and the README.md on the github repository for this project.

### Adam Ring

- Fine-tuned FasterRCNN Model to recognize both faces and people.
- Deployed the fine-tuned model in the virtual environment.
- Wrote the detection node, which subscribes to the camera topic produced by the turtlebot and publishes topics holding data about the centroid of the person detected and whether or not a face is detected in the frame.
- Made contributions to this website and the README.md in the github repository.

# Final Thoughts

This project proved a challenge not only in robotics programming, but also in Gazebo configuration, code deployment, web development, and making compromizes. Our initial direction with this project was to use simple OpenCV detection for facial detection and person recognition. However this initially proved to be unsuccessful due to both the limitations of OpenCV and the inaccuracy of the models used. The challenge that we needed to overcome was to find a model for detection that would be concise, yet generalizable outside of Gazebo if we were to implement this program with a real Turtlebot3 waffle. Once we developed the best model for person and face recognition, the challenge became how we would deploy the model and implement the obstacle avoidance in Gazebo. This proved to be even more of a challenge, however we eventually were able to reach the compromize of slowing down the simulation and recording it over a period of time to see the results. If we had more time with this project, we would attempt deployment with a real Turtlebot3 Waffle and run the code using a system with an integrated GPU.
