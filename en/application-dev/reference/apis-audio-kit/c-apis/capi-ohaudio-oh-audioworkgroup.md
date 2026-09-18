# OH_AudioWorkgroup

```c
typedef struct OH_AudioWorkgroup OH_AudioWorkgroup
```

## Overview

Declare the audio workgroup. The handle of audio workgroup is used for workgroup related functions. The system will manage cpu resources on a workgroup basis instead of thread. For parallel task threads, you can add them into one workgroup, and for asynchronous task threads, use one workgroup for each thread. There is an upper limit to the total number of workgroups for each process, so application should release the workgroup which is no longer in use.

**Since**: 20

**Related module**: [OHAudio](capi-ohaudio.md)

**Header file**: [native_audio_resource_manager.h](capi-native-audio-resource-manager-h.md)

