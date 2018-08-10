<font color=#66ccff>by lty4ever</font>
# Day1
## note one - ways to use md
normaly we put a "#" before words for a title , "##" before a mainpoint and "*" before a list component in a list , to put in plain words , we just create a new line and type words into it.
+ for a link we use the following format
+ [百度](https://baidu.com)
+ a pair of [] which contains the word want to show with a pair of () which contains the website want to link to
+ [-=-]=-=(-=-)
## note two - ways to use terminal in linux
* press ctrl + alt + t to open terminal at Home of your user.
* ## cd
* ## ls: show components in this dir
+ type nothing after cd goes back to ~(Home)(the same use as typing ~)
not only / means the root which can be used as a standard when getting into dirs , the ~ which means Home can also be used this way
* ## mkdir
+ dirname to make this dir here
+ (-p) + dirname/dirname/dirname to make dirname/dirname/dirname here
+ dirname dirname dirname to make dirname dirname and dirname here
* ## touch
+ used almost the same way as mkdir
* ## gedit
+ filename to open filename using gedit
* ## man
+ codename to show the usages of the code
* ## press tab to fill in automatically according to what is already typed in
mind that there's two situation when tab is pressed
	1. no conflicts occurs , fill in complished
	2. conflicts occurs , nothing happens . If tab pressed a second time , all possible dirs appears with thier names.
## note three - begining ros
+ turtle bot
+ open a terminal
+ roscore
+ open another terminal
+ rosrun turtlesim turtlesim_node
+ open another terminal again
+ rosrun turtlesim turtle_teleop_key
+ the third terminal must get focus
## note four - basic rules of ros
+ the system is separated into nodes topics and the ROS Master
+ firstly , master should be ran
+ secondly , nodes are ran and regist themselves to the Master e.g. what topic they will publish or subscribe
+ when Master find two nodes have a bond , it gives the control to the two nodes and the nodes will get each other known
+ the subscriber checkout the topic continuously
## note five - basic codes for ros
+ roscore -run master
+ rosrun pakagename nodename -run node and regist to the master
+ rostopic echo topicname -subscribe topic within this terminal
+ rostopic info topicname -show lists of publishers and subscribers
+ rostopic list -listout all the topics available
+ rqt_graph -show a publisher_topic_subscriber graph in the whole program
# Day2
## note one - ways to make a work space and a pakage
+ firstly , a empty dir with proper name should created (normally named as ..._ws)(should contain a sub dir named src)
+ secondly , get into the _ws dir
+ catkin_make to compile the work space
+ once we compiled a dir , sub dir build and devel created , src get new file CMakeLists.txt
+ catkin_create_pkg pakagename languagename(rospy or roscpp) to make a pakage
+ get into devel
+ source setup.bash to use socks to add bash file into environment arguements
+ roscd pakagename to get to a pakage dir quickly
+ create a dir named launch under pakagename dir
+ get into it and make a launch file named properly
+ gedit it
+ the format of the file should be like the one down here
+ <=====launch=====>
+ <=====node name="whatever" pkg="pakagename" type="nodename" /=====>
+ <=====node name="tyzl" pkg="turtlesim" type="turtlesim_node" /=====>(example , the real format should get rid of the (=====)s)
+ <=====/launch=====>
## note two - additional code used to merge two topics
  1. <=====node name="tyzl" pkg="turtlesim" type="turtlesim_node" (used to have a "/" here , deleted)=====>
     <=====remap from="original topic" to="destination topic" /=====>
     <=====/node=====>
  2. rosrun topic_tools relay originalTopic destinationTopic
## note three - including a launch file in another
+ <=====include file ="$(find pkgname)(/launch)/filename.launch"/=====> (/launch) means it is needed most of time
+ when a launch file includes itself , it will be forbidden even if it ran
+ forbidden also works when two launch file includes each other
# Day3
## note one - avoid controling the robot on such a small screen
+ review XD
+ plug sensors into computer through a lengthen wire (at least usb3.0) so that every thing could be seen more clearly
+ when errors like "no cameras detected" appears , keep the wire linked while get the computer reboot
## note two - SLAM
+ mapping while locating
+ a robot starts at some where unknown , the robot moves , detects the environment , enhance a map while locate itself in the map
## note three - route planning
+ global planning - starting point , destination , route
+ local planning - when crash into trouble , whether change the route/way or not
+ there mainly 2 algroithms used to plan a route - A* and Dijkstra's
+ A* is the most quickly one in the direct searching while D's is the most usual one
+ the main principle of the dynamic window algorithm -
	1.given the state of the bot
	2.according to the speed and other elements dicide the best route
	3.repeat
## note four - mapping
+ roslaunch mx_bringup rbc_camera_start.launch(or mx_btingup rbc_lidar_start.launch)
+ roslaunch mx_nav gmapping_demo.launch
+ roslaunch mx_rviz gmapping_view.launch
+ !!!!if robot is not moving : 
	1.try more controlling nodes 
	2.if still not work , reboot the system 
	3.ensure the circuit is complete (the switch is off)
	4.if the same thing happens over and over , check if the motor driver is broken(happens when motor is overloaded for a time period which is too long)
+ avoid bumping into walls coz the map will be broken
+ when robot only drifts a little , it doesn't matter , some strong code will repair the damage to the maps
## note five - radars
+ normal lidar - spins and culculates using triangular similation
+ solid lidar - doesn't spin and culculates diatance using [data deleted]
# Day4
## note one - basical python
+ cv2.waitKey(number) makes the program stay on this line of code till the wanted key is pressed
+ cv2.waitKey(0) means wait for anykey
+ cv2.imshow('label',a variable contains a img) pops up a form with a img titled label
## note two - use python to code a ros node
+ the first line of program should be "#!/usr/bin/env python" or the program will not know use which program to run itself
+ rate = rospy.rate(Hz) using together with rate.sleep() will make the while loop run at (Hz)Hz
+ 'I coded the program and saved it , I also sourced the bash file , why can't I find it when I press Tab in Terminal?'
+ the program should be set to be a executable one so that it could be found
+ to set program into a executable one , mouse 2 on the file in the resource manager , mouse 1 on properties , selece Permissions and put a tick in the checkbox labeled execute
## note three - neural network
+ CNN - Convolutional Neural Network - used for image recognizing
+ DNN - Deep Neural Network - used for voice recognition
+ RNN - Recurrent Neural Network - used for writing or voice recognition
+ trained using different frames - tensorflow / caffe /...
+ the process of using neural network to classify pics/tracks/marks is separated into three steps
	1.pick a frame , train a network
	2.pack the net work into a graph file and post it into the movidious which we will work with so that less tine will be cost
	3.post the object into the movidious and wait for a result
+ python two separately upgraded versions , movidious works with only python3 and at least usb 3.0
----
ref erences :
+ [materials for md usage](http://markdown.cn)
+ [ros wiki](http://wiki.ros.org)
+ [usage of remap](http://wiki.ros.org/roslaunch/XML/remap)
+ [sunMaxwell's github](https://github.com/sunmaxwll)
