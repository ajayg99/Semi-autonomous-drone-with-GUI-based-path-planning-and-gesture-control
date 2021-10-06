# Semi-autonomous-drone-with-GUI-based-path-planning-and-gesture-control
This project provides a solution for the first responders to gather insights of the current condition and devise strategic plan for search and rescue without risking their lives.

## Autonomous Indoor Navigation
Used PEDRA to train the drone on Indoor environment(unreal engine) and applied transfer learning -<a href="https://github.com/aqeelanwar/PEDRA" target="_blank">PEDRA</a><br />
Indoor navigation Model - <a href="https://drive.google.com/drive/folders/1QFDFtnpl3PFECgX6Z_uvRoaxcXmPd-5P?usp=sharing" target="_blank">Model</a>

##### Output
![image](https://user-images.githubusercontent.com/45633028/136217727-3203775f-bab3-4f2b-af24-ed4ef248edd7.png)<br />
![image](https://user-images.githubusercontent.com/45633028/136217844-80822b8b-73be-425d-b756-59257c9a5b7a.png)<br />



## Outdoor navigation- GUI based path planning.
![image](https://user-images.githubusercontent.com/45633028/136208482-a7ff5392-da53-451a-ae03-c5373667d982.png)<br />
The path planning is done using pyGame (a python module). The pygame window is set out with a birdview image of the scouting area. On simple mouse clicks of the various points on the map, the system figures out a trajectory path and maps it to the actual flight distance of the drone. The system then maps these paths to the actual flight path and transmits the same to the drone within a low Wi-Fi Range while providing live camera feedback on the system.<br />
Distance calculation between the co-orinates: √((x_2-x_1)²+(y_2-y_1)²) </br >
Angle calculation between the vector: Angle in deg = (measured angle in radians * 180 / value of pi)
##### **Distance way point mapping**
The distance calculated in terms of pixels is converted into centimeters using a simple coefficient formula as shown below. Based on the scaling of the image to the real-world projection of the region, the coefficient is calculated by the formula shown below:
Map Coefficient = Actual Distance in cms / Number of pixels in GUI ere, the value of this conversion as scaled is 70px = 360 cm thus, making the value of the map_coeff = 360/70 = 5.14

This conversion allows direct conversion of points on the GUI to be mapped onto way-points in real world thus enabling easier transmission of distance to be travelled by the drone. The angle calculated also enables us to identify the angle in which the drone needs to turn before proceeding to the next way-point, thus giving us a full-fledged way-point mapping from the GUI to the real world.
Thus, while mapping each point as when click on the GUI, the distance and angle are calculated and are appended into a JSON file in the with the following properties:
Direction
Angle to turn degree
Distance to travel
Speed of the drone
These values are appended into the JSON file for every way-point mapped on the GUI and are readily accessible to the drone</br >
##### **Drone Navigation Through Json Parsing**
In order to communicate with the drone. The drone first needs to be connected to the workstation through a common Wi-Fi connection hosted by the drone. The JSON file is parsed with the help of an inbuilt python module named json. This helped load all the way-points of the path into key-value pairs that can be integrated through with ease.
For every way-point obtained from the JSON way-point file, the distance and angle are printed for reference and are communicated to the drone directly using the drone controller framework provided in python.

NOTE : The drone angles comprehended are conventional and the rotation of the drone must always be in the clockwise direction so as to get the desired mapping of way-point in real-world navigation

##### Output
![image](https://user-images.githubusercontent.com/45633028/136218085-ad222366-c7bb-41d5-b5a9-d9179d02c28e.png)<br />
![image](https://user-images.githubusercontent.com/45633028/136218115-7cfbf1d4-fa6c-48a8-bb03-b82282c88762.png)


## Object Detection
Used yolov3 algorithm

##### Output
![image](https://user-images.githubusercontent.com/45633028/136217968-c3006c1c-1918-495d-a106-3d83652bd372.png)<br />

## Hand Gesutre Recognition
The basic motive behind this module is to provide a user friendly access of the drone to select the mode of deployment. The hand gesture detection is carried out using a computer vision program that finds the number of fingers with the help of  a convex hull algorithm and maps it to a bit wise AND operator. This detects and recognises the hand gesture and can be mapped to change the modes of a drone or change it’s motions, as demanded.
The hand gesture control could also be used to remote scouting as a method to give as an input to the feed on the workstation which then communicates with the drone to perform a particular activity.

##### Output
![Screenshot 2021-10-06 193614](https://user-images.githubusercontent.com/45633028/136219132-5316be1b-3fef-4403-8231-4884dd712c5a.png)

## GUI
![Gui](https://user-images.githubusercontent.com/45633028/136219242-354a234b-d006-466a-acc4-303773a1aae6.png)
