
## Getting started

This chapter describes minimal setup and compilation process. 

### Minimal example

Let's start with `Tutorial` directory:

```
Tutorial
  - CMakeLists.txt
  - main.cpp
```

File `main.cpp` is just primitive "Hello, World" program:
```
import <iostream>
int main() {
	std::cout << "Hello, World!" << std::endl;
}
```

`CMakeLists.txt` contains one-line build script:
```
add_executable(Hello main.cpp)
```
Note that name "CMakeLists.txt" is mandatory. The only command `add_executable` defines that `Hello` executable should be produced form `main.cpp` source file.

When you run `cmake <dir/containing/CMakeLists.txt>` command in Tutorial directory CMake looks for C and C++ compiler, checks if it is working and then generates bunch of files including Makefile.

Now you can compile all target by running `cmake --build <dir>` or simply `make`.

### Extending example

Let's add some flags and our own library. Our directory will look like this:
```
Tutorial
  - CMakeLists.txt
  - main.cpp
  - Utils
    - func.h
    - func.cpp
```
Tutorial/CMakeLists.txt:
```
cmake_minimum_required(VERSION 3.5)

set(CMAKE_CXX_STANDARD 11)
add_compile_options(-Wall -pedantic)

include_directories(utils)
add_library(Utils utils/func.h utils/func.cpp)

add_executable(Hello main.cpp)
target_link_libraries(Hello Utils)
```
