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
* ## ls
+ shows components in this dir
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
## note four - mapping
+ roslaunch mx_bringup rbc_camera_start.launch(or mx_btingup rbc_lidar_start.launch)
+ roslaunch mx_nav gmapping_demo.launch
+ roslaunch mx_rviz gmapping_view.launch
+ !!!!if robot is not moving , try more controlling nodes , if still not work , reboot the system , if the same thing happens over and over , check if the motor driver is broken(happens when motor is overloaded for a time period which is too long)
+ avoid bumping into walls coz the map will be broken
+ when robot only drifts a little , it doesn't matter , some strong code will repair the damage to the maps
----
references :
+ [materials for md usage](http://markdown.cn)
+ [ros wiki](http://wiki.ros.org)
+ [usage of remap](http://wiki.ros.org/roslaunch/XML/remap)
+ [sunMaxwell's github](https://github.com/sunmaxwll)
