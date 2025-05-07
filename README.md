# Structure from Motion-based Depth Estimation in Indoor Environments for Tello Drones
This repository consists of an implementation of an ORB feature point depth estimation via Structure from Motion using a Tello Drone's camera feed and VICON. We used a Tello Drone to get the camera sequence to process but you can do it with any kind of mobile robot that you want. For more details about the theory and experiments behind this work, see [this file](./Documentation.pdf).

**<ins>PS</ins>. This repository is not finished yet, additional files are waiting approval to be committed​​ ‼️​**

## Table of Contents
- [ORB Feature Extraction](#orb-feature-extraction)
- [Tello Drone Tracker](#tello-drone-tracker)
- [Depth Estimation](#depth-estimation)
- [Contact](#contact)

## ORB Feature Extraction
- Make sure your camera is callibrated, you can easily do that using MATLAB's *CameraCalibrator* app.
- Add your camera feed to your workspace and run [orb_ft.py](./ORB_ft.py). 
- Extract the image coordinates of your ORB feature point as a *.csv* or *.mat* file.

## Tello Drone Tracker
- Place a minimum of 3 markers on both the drone (or your robot) and the target point
- In the VICON software, add each object as a VICON frame.
- Establish a private IPv4 connection between the VICON host pc and your own computer.
- Track the objects as they move in your environment and export the tracked data as a *.csv* file. Or use the [vicon_bridge](https://github.com/ethz-asl/vicon_bridge.git) package and listen to the ROS topics of your interests.
- Import your ground truth data to your workspace and run [GT.ipynb](./GT.ipynb).

## Depth Estimation
- Render your data as a *.mat* file and import it to your workspace.
- Install the [yalmip](https://yalmip.github.io/) toolbox and the [SDPT3](https://yalmip.github.io/solver/sdpt3/) solver as well.
- Run [LMIs.m](./LMIs.m) to calculate the observer gain (make sure your velocity equations respects the fixed fuzzy bounding, see [the project's report](./Documentation.pdf) for more details).
- Run [SFM_qlpv.slx](./SFM_qlpv.slx) to get the depth estimation. Please note that the qLPV camera model is used as the depth's ground truth here for the sake of checking the observer's performance.

## Contact
Feel free to explore the project and its files. If you have any feedback or are facing any technical issues, please report to the issues tab. If you want to add more features on this work, don't hesitate to fork this repo.

- [Linkedin](https://www.linkedin.com/in/yhadj/)
- [Email](mailto:y_hadj@outlook.com)
