## CMake Ecosystem

After reading "Getting Started" chapter you should have basic idea how CMake operates. However there are few things you better know and they may not be so intuitive.


### When are CMake scripts processed

Running `cmake <DIR>` populates cache and generates build files from CMakeLists.txt. You might expect you need to rerun this command every time you modify CMakeLists to update your scripts. However CMake actually includes automatic checks into build scripts and they will update themselves whenever necessary. You need to run `cmake <DIR>` only once.

One exception to this is when you move your files or project folder. Remember that CMake generates build files using absolute paths. Obviously CMakeLists.txt is not affected by such change so you need to rerun `cmake` manually.

CMakeLists.txt files looks like scripts (and they are!) but it's important to keep in mind when they are run. It's possible to run scripts from CMakeLists.txt, to generate code or to modify directory structure. However if not set properly triggering of these actions will depend on change of the CMakeLists.txt file rather then on files used by scripts or so. If you want some action to depend on change of different file use `add_custom_target` possibly `ExternalProject_Add`.


### Splitting scripts & assembling them into tree

You don't have to process your entire project source tree from one script. CMakeLists file is generally an entry point to project directory and you can use more than one. For example if you have directory with library source files within your project you can set CMakeLists.txt responsible for building that particular library. Putting this file into library directory is convenient as all relative paths as well as expressions like `*.cpp *.h` will be resolved against this file.

To include another CMakeLists.txt use `add_subdirectory('path/to/CMakeLists.txt')`. By doing that you create build tree. Variables flow down the tree and targets flow up.

In previous chapter we added library to our project. But let's give that lib the luxury of own CMakeLists file.

Our directory will look like this:
```
Tutorial
  - CMakeLists.txt
  - main.cpp
  - Utils
	- CMakeLists.txt
    - func.h
    - func.cpp
```

```
example
```

This approach promotes modularity, Single Responsibility Principle and can speed up build. It's also really simple to include 3rd party code (that is using CMake) into your project.