# Types

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1961de06e85063963f633ec54a8a4baaf5cb7dc8 translatedAt=2026-07-21T03:49:03.883Z pushedAt=2026-07-21T07:08:51.761Z -->

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

Audio effect mode array type for scenarios combining `ContentType` and `StreamUsage`. It is an [AudioEffectMode](arkts-apis-audio-e.md#audioeffectmode10) array and read-only.

**System capability**: SystemCapability.Multimedia.Audio.Renderer

| Type     | Description                                                           |
|---------|---------------------------------------------------------------|
| Array&lt;Readonly&lt;AudioEffectMode&gt;&gt; | Audio effect mode array type for scenarios combining `ContentType` and `StreamUsage`. It is an [AudioEffectMode](arkts-apis-audio-e.md#audioeffectmode10) array and read-only. |

## AudioDeviceDescriptors

type AudioDeviceDescriptors = Array&lt;Readonly&lt;AudioDeviceDescriptor&gt;&gt;

Defines an [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) array, which is read-only.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Audio.Device

| Type     | Description                                                           |
|---------|---------------------------------------------------------------|
| Array&lt;Readonly&lt;AudioDeviceDescriptor&gt;&gt; | [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) array, which is read-only.|

## AudioRendererWriteDataCallback<sup>12+</sup>

type AudioRendererWriteDataCallback = (data: ArrayBuffer) => AudioDataCallbackResult | void

Callback function type used for writing data to the audio renderer. After the callback ends, the audio service places the data pointed to by **data** into a queue for playback. Therefore, do not modify the data pointed to by **data** outside the callback, and ensure that **data** is fully filled with the data to be played. Otherwise, noise may occur during audio playback.

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

Array type, which is a [DeviceType](arkts-apis-audio-e.md#devicetype) array.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Device

| Type | Description |
|---------|---------------------------------------------------------------|
| Array&lt; [DeviceType](arkts-apis-audio-e.md#devicetype)&gt; | DeviceType array. |