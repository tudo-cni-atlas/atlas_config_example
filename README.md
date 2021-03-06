# atlas_config_example

## Overview

This is a configuration example for the the [ATLAS Real-Time Localization System (RTLS)](https://github.com/tudo-cni-atlas/atlas_rtls/).

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.2579940.svg)](https://doi.org/10.5281/zenodo.2579940)


### License

The source code of the localization is released under [BSD 3-Clause license](LICENSE).

**Authors:** Janis Tiemann, Yehya Elmasry

**Maintainer:** Janis Tiemann, janis.tiemann@tu-dortmund.de

**Affiliation:** Communication Networks Institute (CNI), TU Dortmund University

### Publications

If you use this work in an academic context, please cite the following publication(s):

* J. Tiemann, Y. Elmasry, L. Koring, C. Wietfeld, **ATLAS FaST: Fast and Simple Scheduled TDOA for Reliable Ultra-Wideband Localization**, In IEEE International Conference on Robotics and Automation (ICRA), Montréal, Canada, May 2019. (accepted for presentation). 

        @InProceedings{Tiemann2019atlasfast,
                Author = {Janis Tiemann and Yehya Elmasry and Lucas Koring and Christian Wietfeld},
                Title = {ATLAS FaST: Fast and Simple Scheduled TDOA for Reliable Ultra-Wideband Localization},
                Booktitle = {IEEE International Conference on Robotics and Automation (ICRA)},
                Year = {2019},
                Publishingstatus = {accepted for presentation},
                Address = {Montréal, Canada},
                Month = {May}
        }


The atlas_config_example package has been tested under [ROS] Kinetic and Ubuntu 16.04. This is research code, expect that it changes often and any fitness for a particular purpose is disclaimed.

![Example image](doc/viz.jpg)


## Installation

### Building from Source

#### Dependencies

- [Robot Operating System (ROS)](http://wiki.ros.org) (middleware for robotics),
- [ATLAS RTLS](https://github.com/tudo-cni-atlas/atlas_rtls/)


#### Building

To build from source, clone the latest version from this repository into your catkin workspace and compile the package using

	cd catkin_workspace/src
	git clone https://github.com/tudo-cni-atlas/atlas_config_example.git
	cd ../
	catkin_make -j1


## Usage

Due to the modular nature and numerous configuration files that are required to run the ATLAS RTLS, multiple terminal instances is needed. An example is provided here:

Start a roscore:

	roscore

Load the required config files:

	source devel/setup.bash
	roslaunch atlas_config_example config.launch


Start the ATLAS core node (Taking the TOA messages and performing TDOA sample assembly):

	source devel/setup.bash
	roslaunch atlas_config_example core.launch

Start the ATLAS localization node(s) (Taking the TDOA samples and calculating positions):

	source devel/setup.bash
	roslaunch atlas_config_example localizer.launch

Start the ATLAS visualization node:

	source devel/setup.bash
	roslaunch atlas_config_example visualizer.launch

Unzip the bags/2018-09-10-14-27-04.zip first and place the .bag file in the bags folder.

The replay the raw TOAs and ground-truth messages:

	source devel/setup.bash
	rosbag play -s 35 src/atlas_config_example/bags/2018-09-10-14-27-04.bag


[ROS]: http://www.ros.org
[rviz]: http://wiki.ros.org/rviz
[Eigen]: http://eigen.tuxfamily.org
