# Porting an existing C++ codebase using CMake to Android

Awhile ago, I was working on a codebase that compiled on Windows, GNU/Linux, and OS X. I used [CMake](http://www.cmake.org/) to handle generating the build files for each platform. CMake is far from perfect, but it really is the best tool currently available for maintaining a cross-platform C/C++ project.

Unfortunately, while CMake can, out of the box, generate GNU Makefiles, XCode project files, and MSVC project files, it _cannot_ generate the necessary build files for Android and iOS. This is ridiculous considering how popular these platforms are and how long they've been available. Fortunately, with a little bit of work, we can have CMake generate Android/iOS build files.

In this post, I'll be covering how to generate Android build files. I might do another post specific to iOS at a later time.

## Setting Up the Android NDK

1. Download the [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html) for your platform and extract it somewhere convienent.

2. Set environment variable ```ANDROID_NDK``` to the root NDK directory.

3. Make a standalone toolchain for your target Android platform and architecture using ```$ANDROID_NDK/build/tools/make-standalone-toolchain.sh```
   *Example:*
   ```$ANDROID_NDK/build/tools/make-standalone-toolchain.sh --platform=android-19 --toolchain=arm-linux-androideabi-4.9```

   For help, try passing in ```--help```
