# Porting an existing C++ codebase using CMake to Android

Awhile ago, I was working on a codebase that compiled on Windows, GNU/Linux, and OS X. I used [CMake](http://www.cmake.org/) to handle generating the build files for each platform. CMake is far from perfect, but it really is the best tool currently available for maintaining a cross-platform C/C++ project.

Unfortunately, while CMake can, out of the box, generate GNU Makefiles, XCode project files, and MSVC project files, it _cannot_ generate the necessary build files for Android and iOS. This is ridiculous considering how popular these platforms are and how long they've been available. Fortunately, with a little bit of work, we can have CMake generate Android/iOS build files.

In this post, I'll be covering how to generate Android build files. I might do another post specific to iOS at a later time.
