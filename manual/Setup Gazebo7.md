# Install Gazebo7  using Ubuntu packages

## 1.Setup your computer to accept software from packages.osrfoundation.org.
Note: there is a list of available mirrors for this repository which could improve the download speed.
```shell
sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'
```
You can check to see if the file was written correctly. For example, in Ubuntu Xenial, you can type:
```shell
$ cat /etc/apt/sources.list.d/gazebo-stable.list
deb http://packages.osrfoundation.org/gazebo/ubuntu-stable xenial main
```
## 2.Setup keys
```shell
wget http://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -
```
## 3.Install Gazebo.
First update the debian database:
```shell
sudo apt-get update
```
Hint: make sure the apt-get update process ends without any errors, the console output ends in Done similar to below:
```shell
$ sudo apt-get update
...
Hit http://ppa.launchpad.net xenial/main Translation-en
Ign http://us.archive.ubuntu.com xenial/main Translation-en_US
Ign http://us.archive.ubuntu.com xenial/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com xenial/restricted Translation-en_US
Ign http://us.archive.ubuntu.com xenial/universe Translation-en_US
Reading package lists... Done
```
Next install gazebo-7 by:
```shell
sudo apt-get install gazebo7
# For developers that work on top of Gazebo, one extra package
sudo apt-get install libgazebo7-dev
```
If you see the error below:
```shell
$ sudo apt-get install gazebo9
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package gazebo9
```
It's possible the version of Gazebo you are looking for is not supported on the version of OS you are using. For example, installing gazebo9 on Ubuntu Trusty (14.04) will produce the error above. Hint: Take a look at "Project Status" section at http://gazebosim.org/#status, next to each version is the supported ubuntu versions and ROS versions.
## 4.Check your installation
Note The first time gazebo is executed requires the download of some models and it could take some time, please be patient.
```shell
gazebo
```
## 5.Testshooting



# Gazebo in different deb packages
Gazebo ships different Ubuntu debian packages following the official packaging guidelines:

- Use Gazebo as an application: for the users that just run Gazebo simulator with the provided plugins and models and do not plan on developing on top of gazebo its own custom software. To use Gazebo 7 please install the package called gazebo7.

- Use Gazebo to develop software using Gazebo libraries: for users that develop plugins or any other kind of software that needs Gazebo headers and libraries. In this case, together with gazebo9 package, please install libgazebo7-dev.
