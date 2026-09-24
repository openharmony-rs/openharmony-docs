# AVPlayerCallback

```c
typedef struct AVPlayerCallback {...} AVPlayerCallback
```

## Overview

The struct contains the set of the **OH_AVPlayerOnInfo** and **OH_AVPlayerOnError** callback function pointers. To ensure the normal running of OH_AVPlayer, you must register the instance of this struct with the OH_AVPlayer instance and process the information reported by the callback functions.

**Since**: 11

**Deprecated**: 12

**Replaced by**: {@link OH_AVPlayerOnInfoCallback} {@link OH_AVPlayerOnErrorCallback}

**Related module**: [AVPlayer](capi-avplayer.md)

**Header file**: [avplayer_base.h](capi-avplayer-base-h.md)

