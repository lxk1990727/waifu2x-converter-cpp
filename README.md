# waifu2x (converter only version)

This is a reimplementation of waifu2x ([original](https://github.com/nagadomi/waifu2x)) converter function, in C++, using OpenCV.
This is also a reimplementation of [waifu2x python version](https://marcan.st/transf/waifu2x.py) by [Hector Martin](https://marcan.st/blog/).
You can use this as command-line tool of image noise reduction or/and scaling.

## Prebuilt binary-form release

https://github.com/max20091/waifu2x-converter-cpp/releases

## waifu2x converter GUI

 * [waifu2x_win_koroshell](http://inatsuka.com/extra/koroshell/)
   - waifu2x-converter GUI frontend that is easy to use, and so cute. You need only drag&drop to convert your image. (and also you can set converting mode, noise reduction level, scale ratio, etc..., on GUI)
   - Both waifu2x-converter x86 and x64 are included this package, and GUI see your windows architecture(x86|x64) and selects automatically which to use. 
   - For windows only.


## Dependencies

### Platform

 * Ubuntu  
 * Windows  
 * Mac OS X?  
 
(This program probably can be built under MacOSX, because OpenCV and other libraries support OS X)

### Libraries

 * [OpenCV](http://opencv.org/)(version 3.0)

This programs also depends on libraries shown below, but these are already included in this repository.
*CUDA Support in OpenCV is optional, since not required. (in version 1.0.0, CUDA Support is not used.)*

 * [picojson](https://github.com/kazuho/picojson)
 * [TCLAP(Templatized C++ Command Line Parser Library)](http://tclap.sourceforge.net/)

## How to build

### for Ubuntu

Sorry, under construction...

These are hints for building :

 * I recommend to install OpenCV from sources. (build instruction is found [here](http://opencv.org/quickstart.html))
 * include path : `include/` `(/path/to/opencv/installed/directory)/include`
 * library path : `(/path/to/opencv/installed/directory)/lib` 
     - if you have built and installed OpenCV from source, and have changed install directory(by using `CMAKE_INSTALL_PREFIX`), you may need to set environment variable `LD_LIBRARY_PATH` for your OpenCV installed directory.
 * libraries to link : `opencv_core` `opencv_imgproc` `opencv_imgcodecs` `opencv_features2d`
 * standard of C++ : `c++11`

### for Windows (Windows x64 with AMD GPU)

1. Download and install VS2013, OpenCV 3.0, CMake x64 and AMD APP SDK v2.9
2. Copy master branch to somewhere then copy CMakeLists.txt from NoCUDA-Windows branch to master branch
3. Run CMake GUI, Press Browse source and choose waifu2x-converter-cpp folder
4. Add OPENCV_PREFIX entry, folder location point to %OpenCV%\build\ (%OpenCV% is the installed OpenCV location)
5. Press Configure, choose Visual Studio 12 2013 x64
6. Compile it with VS2013 and done!

## Usage

Usage of this program can be seen by executing this with `-h` option.

(My native language is not English, then I'm sorry for my broken English.)

## modifided by tanakamura
 * Added CUDA, OpenCL(AMD GPU), x86 FMA, x86 AVX Support (That is selected automatically at runtime)
  * OpenCL(AMD GPU) version achieves 40% of peak performance (291GFLOPS @ A10-7850K)
 * Added CMakeLists.txt
  * You can build it by cmake ($ cmake -D OPENCV_PREFIX=&lt;OpenCV include/lib dir&gt;)
 * [DLL interface](src/w2xconv.h)
  * You can use waifu2x as library. include w2xconv.h & link w2xc.lib.

## modifided by max20091
 * Updated tclap, PicoJSON, Waifu2x model
 * Added Noise Reduction Level 3
 * Using nagadomi original model
 * Added Windows build guide
