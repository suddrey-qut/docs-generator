# Installing Software

Import the RV GPG Key using the following command

```bash
sudo -E apt-key adv --keyserver hkp://keyserver.ubuntu.com --recv-key 5B76C9B0
```

Add the Robotic Vision repository to the apt sources list directory

```bash
sudo sh -c 'echo "deb [arch=$(dpkg --print-architecture)] http://roboticvision.org/packages $(lsb_release -sc) main" > /etc/apt/sources.list.d/acrv-latest.list'
```

Update your packages list

```bash
sudo apt update
```

# Resolving Rosdep Issues

rosdep provides a useful mechanism for retrieving system dependencies required to build ROS packages from source. However, the list of packages maintained by the official ROS index is rather limited.

As part of developing our Robotic Vision libraries we have frequently discovered dependencies that were simply not available via rosdep. To resolve this issue we have created our own index compliment that provided by ROS.

To use rosdep to install depencencies needed for building the Robotic Vision libraries from source, please run the following command:

```bash
sudo sh -c 'echo "yaml https://bitbucket.org/acrv/rv_package_list/raw/HEAD/bionic/sources.yaml" >> /etc/ros/rosdep/sources.list.d/20-default.list'
rosdep update
```

**Note:** This assumes that you have previously installed ROS and have run `rosdep init`
