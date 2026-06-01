# zlib

<!-- md-trans-meta sourceCommit=7322f9d523f66911f71514248bc2b0cdc9af44ee translatedAt=2026-05-28T03:07:46.171Z pushedAt=2026-05-28T09:05:19.305Z -->
## Introduction

[zlib](https://zlib.net/) is a general data compression library implemented in C/C++.

## Supported Capabilities

The zlib library provides in-memory data compression and decompression capabilities using the Deflate algorithm. It supports different compression levels and delivers good compression results for various types of data. It also offers control over processor and memory usage. If the buffer is large enough, compression can be completed in a single step; otherwise, it can be achieved by repeatedly calling the compression API.

By default, the zlib interfaces use the zlib format ([RFC1950](https://www.rfc-editor.org/rfc/rfc1950)). In addition, the zlib library provides interfaces that start with gz to read and write gzip files ([RFC1952](https://www.rfc-editor.org/rfc/rfc1952)). The zlib format is designed for efficient use in memory and communication channels, ensuring both compactness and swift performance. The gzip format is designed for the compression of individual files. Its header is larger than that of zlib in order to maintain directory information. gzip uses a check method that, while different, is comparatively slower than the one used by zlib.

The decoder within the zlib library checks the integrity of compressed data. Therefore, the library will not crash even in the case of corrupted input.

## Introducing zlib

To use zlib capabilities, include the following header file:

```c
#include <zlib.h>
```

Add the following dynamic link library to **CMakeLists.txt**:

```
libz.so
```

## Supported APIs

For details, see [zlib](https://www.zlib.net/manual.html).