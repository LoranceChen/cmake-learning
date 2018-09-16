# README
learning cmake build tool from [cmake tutorials](https://lellansin.gitbooks.io/cmake/content/)

## Commands
- `cmake CMakeLists.txt`, generator makefile
- `make`, build a executable file and defined library
- `make clean`, delete executable file
- `make install`, install `*.h`, `*.a` and executable file to `/usr/local/include` and `/usr/local/bin`.
- `cpack --config CPackConfig.cmake`, create a installer
- `cmake -G Xcode ..`, create a xcode project
    - use CMakeLists.txt at `../`