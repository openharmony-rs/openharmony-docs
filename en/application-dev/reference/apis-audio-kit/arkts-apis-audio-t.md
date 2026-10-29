# Types
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4575f288d13c429dbede3c0b33d0bfd71bcb7755 translatedAt=2026-10-08T12:12:13.749Z pushedAt=2026-10-12T10:21:07.486Z -->

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## AudioRendererChangeInfoArray<sup>9+</sup>

type AudioRendererChangeInfoArray = Array&lt;Readonly&lt;AudioRendererChangeInfo&gt;&gt;

Defines an AudioRendererChangeInfo array, which is read-only.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

| Type     | Description                                                           |
|---------|---------------------------------------------------------------|
| Array&lt;Readonly&lt;AudioRendererChangeInfo&gt;&gt; | An [AudioRendererChangeInfo](arkts-apis-audio-i.md#audiorendererchangeinfo9) array, which is read-only.|


## AudioCapturerChangeInfoArray<sup>9+</sup>

type AudioCapturerChangeInfoArray = Array&lt;Readonly&lt;AudioCapturerChangeInfo&gt;&gt;

Defines an AudioCapturerChangeInfo array, which is read-only.

**System capability**: SystemCapability.Multimedia.Audio.Capturer

| Type     | Description                                                             |
|---------|-----------------------------------------------------------------|
| Array&lt;Readonly&lt;AudioCapturerChangeInfo&gt;&gt; | An [AudioCapturerChangeInfo](arkts-apis-audio-i.md#audiocapturerchangeinfo9) array, which is read-only.|


## AudioEffectInfoArray<sup>10+</sup>

type AudioEffectInfoArray = Array&lt;Readonly&lt;AudioEffectMode&gt;&gt;

Defines an array that contains the audio effect mode corresponding to a specific audio content type (specified by **ContentType**) and audio stream usage (specified by **StreamUsage**). The [AudioEffectMode](arkts-apis-audio-e.md#audioeffectmode10) array is read-only.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

| Type     | Description                                                           |
|---------|---------------------------------------------------------------|
| Array&lt;Readonly&lt;AudioEffectMode&gt;&gt; | Array that contains the audio effect mode corresponding to a specific audio content type (specified by **ContentType**) and audio stream usage (specified by **StreamUsage**). The [AudioEffectMode](arkts-apis-audio-e.md#audioeffectmode10) array is read-only. |

## AudioDeviceDescriptors

type AudioDeviceDescriptors = Array&lt;Readonly&lt;AudioDeviceDescriptor&gt;&gt;

Defines an [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) array, which is read-only.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Audio.Device

| Type     | Description                                                           |
|---------|---------------------------------------------------------------|
| Array&lt;Readonly&lt;AudioDeviceDescriptor&gt;&gt; | Defines an [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) array, which is read-only.|


## AudioRendererWriteDataCallback<sup>12+</sup>

type AudioRendererWriteDataCallback = (data: ArrayBuffer) => AudioDataCallbackResult | void

Callback function type used for writing data to the audio renderer. After the callback function ends, the audio service places the data pointed to by data into a queue to wait for playback. Therefore, do not modify the data pointed to by data again outside the callback, and ensure that data is filled with the data to be played; otherwise, noise may occur during audio playback.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

**Parameters**

| Name         | Type     |Mandatory  | Description        |
| :--------------| :--------| :----- | :------------ |
| data           | ArrayBuffer  | Yes| Data to be written to the buffer.|

**Return value** 

| Type                                                          | Description                                                                                                         |
|--------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [AudioDataCallbackResult](arkts-apis-audio-e.md#audiodatacallbackresult12) \| void | If **void** or **AudioDataCallbackResult.VALID** is returned, the data is valid and the audio data is played. If **AudioDataCallbackResult.INVALID** is returned, the data is invalid and the audio data is not played.|

## DeviceTypeArray

type DeviceTypeArray = Array&lt;DeviceType&gt;

Defines the device type, which is a [DeviceType](arkts-apis-audio-e.md#devicetype) array.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Device

| Type      | Description                                                            |
|---------|---------------------------------------------------------------|
| Array&lt; [DeviceType](arkts-apis-audio-e.md#devicetype)&gt; | DeviceType array. |