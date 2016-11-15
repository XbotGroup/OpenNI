# OpenNI (Version 1.5.4.0 - May 7th 2012)

由中国科学院软件研究所协同创新中心维护的OpenNI分支。

Sources are available at:
https://github.com/XbotGroup/OpenNI

## Release Notes:

TODO

## Build Notes:

Linux Only

### Requirements:
1) GCC 4.x

    `sudo apt-get install g++`

2) Python 2.6+/3.x

 `sudo apt-get install python`

3) LibUSB 1.0.x

    `sudo apt-get install libusb-1.0-0-dev`

4) FreeGLUT3

    `sudo apt-get install freeglut3-dev`

5) JDK 6.0

    `sudo apt-get install openjdk-6-jdk`

Optional Requirements (To build the documentation):

  1) Doxygen

     sudo apt-get install doxygen

  2) GraphViz

     sudo apt-get install graphviz

Optional Requirements (To build the Mono wrapper):
  1) Mono
     From: http://www.go-mono.com/mono-downloads/download.html
     Or via apt:
     sudo apt-get install mono-complete

### Building OpenNI:
  1) Go into the directory: "Platform/Linux/CreateRedist".

     Run the script: "./RedistMaker".

     This will compile everything and create a redist package in the "Platform/Linux/Redist" directory.

     It will also create a distribution in the "Platform/Linux/CreateRedist/Final" directory.

  2) Go into the directory: "Platform/Linux/Redist".

     Run the script: "sudo ./install.sh" (needs to run as root)


       The install script copies key files to the following location:

         Libs into: /usr/lib

         Bins into: /usr/bin

         Includes into: /usr/include/ni

         Config files into: /var/lib/ni

  To build the package manually, you can run "make" in the "Platform\Linux\Build" directory.

  If you wish to build the Mono wrappers, also run "make mono_wrapper" and "make mono_samples".

### Building OpenNI using a cross-compiler:

  1) Make sure to define two environment variables:

     - <platform>_CXX - the name of the cross g++ for platform <platform>

     - <platform>_STAGING - a path to the staging dir (a directory which simulates the target root filesystem).

     Note that <platform> should be upper cased.

     For example, if wanting to compile for ARM from a x86 machine, ARM_CXX and ARM_STAGING should be defined.

  2) Go into the directory: "Platform/Linux/CreateRedist".

     Run: "./RedistMaker <platform>" (for example: "./RedistMake Arm").

     This will compile everything and create a redist package in the "Platform/Linux/Redist" directory.

     It will also create a distribution in the "Platform/Linux/CreateRedist/Final" directory.

  3) To install OpenNI files on the target file system:

     Go into the directory: "Platform/Linux/Redist".

     Run the script: "./install.sh -c $<platform>_STAGING" (for example: "./install.sh -c $ARM_STAGING").

       The install script copies key files to the following location:

         Libs into: STAGING/usr/lib

         Bins into: STAGING/usr/bin

         Includes into: STAGING/usr/include/ni

         Config files into: STAGING/var/lib/ni

  To build the package manually, you can run "make PLATFORM=<platform>" in the "Platform\Linux\Build" directory.

  If you wish to build the Mono wrappers, also run "make PLATFORM=<platform> mono\_wrapper" and "make PLATFORM=<platform> mono_samples".

