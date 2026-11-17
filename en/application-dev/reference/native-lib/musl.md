# musl libc
<!--Kit: ArkTS-->	 
<!--Subsystem: arkcompiler-->
<!--Owner: @da_wei_li11-->
<!--Designer: @liyiming13-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=eaf834c0e8a7b1d52ab7109799c81fa57c16f64e translatedAt=2026-11-06T12:15:52.140Z pushedAt=2026-11-13T11:22:18.696Z nl=2 -->

## Overview
The C standard library (libc) provides standard header files and common library implementations (such as input/output processing and string handling) in C language programming.

OpenHarmony uses musl as the libc. musl is a lightweight, fast, simple, and free open-source libc. For details, see [musl libc Reference Manual](http://musl.libc.org/manual.html).

For details about the differences between musl and glibc, see [Functional differences from glibc](https://wiki.musl-libc.org/functional-differences-from-glibc.html).

## libc Components

C11 is implemented by [libc, libm, and libdl](https://en.cppreference.com/w/c/header).

libc: provides thread-related interfaces and a majority of standard interfaces.

libm: provides mathematical library interfaces. Currently, OpenHarmony provides a link to libm, and the interfaces are defined in libc.

libdl: provides dynamic linker interfaces such as dlopen. Currently, OpenHarmony provides a link to libdl, and the interfaces are defined in libc.

## musl Version

1.2.0

1.2.3 since OpenHarmony 4.0

1.2.5 since OpenHarmony 5.0

## Supported Capabilities
Provides header files and library function interfaces compatible with C99, C11, and POSIX standards, but not fully compatible. Currently supports three architectures: armv7a, arm64, and x86_64.

To better adapt to the basic characteristics of OpenHarmony devices, such as high performance, low memory, high security, lightweight design, and support for multiple device forms, optimizations and enhancements are made based on the musl open-source library, and interfaces that are not suitable for embedded devices are trimmed.

### New Capabilities
1. The dynamic loader supports namespace isolation. Dynamic libraries loaded by applications through dlopen are restricted by the system namespace (for example, system-side dynamic libraries cannot be opened).
2. **dlclose()** can be used to unload a dynamic library. This capability is not supported by musl.
3. The symbol-versioning is supported.
4. **dlopen()** can directly load uncompressed files in a .zip package.
5. Supports C API compatibility version protection.
6. Starting from API version 26.1.0, some new interfaces are added. For details, see [New Interfaces in musl 26.1.0](musl-new-api-26-1-0.md).
<!--Del-->
### Debugging Capabilities
The libc provides dynamic enabling of debug logging (enabled by default). The debug logs help you learn about exceptions of the libc. With this function, you only need to set **param**, which eliminates the need for rebuilding the libc. However, you are advised not to enable debug logging in official versions because it affects the running performance.

**Functionality of musl.log**

Set **musl.log.enable** to **true** to enable printing of musl debug logs. You need to enable musl.log before printing other logs.
```
param set musl.log.enable true
```

**Loader Logging**

The loader starts applications and invokes **dlopen** and **dlclose** in the libc. To view exceptions during the loading process, you need to enable the loader logging function. The following describes common operations.
* Enable the loader logging for all applications. Exercise caution when enabling this function because a large number of logs will be generated.
```
param set musl.log.ld.app true
```
* Enable the loader logging for an application specified by {app_name}.
```
param set musl.log.ld.all false
param set musl.log.ld.app.{app_name} true
```
* Enable the loader logging for all applications except the specified application.
```
param set musl.log.ld.all true
param set musl.log.ld.app.{app_name} false
```
<!--DelEnd-->
## APIAVAILABLE Compatibility Version Protection

> **Note**
>
> To use the APIAVAILABLE feature, you must be very familiar with mechanisms such as strong symbols, weak symbols, and weak libraries, and strictly follow the steps in the guide. Otherwise, runtime crashes may occur.
> Usability is being optimized. Before the optimization is complete, it is recommended to use dlopen and dlsym to resolve compatibility issues.

| Macro Definition Name | Description |
|:--|:--|
| APIAVAILABLE(maj, min, patch) | Used together with the compiler to ensure compatibility and stability of applications across different system versions. Through compile-time and runtime condition checks, it prevents crashes caused by calling nonexistent APIs on lower system versions. When using an API higher than the target distribution version (compatibleSdkVersion), you must use this macro for compatibility protection and provide a reasonable fallback solution. The input parameter **maj** is the major version number (value range 0-99), **min** is the minor version number (value range 0-99), and **patch** is the patch version number (value range 0-99).<br/>**Start version:** 22 |

## musl API Difference

| API         | Description                                                                                        |
|:--               |    :--                                                                                       |
| epoll_create     | In the current OpenHarmony musl repository, epoll_create does not validate the size input parameter and does not distinguish whether size is less than or equal to 0. The actual behavior is: when size <= 0, the call may still create an epoll instance successfully. This behavior differs from musl community v1.2.5 and later versions. The musl community requires size to be greater than 0, and the interface behaves as follows: when size <= 0, epoll_create should fail, return -1, and set errno to EINVAL. If developers need to be compatible with musl community v1.2.5+ behavior, it is recommended to ensure size > 0 before calling epoll_create, or prefer using epoll_create1. |
| pthread_join     | When the target thread is in the detached state (for example, detached via pthread_detach, or created with the PTHREAD_CREATE_DETACHED attribute), before API version 26.1.0, OpenHarmony musl behaved the same as the musl community version and would trigger a process crash; starting from API version 26.1.0, the behavior changes to directly returning EINVAL without crashing, which differs from the musl community version (which still crashes). This error code is returned directly by the interface return value and is not set through errno. If developers need to be compatible with different system versions, it is recommended to avoid calling pthread_join on a thread in the detached state; if the call is still required, note that only from API version 26.1.0 onward can error handling be performed by checking whether the return value is EINVAL, while earlier versions crash directly and cannot be determined through the return value. |

## Character Encoding Formats Supported by iconv

Character set encoding formats supported by musl, and the supported aliases.
> **Note**
>
> When converting character set encoding formats, use the correct source character set encoding format, and the target character set encoding format must support the characters to be converted. Otherwise, the conversion fails.
> In musl, conversion from the source character set encoding format to the following two target character set encoding formats is not supported: big5, euckr.

| Encoding Format| Alias                  | Supported by musl|
|:--      |    :--                   |  :--:  |
|utf8     |                          |  Yes  |
|wchart   |                          |  Yes  |
|ucs2be   |                          |  Yes  |
|ucs2le   |                          |  Yes  |
|utf16be  |                          |  Yes  |
|utf16le  |                          |  Yes  |
|ucs4be   |utf32be                   |  Yes  |
|ucs4le   |utf32le                   |  Yes  |
|ascii    |usascii, iso646, iso646us |  Yes  |
|utf16    |                          |  Yes  |
|ucs4     |utf32                     |  Yes  |
|ucs2     |                          |  Yes  |
|eucjp    |                          |  Yes  |
|shiftjis |sjis, cp932               |  Yes  |
|iso2022jp|                          |  Yes  |
|gb18030  |                          |  Yes  |
|gbk      |                          |  Yes  |
|gb2312   |                          |  Yes  |
|big5     |bigfive, cp950, big5hkscs |  Yes  |
|euckr    |ksc5601, ksx1001, cp949   |  Yes  |
|iso88591 |latin1                    |  Yes  |
|iso88592 |                          |  Yes  |
|iso88593 |                          |  Yes  |
|iso88594 |                          |  Yes  |
|iso88595 |                          |  Yes  |
|iso88596 |                          |  Yes  |
|iso88597 |                          |  Yes  |
|iso88598 |                          |  Yes  |
|iso88599 |                          |  Yes  |
|iso885910|                          |  Yes  |
|iso885911|tis620                    |  Yes  |
|iso885913|                          |  Yes  |
|iso885914|                          |  Yes  |
|iso885915|latin9                    |  Yes  |
|iso885916|                          |  Yes  |
|cp1250   |windows1250               |  Yes  |
|cp1251   |windows1251               |  Yes  |
|cp1252   |windows1252               |  Yes  |
|cp1253   |windows1253               |  Yes  |
|cp1254   |windows1254               |  Yes  |
|cp1255   |windows1255               |  Yes  |
|cp1256   |windows1256               |  Yes  |
|cp1257   |windows1257               |  Yes  |
|cp1258   |windows1258               |  Yes  |
|koi8r    |                          |  Yes  |
|koi8u    |                          |  Yes  |
|cp437    |                          |  Yes  |
|cp850    |                          |  Yes  |
|cp866    |                          |  Yes  |
|cp1047   |ibm1047                   |  Yes  |

## Unsupported musl Interfaces

[Native API Symbols Not Exported](musl-peculiar-symbol.md)

[NDK-Related musl libc Interface Usage Restrictions](guidance-on-ndk-libc-interfaces-affected-by-permissions.md)

[NDK musl-libc Supplementary APIs](https://gitcode.com/openharmony/third_party_musl/tree/master/docs)
<!--no_check-->
