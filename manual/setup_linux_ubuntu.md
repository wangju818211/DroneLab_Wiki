# Development Environment on Ubuntu LTS



## Common Dependencies

Update the package list and install the following dependencies for all PX4 build targets.

```sh
sudo apt-get update -y
sudo apt-get install git zip qtcreator cmake \
    build-essential genromfs ninja-build -y
# Required python packages
sudo apt-get install python-argparse \
    python-empy python-toml python-numpy \
    python-dev python-pip -y
sudo -H pip install --upgrade pip
sudo -H pip install pandas jinja2 pyserial
```



### Gazebo

> **Note** If you're going work with ROS then follow the [ROS/Gazebo](#rosgazebo) instructions in the following section (these install Gazebo automatically, as part of the ROS installation).

Install the dependencies for [Gazebo Simulation](../simulation/gazebo.md).

```
# Gazebo simulator
sudo apt-get install protobuf-compiler libeigen3-dev libopencv-dev -y
sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'
## Setup keys
wget http://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -
## Update the debian database:
sudo apt-get update -y
## Install Gazebo7 because we are using this edition!
sudo apt-get install gazebo7 -y
## For developers (who work on top of Gazebo) one extra package
sudo apt-get install libgazebo9-dev -y
```

> **Tip** PX4 works with Gazebo 7, 8, and 9. The [installation instructions](http://gazebosim.org/tutorials?tut=install_ubuntu&cat=install) above are for installing Gazebo 9.

<!-- these dependencies left over when I separated the dependencies. These appear to both be for using Clang. MOve them down?
sudo apt-get install clang-3.5 lldb-3.5 -y
-->
