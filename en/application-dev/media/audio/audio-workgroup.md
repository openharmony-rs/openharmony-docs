# Audio Workgroup Management
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

The audio workgroup is a set of APIs that help the system identify key audio threads within an application through tagging. By providing key audio threads and workgroup runtime information, the system can ensure healthier operation of audio threads.

The examples in each of the following steps are code snippets. You can click the link at the bottom right of the sample code to obtain the [complete sample codes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleC).

## How to Use

For audio playback applications, you need to create an audio workgroup first and then periodically inform the system of the workgroup's runtime information. After the work is completed, it is necessary to clean up the audio workgroup.

### Obtaining an AudioResourceManager Instance

Before calling any API of OH_AudioWorkgroup, you must use [OH_AudioManager_GetAudioResourceManager](../../reference/apis-audio-kit/capi-native-audio-resource-manager-h.md#oh_audiomanager_getaudioresourcemanager) to obtain an OH_AudioResourceManager instance.

<!-- @[GetAudioResourceManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleC/entry/src/main/cpp/renderer.cpp) -->

``` C++
#include <ohaudio/native_audio_resource_manager.h>
// ...
OH_AudioResourceManager *resMgr;
// ...
    OH_AudioManager_GetAudioResourceManager(&resMgr);
```

### Creating an Audio Workgroup and Adding Key Threads

Call [OH_AudioResourceManager_CreateWorkgroup](../../reference/apis-audio-kit/capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_createworkgroup) to create an audio workgroup, and then call [OH_AudioWorkgroup_AddCurrentThread](../../reference/apis-audio-kit/capi-native-audio-resource-manager-h.md#oh_audioworkgroup_addcurrentthread) to add key threads to the workgroup.

<!-- @[CreateWorkgroup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleC/entry/src/main/cpp/renderer.cpp) -->

``` C++
#include <chrono>
// ...
int32_t g_tokenId;
OH_AudioWorkgroup *grp = nullptr;
// ...
    OH_AudioResourceManager_CreateWorkgroup(resMgr, "workgroup", &grp);
    OH_AudioWorkgroup_AddCurrentThread(grp, &g_tokenId);
```

### Notifying the System of Workgroup Start and End

When an audio workgroup begins a cycle of work, you can notify the system of the task's start time and expected end time. When the workgroup finishes its work for the current cycle, notify the system that the task has ended.

<!-- @[OH_AudioWorkgroup_Start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleC/entry/src/main/cpp/renderer.cpp) -->

``` C++
constexpr static uint64_t intervalMs = 20;
bool threadShouldRun = true;

while (threadShouldRun) {
    auto now = std::chrono::system_clock::now().time_since_epoch();
    auto startTimeMs = std::chrono::duration_cast<std::chrono::milliseconds>(now).count();
    OH_AudioWorkgroup_Start(grp, startTimeMs, startTimeMs + intervalMs);
    threadShouldRun = false;
    // Process audio data.
    OH_AudioWorkgroup_Stop(grp);
}
```

### Cleanup After Workgroup Task Completion

<!-- @[OH_AudioWorkgroup_RemoveThread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleC/entry/src/main/cpp/renderer.cpp) -->

``` C++
// Remove the thread from the workgroup when it is no longer required.
OH_AudioWorkgroup_RemoveThread(grp, g_tokenId);

OH_AudioResourceManager_ReleaseWorkgroup(resMgr, grp);
grp = nullptr;
```
