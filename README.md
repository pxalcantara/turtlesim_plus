# turtlesim_plus
It's a package based on `turtlesim` simulator for ROS adding some extra functionalities. The idea of this project is keep the traditional funcionalities of the tutlesim and, on top of it, add more funtionalities so others can use this helpfull tool to teach more advanced topics in mobile robots. The code was build from the [original code](https://github.com/ros/ros_tutorials/tree/noetic-devel/turtlesim).

## Features

### Original Features
  To the original features, there is the [Turtlesim Wiki page](http://wiki.ros.org/turtlesim) with a really good documentation and a lot of tutorials.
  
### New Features

#### Topics

1. ***turtleX/range_color_sensor***([turtlesim/Color](http://docs.ros.org/api/turtlesim/html/msg/Color.html))   
    It's a sensor that get the color ahead the turtle, similar to a *range_sensor*. Instead of measure the distance, given a certain distance, this topic gives you the RGB values of the pixel in that distance. The diference from the *turtleX/color_sensor* in the original `turtlesim` is, this topic gives you the RGB color underneath the turtle, not ahead.


