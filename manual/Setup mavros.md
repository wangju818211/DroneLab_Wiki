Installation
------------

### Required dependencies

Most of the ROS dependencies are supported and installed by `rosdep`, including external
libraries as Eigen and Boost.

[GeographicLib][geolib] can be installed by `apt-get` and it is already included on the
rosdep of MAVROS package. It is also possible to compile it and install it from src but
be advised to have the proper install directories the same as the ones of the `apt-get`
install, in order to make sure that the `FindGeographicLib.cmake` finds the required
shared libraries (`libGeographic.so`).

Since **GeographicLib requires certain datasets** (mainly the geoid dataset) so to fulfill
certain calculations, these need to be installed manually by the user using `geographiclib-tools`,
which can be installed by `apt-get` in Debian systems. For a quicker procedure, just **run
the available script in the "mavros/scripts" folder, `install_geographiclib_datasets.sh`**.

Note that if you are using an older MAVROS release source install and want to update to a new one, remember to
run `rosdep update` before running `rosdep install --from-paths ${ROS_WORKSPACE} --ignore-src --rosdistro=${ROSDISTRO}`,
with `ROS_WORKSPACE` your src folder of catkin workspace. This will allow updating the `rosdep` list
and install the required dependencies when issuing `rosdep install`.

:bangbang: **The geoid dataset is mandatory to allow the conversion between heights in order to
respect ROS msg API. Not having the dataset available will shutdown the `mavros_node`** :bangbang:

:heavy_exclamation_mark:Run `install_geographiclib_datasets.sh` to install all datasets or
`geographiclib-datasets-download egm96_5` (*Debian 7*, *Ubuntu 14.04*, *14.10*), `geographiclib-get-geoids egm96-5`
(*Debian 8*, *Fedora 22*, *Ubuntu 15.04* or later) to install the geoid dataset only:heavy_exclamation_mark:


### Binary installation (deb)

ROS repository has binary packages for Ubuntu x86, amd64 (x86\_64) and armhf (ARMv7).
Kinetic also support Debian Jessie amd64 and arm64 (ARMv8).

Just use `apt-get` for installation:

    sudo apt-get install ros-kinetic-mavros ros-kinetic-mavros-extras
        

![random screenshot](../img/test.png)

Then install GeographicLib datasets by running the `install_geographiclib_datasets.sh` script:

    wget https://raw.githubusercontent.com/mavlink/mavros/master/mavros/scripts/install_geographiclib_datasets.sh
    ./install_geographiclib_datasets.sh
