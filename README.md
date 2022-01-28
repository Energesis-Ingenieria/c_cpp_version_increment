#Version Increment for C/C++ projects
Simple version increment script for C/C++ projects.  
  
_Some IDE does not have a tool to automatically increment the version number of an app when building it. So I decided to take sblantipodi's idea and use it for other IDEs._

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Energesis Ingeniería](https://img.shields.io/static/v1?label=Energesis&message=Software&color=orange)](https://www.dpsoftware.org)

## How To Use
1) From the root of your project run
```
git submodule add https://github.com/sblantipodi/platformio_version_increment.git cpp_version_increment
```

2) Configure your IDE for:
    - execute `cpp_version_increment/version_increment_pre.py` before compile
    - execute `cpp_version_increment/version_increment_post.py` after compile

3) Add `#include "Version.h"` to any source file or header file that need to know the version (i.e. `main.cpp`)
4) Build your software . In the root of your project you will find two files:
    - version
    - include/Version.h 

The `version` file will default to `0.1.0`, but you can edit this with the version number you wish to start incrementing from.

Every completed build will trigger a +1 on the patch number.

In the `Version.h` file (which you'll need to include in order to access the incrementing version and timestamp variables) you'll have this:
```c++
// AUTO GENERATED FILE, DO NOT EDIT THIS FILE
#ifndef VERSION
  #define VERSION "0.1.0"
#endif
#ifndef BUILD_TIMESTAMP
  #define BUILD_TIMESTAMP "2020-04-10 17:58:52.937616"
#endif
```    

You now have auto-incrementing VERSION and BUILD_TIMESTAMP variables you can use in your program as you wish!

For example:
```c++
cout << "Project version: " <<  VERSION << endl;
cout << "Build timestamp:" << BUILD_TIMESTAMP << endl;
```

or

```c++
printf("Project version v%s, built %s\n",VERSION,BUILD_TIMESTAMP);
```

## License
This program is licensed under MIT License
