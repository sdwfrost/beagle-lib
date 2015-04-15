## Installing BEAGLE on Linux ##
To install BEAGLE on Linux-based operating systems you will need to build BEAGLE from source.


### Installing from source ###
#### Step 1. Obtain prerequisites ####

You will need the following software to download and build BEAGLE from source:
  * gcc (or other equivalent compiler)
  * make
  * autoconf
  * automake
  * libtool
  * subversion
  * pkg-config

Additionally we recommended installing the following optional prerequisites:
  * OpenCL implementations for your hardware resources
  * NVIDIA CUDA drivers and toolkit (if you want to use BEAGLE with CUDA on an NVIDIA GPU)
  * Java JDK (if you want to use BEAGLE with BEAST)

The prerequisite software should be fairly easy to install.
On Ubuntu and other Debian Linux distributions all the requisite software can be obtained via apt-get:
```
sudo apt-get install build-essential autoconf automake libtool subversion pkg-config openjdk-6-jdk
```

OpenCL implementations are available from:
  * Intel http://software.intel.com/en-us/vcsource/tools/opencl-sdk
  * AMD http://developer.amd.com/tools-and-sdks/heterogeneous-computing/amd-accelerated-parallel-processing-app-sdk/downloads/
  * NVIDIA https://developer.nvidia.com/opencl

The NVIDIA CUDA drivers and toolkit can be downloaded from [http://www.nvidia.com/object/cuda\_get.html](http://www.nvidia.com/object/cuda_get.html). They need to be installed for BEAGLE to use CUDA for GPU acceleration.

#### Step 2. Build from the source repository ####

```
svn checkout http://beagle-lib.googlecode.com/svn/trunk/ beagle-lib
cd beagle-lib
./autogen.sh
./configure --prefix=$HOME
make install
```

#### Step 3. Set environment variables ####

If you followed the instructions above, then BEAGLE was installed to your home directory.  You'll need to tell other programs to find the beagle library in your home directory by setting the `LD_LIBRARY_PATH` environment variable:
```
export LD_LIBRARY_PATH=$HOME/lib:$LD_LIBRARY_PATH
```
Or if using tcsh:
```
setenv LD_LIBRARY_PATH $HOME/lib:$LD_LIBRARY_PATH
```
That command will need to be run every time you log in, so it's best to put it in a login script such as `.bashrc` or `.profile` or `.cshrc`, etc.

If you plan to build other applications that depend on beagle, you'll also need be sure BEAGLE is in your pkg-config path:
```
export PKG_CONFIG_PATH=$HOME/lib/pkgconfig:$PKG_CONFIG_PATH
```
This too can be put in a login script.

#### Step 4. Verify that everything works ####

Finally, to verify that the installation worked and that your NVIDIA card is working go to the `beagle-lib` directory and type:
```
make check
```
This will run a suite of test programs using the BEAGLE library.

If you get no errors you are ready to use BEAGLE with compatible applications such as BEAST, MrBayes, and GARLI.

For instructions on how to use BEAGLE with BEAST please refer to [Using BEAGLE with BEAST](http://beast.bio.ed.ac.uk/BEAGLE)