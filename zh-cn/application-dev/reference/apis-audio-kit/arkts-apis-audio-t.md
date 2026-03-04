# Types

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## AudioRendererChangeInfoArray<sup>9+</sup>

type AudioRendererChangeInfoArray = Array&lt;Readonly&lt;AudioRendererChangeInfo&gt;&gt;

数组类型，AudioRenderChangeInfo数组，只读。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

| 类型      | 说明                                                            |
|---------|---------------------------------------------------------------|
| Array&lt;Readonly&lt;AudioRendererChangeInfo&gt;&gt; | 数组类型，[AudioRendererChangeInfo](arkts-apis-audio-i.md#audiorendererchangeinfo9)数组，只读。 |


## AudioCapturerChangeInfoArray<sup>9+</sup>

type AudioCapturerChangeInfoArray = Array&lt;Readonly&lt;AudioCapturerChangeInfo&gt;&gt;

数组类型，AudioCapturerChangeInfo数组，只读。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

| 类型      | 说明                                                              |
|---------|-----------------------------------------------------------------|
| Array&lt;Readonly&lt;AudioCapturerChangeInfo&gt;&gt; | 数组类型，[AudioCapturerChangeInfo](arkts-apis-audio-i.md#audiocapturerchangeinfo9)数组，只读。 |


## AudioEffectInfoArray<sup>10+</sup>

type AudioEffectInfoArray = Array&lt;Readonly&lt;AudioEffectMode&gt;&gt;

待查询ContentType和StreamUsage组合场景下的音效模式数组类型，[AudioEffectMode](arkts-apis-audio-e.md#audioeffectmode10)数组，只读。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

| 类型      | 说明                                                            |
|---------|---------------------------------------------------------------|
| Array&lt;Readonly&lt;AudioEffectMode&gt;&gt; | 待查询ContentType和StreamUsage组合场景下的音效模式数组类型，[AudioEffectMode](arkts-apis-audio-e.md#audioeffectmode10)数组，只读。 |

## AudioDeviceDescriptors

type AudioDeviceDescriptors = Array&lt;Readonly&lt;AudioDeviceDescriptor&gt;&gt;

设备属性数组类型，为[AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor)的数组，只读。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 20

| 类型      | 说明                                                            |
|---------|---------------------------------------------------------------|
| Array&lt;Readonly&lt;AudioDeviceDescriptor&gt;&gt; | 设备属性数组类型，为[AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor)的数组，只读。 |


## AudioRendererWriteDataCallback<sup>12+</sup>

type AudioRendererWriteDataCallback = (data: ArrayBuffer) => AudioDataCallbackResult | void

回调函数类型，用于音频渲染器的数据写入，回调函数结束后，音频服务会把data指向的数据放入队列里等待播放，因此请勿在回调外再次更改data指向的数据, 且务必保证往data填满待播放数据, 否则会导致音频服务播放杂音。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名          | 类型      |必填   | 说明         |
| :--------------| :--------| :----- | :------------ |
| data           | ArrayBuffer  | 是 | 待写入缓冲区的数据。 |

**返回值：** 

| 类型                                                           | 说明                                                                                                          |
|--------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [AudioDataCallbackResult](arkts-apis-audio-e.md#audiodatacallbackresult12) \| void | 如果返回 void 或 AudioDataCallbackResult.VALID：表示数据有效，将播放音频数据；如果返回 AudioDataCallbackResult.INVALID：表示数据无效，且音频数据不播放。 |


## AudioRendererWriteDataCallback<sup>23+</sup>

type AudioRendererWriteDataCallback = (data: ArrayBuffer) => AudioDataCallbackResult

回调函数结束后，音频服务会把data指向的数据放入队列里等待播放，请勿在回调外再次更改data指向的数据，且务必保证往data填满待播放数据，否则会导致音频服务播放杂音。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名          | 类型      |必填   | 说明         |
| :--------------| :--------| :----- | :------------ |
| data           | ArrayBuffer  | 是 | 待写入缓冲区的数据。 |

**返回值：** 

| 类型                                                           | 说明                                                                                                          |
|--------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [AudioDataCallbackResult](arkts-apis-audio-e.md#audiodatacallbackresult12) | - 如果返回AudioDataCallbackResult.VALID：表示数据有效，将播放音频数据。<br>- 如果返回 AudioDataCallbackResult.INVALID：表示数据无效，且音频数据不播放。 |
