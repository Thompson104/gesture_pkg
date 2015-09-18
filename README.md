# gesture_pkg

This repository is a combination of hand gesture detection code and the corresponding launch files for the detection codes. This repository as a simple gesture detection code uses the webcam or the kinect camera to detect the gesture made by the user and performs some basic operations accordingly. The user has to perform a specific gesture. The webcam or kinect camera captures this gestures as  frames and displays it. Further, the code extracts the ROI(region of interest or otherwise called background subtraction), finds the the contours, then finds the convexity defects after drawing the convexity hull and then uses the number of defects to perform some basic gestures like counting number of fingers and hand waving. 

The code is not much difficult to understand and add any other features but needs hard work-through and mastering on OpenCV(Open Source Computer Vision Library), which was developed by Intel as a library of programming functions mainly aimed at real-time computer vision. For more information [click here](http://opencv.org/)  

## Install
We need to install either of the following pairs of ros packages to be able to use the ros usb node and openni-camera/kinect.. 

`{ros-indigo-openni-camera, ros-indigo-openni-launch }` - Recommended

`{ros-indigo-openni2-camera, ros-indigo-openni2-launch}`

` eg. sudo apt-get install ros-indigo-openni-camera `

Install the following packages for transporting ros images into opencv matrix images->cv-bridge

`{ros-indigo-cv-bridge , ros-indigo-usb-cam , ros-indigo-image-transport}` 

` eg. sudo apt-get install ros-indigo-cv-bridge`

## Build
To build gesture_pkg as ros package, perform the following steps at the shell prompt(in the terminal)

`cd ~/catkin_ws/src/`

`git clone `

`cd cd ../`

`catkin_make`

`source ./devel/setup.bash`


## Run
In some cases we need to set value for camera parameters by using the following command even after setting it in the launcher file.

`rosparam set usb_cam/pixel_format yuyv`

Use either of the ros based launch files... no need to start every services separately but just roslaunch the gesture recognizer code using one of the following two terminal commands.

**`roslaunch gesture_pkg cam_gesture_recognizer.launch`** - for usb camera

**`roslaunch gesture_pkg kin_gesture_recognizer.launch`** - for kinect camera

In the case of usb camera... some important published topics are: 
#### /gesture_channel

#### /rgb/camera_info

#### /rgb/image_raw
 
#### /rgb/image_raw/compressed
