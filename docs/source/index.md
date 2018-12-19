## Introduction - Two Phases of the Build

So, how it works? The build process is defined in platform and compiler independent configuration files named CMakeLists.txt. (The name is mandatory.) These files are highly declarative. You specify what executables should be built, what libs should be linked to them, what C++ version should be used and so forth. But you don't care about object files or other "internal details".

CMake then uses [Generator](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) to create build files for native build system. On Linux these would be Makefiles by default. But you can select Ninja generator and others. There are also [Extra Generator](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html#extra-generators) to support IDE integration. See documentation for complete list.

	
	
