# Fulcrum
A fast & nimble SPV server for Bitcoin Cash.

#### Copyright
(C) 2019-2020 Calin Culianu <calin.culianu@gmail.com>

#### License:
GPLv3. See the included `LICENSE.txt` file or [visit gnu.org and read the license](https://www.gnu.org/licenses/gpl-3.0.html).

### Highlights:

- *Fast:* Written in 100% modern `C++17` using multi-threaded and asynchronous programming techniques.
- *A drop-in replacement for ElectronX/ElectrumX:* The initial release of this server is 100% protocol-level compatible with the ElectronX/ElectrumX 1.4.2 protocol. Existing server admins should feel right at home with this software since installation and management of it is nearly identical to ElectronX/ElectrumX server.
- *Cross-platform:* While this codebase was mainly developed and tested on MacOS, Windows and Linux, it should theoretically work on any modern OS (such as *BSD) that has QtCore available.

### Requirements

- `Qt Core` & `Qt Networking` libraries `5.11` or above (I use `5.13.2` myself).
- A modern, 64-bit `C++17` compiler.  `clang` is recommended but `G++` also works. MSVC on Windows is not supported (please use `MinGW G++` instead, which ships with Qt Open Source Edition for Windows).

### How To Compile

It's recommended you use Qt Creator.

1. Get the latest version of Qt Open Source Edition for your platform.
2. Point the Qt Creator IDE at the `Fulcrum.pro` file.
3. Set the build configuration to "Release".  Hit Build.  It should "just work".

**A note for Windows users**: `Qt 5.13.2` (or above) with `MinGW G++ 7.x.x` is the compiler/Qt kit you should be using.  MSVC is not supported by this codebase at the present time.

#### What to do if compiling fails
If you have problems compiling, the most likely culprit would be your compiler not being `C++17` compliant (please use a recent verson of `GCC` or `clang` on Linux, Apple's `Xcode` on Mac, or `MinGW G++ 7.x` on Windows).

The other likely culprit is the fact that at the present time I have included a statically-built `librocksdb` in the codebase. There are versions of this library for Windows, Mac, and Linux included right in the source tree, and `Fulcrum.pro` looks for them and links to them. Instructions are included within the `Fulcrum.pro` project file about how to build your own static `librocksdb` if the bundled one does not work on your system.

---

### Platform Notes

#### Big Endian Architectures

The code is more or less configured to assume a "little endian" architecture by default (which is what all Intel x86/x86_64 are).  If you're on a big endian machine, on Linux it should just auto-detect that fact.  However, on other OS's such as BSD, if you're on a big endian machine, you may need to uncomment this line from the `.pro` file:

    # DEFINES += WORDS_BIGENDIAN


#### Windows

This codebase will not compile correctly (or at all) using MSVC. Please use the `MinGW` and/or `G++` kit in Qt Creator to build this software.

#### Linux

If you have `clang` on your system, configure the project to use it as the compiler preferentially over `G++`.  `G++` works too, but `clang` is preferred.

#### MacOS

Everything should just work (I use MacOS as my dev machine).

---

### F.A.Q.



**Q:** Why Qt?  This isn't a GUI app!

**A:** Yes, I know.  However, Qt is a very robust, cross-platform and fast application framework.  You can use its "Core" library for console apps, servers, etc.  It has great network support and other basic things a programmer needs to get stuff done.


---

### Donations

Sure!  Send BCH here:

[bitcoincash:qphax4s4n9h60jxj2fkrjs35w2tvgd4wzvf52cgtzc](bitcoincash:qphax4s4n9h60jxj2fkrjs35w2tvgd4wzvf52cgtzc)

[![bitcoincash:qphax4s4n9h60jxj2fkrjs35w2tvgd4wzvf52cgtzc](https://raw.githubusercontent.com/cculianu/DonateSpareChange/master/donate.png)](bitcoincash:qphax4s4n9h60jxj2fkrjs35w2tvgd4wzvf52cgtzc)
