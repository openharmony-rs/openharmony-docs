# OHAudio
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=fea09459a0476f095195448c2ce1ed787d76ab6a translatedAt=2026-11-10T03:08:14.507Z pushedAt=2026-11-10T04:47:23.429Z nl=1 -->

## Overview

The module provides audio-related C APIs.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

## Files

| Name| Description|
| -- | -- |
| [native_audiocapturer.h](capi-native-audiocapturer-h.md) | Declares the APIs related to audio capture. |
| [native_audio_manager.h](capi-native-audio-manager-h.md) | Declares the functions related to an audio manager.|
| [native_audio_resource_manager.h](capi-native-audio-resource-manager-h.md) | Declares the functions related to an audio resource manager.|
| [native_audio_routing_manager.h](capi-native-audio-routing-manager-h.md) | Declares the APIs related to the audio routing manager.<br> Contains APIs for creating an AudioRoutingManager, registering and unregistering listeners for device connection state changes, and releasing the pointer array that stores device information. |
| [native_audio_session_manager.h](capi-native-audio-session-manager-h.md) | Declares the functions related to an audio session manager.<br> You can call the functions to create an audio session manager, activate or deactivate an audio session, check whether an audio session is activated, and listen for audio session deactivation events.|
| [native_audio_stream_manager.h](capi-native-audio-stream-manager-h.md) | Declares the APIs related to the audio stream manager.<br> The APIs in this file are used to create an AudioStreamManager and to set and manage audio streams. |
| [native_audio_volume_manager.h](capi-native-audio-volume-manager-h.md) | Declares the functions related to an audio volume manager. You can call the functions to create an audio volume manager.|
| [native_audiorenderer.h](capi-native-audiorenderer-h.md) | Declares the functions related to an audio renderer.|
| [native_audio_common.h](capi-native-audio-common-h.md) | Declares the common basic audio data structs.<br> It defines the types of the common return values of audio interfaces.|
| [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md) | Declares the public data structures of the external audio accessory device interfaces. |
| [native_audio_accessory_manager.h](capi-native-audio-accessory-manager-h.md) | Declares the APIs related to the audio accessory manager. |
| [native_audio_accessory_input_stream_manager.h](capi-native-audio-accessory-input-stream-manager-h.md) | Declares the APIs related to the audio accessory input stream manager. |
| [native_audio_device_base.h](capi-native-audio-device-base-h.md) | Declares the types of audio device parameters and the functions for obtaining these parameters.|
| [native_audiostream_base.h](capi-native-audiostream-base-h.md) | Declares the basic data structure of OHAudio.|
| [native_audiostreambuilder.h](capi-native-audiostreambuilder-h.md) | Declares the APIs related to the audio stream builder.<br> Contains APIs for constructing and destroying the builder, and setting audio stream attributes and callbacks. |

