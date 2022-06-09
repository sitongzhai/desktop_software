# desktop_software

## Introduction
This is a cross-platform framework for desktop software. A tcl system drives this framework in background.

This software framework can be started with 'tcl' or 'gui' mode. The GUI mode is developed with the opensource QT interfaces. The opensource Qt5.14.2 toolset is required to before using this framework. The background tcl system is independent with QT. So, QT is not required if you only use the tcl system, but all QT related codes must be removed. 

This framework has been applied in the opensource EDA tool of FPGA, and has been verified its high efficiency and stability. 
  
## License
All source codes are under MIT license.
See the [full license](LICENSE.md) for details.

## Building

This framework requires tcl8.4.20, readline6.0 is required on Linux platform and pthread is required on Windows plarform. In addition, "qmake" is required to build.

#### 1.Windows
Come into direction "desktop_software/code/build". Double click the batch script "make_2019.bat". The environment will be configured and "software.sln" file will be generated automatically, then the solution file will be open with visual studio 2019. 

The third party libraries in "desktop_software/thirdparty" were built by Visual Studio 2019 with the platform toolset "v120" using processor "Intel(R) i7-2720QM". The libraries may need to be recompiled if using other windows platforms.

The default path of Visual Studio 2019 is "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community", "VS_PATH" and "%VS_PATH%\VC\Auxiliary\Build\vcvars64.bat" in "make_2019.bat" should be changed if using other paths.

The default path of "qmake" is "C:\Qt\Qt5.14.2\5.14.2\msvc2017_64\bin". "QT_PATH" in "make_20019.bat" should be modified if using other paths. The default "-spec" of qmake is "win32-msvc", the platform-specific variable should be changed if using other platforms.

#### 2.Linux
Set the environemnt as below or using absolute paths:
    
    export LD_LIBRARY_PATH="../thirdparty/Linux/tcl:../thirdparty/Linux/readline:$LD_LIBRARY_PATH"
    export TCL_LIBRARY="../thirdparty/Linux/tcl/tcl8.4"

If using relative paths as above, come into direction "desktop_software/code" to build:

    ./build/make_pro
    make

The binary executable will be generated in "desktop_software/bin/Linux" as "software".
"make debug" will generate "software-debug" in the same path.

The static libraries were compiled in "Ubuntu 20.04TLS" using processor "Intel(R) i7-2720QM". The libraries may need to be recompiled if using other Linux plarform.

## Run/Debug FST
If using relative paths in the environment on Linux, come into direction "desktop_software/code", run FST with:

    ./bin/Linux/software 

or use "-gui" to open GUI mode as:

    ./bin/Linux/software -gui

or use a tcl script to run as:

    source path_of_script/XXX.tcl

or run the tcl script directly as:

    path_of_desktop_software/software path_of_script/XXX.tcl


#### register new commands
All tcl commands need to be registered in function "int registerAllCmds(Tcl_Interp* interp)" of "desktop_software/code/src/tcl/register_commands.cpp"




