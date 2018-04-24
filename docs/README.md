**Work in Progress!!**

## What is CMake (good for)?

CMake is set of tools for build automation. Command `cmake` is the cornerstone of the CMake product. It allows you to specify compilation process, including additional build steps, in cross-platform and compiler independent way. Other two tools are `ctest` and `cpack` for automation of testing and packaging respectively. For now let's focus on `cmake`.

Note on terminology: I will use term "CMake" when talking about entire product and simply "cmake" when referring to `cmake` command included in the CMake product.



### The Key Idea: Generating native build scripts

So how does CMake achieve platform and compiler independence? It's simple. First you write CMake build script in unified CMake language. Then you select generator for target build system (e.g.: NMake, MinGW, XCode...) that is installed on your system and you run `cmake` to generate corresponding input files for your system (e.g. makefiles).

CMake also provides OS-like command line tools for creating files, folders, symlinks, editing registry and so on. See [CMake documentation](https://cmake.org/cmake/help/v3.3/manual/cmake.1.html#command-line-tool-mode) for more information.

This particular approach has several benefits. It's great for cross-platform projects as it allows you to use full power of native compilers while adhering "Single Source of Truth" principle. Managing several build scripts is error prone as it may cause inconsistency. It's also convenient for open source projects. With CMake you don't force your users or contributors to use one particular compiler.

And even if you target single platform and single build system - let's say `Make` on Linux - you can still benefit from using CMake.



### Other Features of cmake

1) **Scalability**
CMake scripts can be assembled into tree structure which makes it easily scalable.

2) **Configurability**
You can branch your scripts based on conditions like: platform, presence of certain libraries, compiler capabilities, cmake version and others. Custom options can be passed when triggering the build.

3) **Including 3rd party code**
There are few commands that helps you integrate third party code into your project. Most useful is automatic finding of installed libraries or fetching source code from remote repository.

4) **Code generation**
It is also possible to generate source files by scripts and executables. You specify dependencies and CMake recompiles/reruns targets when necessary.

5) **IDE integration**
CMake has large user-base and integrates well with many IDEs including Visual Studio, CLion, Eclipse and XCode.

6) **Human readable code**
This point is bit disputable. Many people find CMake DSL confusing. But when you understand basics of CMake ecosystem scripts became quite clear especially in comparison with Unix makefiles.