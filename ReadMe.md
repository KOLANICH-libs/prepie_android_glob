Implementation of `glob` available to be used for old Android phones
====================================================================

`glob` is officially supported on Android since Pie (Android 9, API Level 28).

It prevents some apps from being built for Android.

Fortunately, [FreeBSD(https://github.com/freebsd/freebsd) has an impl of `glob` and Google has adopted it for its [Bionic](https://github.com/aosp-mirror/platform_bionic/) library. I have just adapted the parts of FreeBSD and Bionic and some functions from [`libbsd`](https://github.com/freedesktop/libbsd) to create a library that can be added to software in order to allow it to be compiled for pre-Pie versions of Android.

More precisely:
* https://github.com/aosp-mirror/platform_bionic/blob/92c6f7ee9014f434fbcce89ab894c745e36732d2/libc/upstream-freebsd/lib/libc/gen/glob.c
* https://github.com/freebsd/freebsd/blob/1d6e4247415d264485ee94b59fdbc12e0c566fd0/include/glob.h
* https://github.com/freebsd/freebsd/blob/03c216ce761c84dbe6ab7611453931211e923986/sys/arm/include/atomic-v4.h
* https://github.com/freedesktop/libbsd/blob/7cfa2d4530325444fa71c2bdb14e11ba9d4de0b6/src/reallocarray.c


This is only for ARMv7. I have inlined some pieces of needed files from FreeBSD source instead of bringing whole includes. If you need to compile to other archs, you should replace all the code related to atomics to the code from the needed arch from FreeBSD source.

So the license of this is [BSD-2-Clause-FreeBSD](https://tldrlegal.com/license/bsd-2-clause-license-(freebsd)) [AND](https://spdx.dev/spdx-specification-21-web-version/#h.jxpfx0ykyb60) [BSD-3-Clause](https://tldrlegal.com/license/bsd-3-clause-license-(revised)) AND [ISC](https://tldrlegal.com/license/-isc-license).
