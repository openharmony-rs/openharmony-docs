# OpenSL ES
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=96f4a6288457dc7323c09f4157fef4291d5dc537 translatedAt=2026-11-04T04:23:07.597Z pushedAt=2026-11-04T08:04:44.651Z nl=1 -->

> **NOTE**
>
> OpenHarmony provides the OpenSL ES APIs for audio development at the native layer since SDK 8. As the version evolves, these APIs fail to meet the capability expansion requirements of the audio system and therefore are no longer recommended. [Switch from OpenSL ES to OHAudio](../../media/audio/replace-opensles-by-ohaudio.md).

## Introduction

OpenSL ES (Open Sound Library for Embedded Systems) is the embedded audio acceleration standard. It provides developers with standardized, high-performance, and low-latency objects and interfaces for developing audio functions. Compared with the open-source and free OpenSL ES, OpenHarmony implements some native APIs based on the [OpenSL ES](https://www.khronos.org/opensles/) 1.0.1 API specification. The supported APIs are listed in the table [Supported APIs](#supported-apis).

## Introducing OpenSL ES

To use OpenSL ES capabilities, include the following header files:

```c++
#include <SLES/OpenSLES.h>
#include <SLES/OpenSLES_OpenHarmony.h>
#include <SLES/OpenSLES_Platform.h>
```

Add the following dynamic link library to **CMakeLists.txt**:

```c++
libOpenSLES.so
```

## Supported APIs

|Object               |External API              |API Invocation                                                                          |Supported  |Description                 |
| ------------------ | -------------------- | -------------------------------------------------------------------------------------|----------| -------------------- |
|SLEngineItf         |CreateAudioPlayer     |CreateAudioPlayer(SLEngineItf self, SLObjectItf *pPlayer, SLDataSource *pAudioSrc, SLDataSink *pAudioSnk, SLuint32 numInterfaces, const SLInterfaceID *pInterfaceIds, const SLboolean *pInterfaceRequired) |Yes       |Creates an audio player.       |
|SLEngineItf         |CreateAudioRecorder   |CreateAudioRecorder(SLEngineItf self, SLObjectItf *pRecorder, SLDataSource *pAudioSrc, SLDataSink *pAudioSnk, SLuint32 numInterfaces, const SLInterfaceID *pInterfaceIds, const SLboolean *pInterfaceRequired)|Yes       |Creates an audio recorder.       |
|SLEngineItf         |CreateOutputMix  |CreateOutputMix(SLEngineItf self, SLObjectItf *pMix, SLuint32 numInterfaces, const SLInterfaceID *pInterfaceIds, const SLboolean *pInterfaceRequired)|Yes        |Creates an audio output mixer.            |
|SLObjectItf         |Realize               |Realize(SLObjectItf self, SLboolean async)                                            |Yes       |Realizes an audio player.       |
|SLObjectItf         |getState              |GetState(SLObjectItf self, SLuint32 *pState)                                           |Yes       |Obtains the state.            |
|SLObjectItf         |getInterface          |GetInterface(SLObjectItf self, const SLInterfaceID iid, void *pInterface)              |Yes       |Obtains the interface.            |
|SLObjectItf         |Destroy               |Destroy(SLObjectItf self)                                                             |Yes       |Destroys an object.            |
|SLOHBufferQueueItf  |Enqueue               |Enqueue(SLOHBufferQueueItf self, const void *pBuffer, SLuint32 size)                   |Yes       |Adds a buffer to the queue.|
|SLOHBufferQueueItf  |clear                 |Clear(SLOHBufferQueueItf self)                                                        |Yes       |Releases the buffer queue.        |
|SLOHBufferQueueItf  |getState              |GetState(SLOHBufferQueueItf self, SLOHBufferQueueState *pState)                        |Yes       |Obtains the BufferQueue status. |
|SLOHBufferQueueItf  |getBuffer             |GetBuffer(SLOHBufferQueueItf self, SLuint8 **buffer, SLuint32 *size)                  |Yes       |Obtains a buffer.          |
|SLOHBufferQueueItf  |RegisterCallback      |RegisterCallback(SLOHBufferQueueItf self, SlOHBufferQueueCallback callback, void *pContext) |Yes |Registers a callback.         |
|SLPlayItf           |SetPlayState          |SetPlayState(SLPlayItf self, SLuint32 state)                                          |Yes       |Sets the playback state.         |
|SLPlayItf           |GetPlayState          |GetPlayState(SLPlayItf self, SLuint32 *pState)                                         |Yes       |Obtains the playback state.         |
|SLRecordItf         |SetRecordState        |SetRecordState(SLRecordItf self, SLuint32 state)                                      |Yes       |Sets the recording state.         |
|SLRecordItf         |GetRecordState        |GetRecordState(SLRecordItf self, SLuint32 *pState)                                   |Yes       |Obtains the recording state.         |
|SLVolumeItf         |SetVolumeLevel        |SetVolumeLevel(SLVolumeItf self, SLmillibel level)                                   |Yes       |Sets the volume.             |
|SLVolumeItf         |GetVolumeLevel        |GetVolumeLevel(SLVolumeItf self, SLmillibel *pLevel)                                    |Yes       |Obtains the volume.             |
|SLVolumeItf         |GetMaxVolumeLevel     |GetMaxVolumeLevel(SLVolumeItf self, SLmillibel *pMaxLevel)                             |Yes       |Obtains the maximum volume.         |