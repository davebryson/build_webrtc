##WebRTC Build Scripts

A set of build scripts useful for building WebRTC libraries for Android.

Bugs: Please submit the [revision](https://code.google.com/p/webrtc/source/list) number that you are using. There are frequent updates to this project so please watch the changelist for bug fixes.

###Android ARMv7, ARMv8, x86, x86_64 Builds -- [Guide here](http://tech.pristine.io/build-android-apprtc/)

The following instructions are for building the native WebRTC libraries for Android.


#### Getting Started
##### On Linux
You should only need Ubuntu 12.04 on a 64 bit machine to get going.

This is only required once.
```shell

# Source all the routines
source android/build.sh

# Install any dependencies needed
install_dependencies

# Pull WebRTC
get_webrtc
```

##### On Mac or Windows
If you don't have a Ubuntu machine available, or you are too lazy to setup a virtual machine manually, you can build WebRTC for Android on your Mac or Windows PC through our Vagrant script.

First of all, you need to [download and install](http://www.vagrantup.com/downloads.html) Vagrant. After that, from the `/android` directory, you need to execute the following in you shell:

```shell

# If you need to use private SSH keys from your host computer 
# Execute this line of code to ensure your private key is added to your identity
ssh-add -L

# If there are no identities, add them by:
ssh-add ~/.ssh/id_rsa

# Boot up and provision the Vagrant box
vagrant up

# SSH into the Vagrant box
vagrant ssh

```

#### Building the libraries

Then you can build the Android example

```shell
# Pull WebRTC
get_webrtc

# Build apprtc
build_apprtc

# Build in debug mode
export WEBRTC_DEBUG=true
build_apprtc
```

You can build for armv7, armv8, x86, x86_64 platform

```shell
export WEBRTC_ARCH=armv7 #or armv8, x86, or x86_64
prepare_gyp_defines &&
execute_build
```

You can build a particular [revision](https://code.google.com/p/webrtc/source/list)

```shell
# Pull WebRTC
get_webrtc 6783

# Build apprtc
build_apprtc
```

When the scripts are done you can find the .jar and .so file in $WEBRTC_ROOT under "libjingle\_peerconnection\_builds".


###### Versioning

The versioning can be explained as follows:

 
[6931](https://code.google.com/p/webrtc/source/detail?r=6931).2.0 

6931 reflects the SVN revision from the WebRTC root Google Code Project

2 reflects a Release Build (0 for Debug, 1 for Profile)

Profile builds are no longer built by default

The minor 0 reflects any changes I might need to make to the sample xcode project itself to work (incremented normally)


