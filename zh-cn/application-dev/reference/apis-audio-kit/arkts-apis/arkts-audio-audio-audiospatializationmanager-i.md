# AudioSpatializationManager

空间音频管理。 在使用AudioSpatializationManager的接口之前，需先通过 [getSpatializationManager]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取AudioSpatializationManager实例。 > **说明：** > > - 本Interface首批接口从API version 18开始支持。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-audio-interface AudioSpatializationManager--><!--Device-audio-interface AudioSpatializationManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

## isSpatializationEnabledForCurrentDevice

```TypeScript
isSpatializationEnabledForCurrentDevice(): boolean
```

获取当前设备空间音频渲染是否开启。同步返回结果。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-AudioSpatializationManager-isSpatializationEnabledForCurrentDevice(): boolean--><!--Device-AudioSpatializationManager-isSpatializationEnabledForCurrentDevice(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前设备空间音频渲染是否开启。true表示开启，false表示未开启。 |

## off('spatializationEnabledChangeForCurrentDevice')

```TypeScript
off(type: 'spatializationEnabledChangeForCurrentDevice', callback?: Callback<boolean>): void
```

取消监听当前设备空间音频渲染开关状态变化事件。使用callback异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-AudioSpatializationManager-off(type: 'spatializationEnabledChangeForCurrentDevice', callback?: Callback<boolean>): void--><!--Device-AudioSpatializationManager-off(type: 'spatializationEnabledChangeForCurrentDevice', callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChangeForCurrentDevice' | 是 | 事件回调类型，支持的事件为'spatializationEnabledChangeForCurrentDevice'，当取消订阅当前设备空间音频渲染开关状态变化事件时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;boolean&gt; | 否 | 回调函数。返回true表示打开空间音频渲染状态；返回false表示关闭空间音频渲染状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## offSpatializationEnabledChangeForCurrentDevice

```TypeScript
offSpatializationEnabledChangeForCurrentDevice(callback?: Callback<boolean>): void
```

Unsubscribes to the spatialization enable state change events by the current device.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AudioSpatializationManager-offSpatializationEnabledChangeForCurrentDevice(callback?: Callback<boolean>): void--><!--Device-AudioSpatializationManager-offSpatializationEnabledChangeForCurrentDevice(callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;boolean&gt; | 否 | Callback used to get the spatialization enable state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## on('spatializationEnabledChangeForCurrentDevice')

```TypeScript
on(type: 'spatializationEnabledChangeForCurrentDevice', callback: Callback<boolean>): void
```

监听当前设备空间音频渲染开关状态变化事件。使用callback异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-AudioSpatializationManager-on(type: 'spatializationEnabledChangeForCurrentDevice', callback: Callback<boolean>): void--><!--Device-AudioSpatializationManager-on(type: 'spatializationEnabledChangeForCurrentDevice', callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'spatializationEnabledChangeForCurrentDevice' | 是 | 事件回调类型，支持的事件为'spatializationEnabledChangeForCurrentDevice'，当空间音频渲染开关状态变化时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;boolean&gt; | 是 | 回调函数。返回true表示打开空间音频渲染状态；返回false表示关闭空间音频渲染状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

## onSpatializationEnabledChangeForCurrentDevice

```TypeScript
onSpatializationEnabledChangeForCurrentDevice(callback: Callback<boolean>): void
```

Subscribes to the spatialization enable state change events by the current device. When the spatialization enable state changes, registered clients will receive the callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AudioSpatializationManager-onSpatializationEnabledChangeForCurrentDevice(callback: Callback<boolean>): void--><!--Device-AudioSpatializationManager-onSpatializationEnabledChangeForCurrentDevice(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;boolean&gt; | 是 | Callback used to get the spatialization enable state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |

