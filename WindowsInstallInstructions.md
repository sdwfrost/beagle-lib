### Installing BEAGLE on Windows ###
The easiest way to install BEAGLE is to use the binary installer.

**Step 1.** Download and run the binary installer:
  * [BEAGLE v2.1 for Windows XP and later](http://beagle-lib.googlecode.com/files/BEAGLE-2.1.msi)

**Step 2. (optional)** If you wish to use BEAGLE with a multicore Intel CPU via OpenCL, please download and install the latest Intel OpenCL CPU runtime from intel.com:
  * [Intel OpenCL](http://software.intel.com/en-us/vcsource/tools/opencl-sdk)

**Step 3. (optional)** If you wish to use BEAGLE with an NVIDIA GPU please download and install the latest NVIDIA drivers for your graphics card from nvidia.com:
  * [NVIDIA Driver Downloads](http://www.nvidia.com/page/drivers.html)

**Step 4.** Restart your computer (this is required so Windows finds the new libraries).

After the installations above are complete, you will be ready to use BEAGLE with compatible applications such as BEAST, MrBayes, PhyML and GARLI.

For instructions on how to use BEAGLE with BEAST please refer to [Using BEAGLE with BEAST](http://beast.bio.ed.ac.uk/BEAGLE)


---


#### Installing from source ####
If you have problems with the binary installer or wish to use the latest SVN revision you may build BEAGLE from source.

The following software prerequisites must be installed prior to building libhmsbeagle on Windows:

  * Visual Studio 2012
  * Java Development Kit 1.6 or later
  * Intel OpenCL SDK (if you wish to build the OpenCL plugin)
  * NVIDIA CUDA toolkit (if you wish to build the CUDA plugin)

**Step 1.** Obtain a subversion client (such as [TortoiseSVN](http://tortoisesvn.net)) and checkout the source code from the repository:
```
http://beagle-lib.googlecode.com/svn/trunk
```

**Step 2.** Configure your Java path by navigating to **`project\beagle-vs-2012`** and running **`findJava.bat`**.

**Step 3.** Open the Visual Studio 2012 project located at **`project\beagle-vs-2012\libhmsbeagle.sln`**.

**Step 4.** Go to **BUILD** -> **Configuration Manager...** in the top menu bar and set the solution configuration to **Release** and the platform to **x64** or **Win32**, according to the architecture of the application you wish to use with BEAGLE.

**Step 5.** Build the solution (**BUILD** -> **Build Solution**).

**Step 6.** The previous step will create **`hmsbeagle*.dll`** files located at **`project\beagle-vs-2012\x64\Release`** or **`project\beagle-vs-2012\Release`**. Copy these **`hmsbeagle*.dll`** files to the directory which contains the executable of the application you wish to use with BEAGLE.