# OpenCV modified for cross-compilation on the Raspberry Pi 3

A few files have been modified to facilitate cross compilation.

./CMakeLists.txt
./platforms/linux/arm.toolchain.cmake

Before compiling, copy the root folders of your raspberry pi to a 
location on the machine that's doing the compiling. In my case I copied
the following from the pi to /opt/arm/raspi/sysroot/
- /usr/include/python2.7
- /usr/bin
- /usr/lib

If you change the path to which these directories are copied, you'll also
need to adjust the cmake_cmd.txt configuration script accordingly.

To compile, run the following from the root of the repo

```bash
mkdir build
cd build
cp ../cmake_cmd.txt .
./cmake_cmd.txt # this will do the configuration
make
```

Then you can run `make install` to install the files to 
CMAKE_INSTALL_PREFIX. From there, copy them to the pi 
and double check to make sure your python path is set to the 
correct directory. You may also need to be sure that the 
/usr/lib/python2.7/dist-packages directory was copied correctly
(sometimes this gets named to site-packages instead of dist-packages 
 depending on the distro).
