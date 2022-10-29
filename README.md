# Config
My collection of config files for Linux, mostly for Gentoo Linux. 
Generally set up for systemd + KDE.

- Kernel .config for Gentoo Linux with systemd + nvidia card, with patch for -match=native for intel CPU, compiled with LLVM using LTO.
- Porage config, using git for sync. 
- make settings, package flags, and package.env made to compile whole system with clang using libc++, lld and LLVM tools in general. (only gcc and glibc built with gcc, maybe replace with musl in the future)
- Masked qtwebengine because it takes ages to compile without ccache or something, use at your own peril

When creating your own system, first compile clang + llvm with these flags with whatever compiler you have avaliable (you might need to disable LTO for it, use gcc or other tricks)
It's important to make clang always use lld and libc++.


If when at some point rebuilding your whole system to use libc++ you get an error from cmake, about undefined symbol from jsoncpp it means that jsoncpp has been recompiler to use libc++ while cmake depends on it being built with libstdc++ (from gcc), easiest solution is to download cmake sources, configure and install it without cmake, portage should pick up that version instead of the one managed by it and it should work, when you then rebuild cmake to use libc++ as well you can uninstall the cmake you compiler yourself.
