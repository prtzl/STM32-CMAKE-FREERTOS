# Fix cmake and CubeMX build configuration 

Changes:
* i updated your CubeMX configuration to only export used library files. Now there are less files and glob recurse will be ok as it won't compile files that are not used. This could fail.
* i updated your CMakeLists.txt to use glob recurse, now works with correct CubeMX configuration  

Because you set CubeMX folder as project root, it's output makefile is here as well, therefore we cannot put our own makefile easily. You can launch cmake manualy:

```shell
cmake -Bbuild -DCMAKE_BUILD_TYPE=Debug -DCMAKE_TOOLCHAIN_FILE=gcc-arm-none-eabi.cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=ON
```

Then go into newly created folder `build` and launch `make -jx`, where x is the number of cores you wish to utilize. Launch `make clean` in same folder to clean the project.  

If you want to use my makefile from the video, create a new cubemx project (sorry, this setting can be applied at fist only) and under Project Manger after you enter project name and its location, under Toolchain Folder Location name folder in which CubeMX will put its Makefile, startup and linker scripts. I use `CubeMX` as the name. Then you can put (my) custom makefile in project root as in the video.  

Cheers,
Matej
