# ScreenCaptureMonitor（系统接口）

A class that provides APIs to query and monitor the system screen recorder status. Before calling any API, you must use getScreenCaptureMonitor() to obtain a ScreenCaptureMonitor instance.

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-unnamed-interface ScreenCaptureMonitor--><!--Device-unnamed-interface ScreenCaptureMonitor-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

## off('systemScreenRecorder')

```TypeScript
off(type: 'systemScreenRecorder', callback?: Callback<ScreenCaptureEvent>): void
```

Unsubscribes from state change events of the system screen recorder.

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-ScreenCaptureMonitor-off(type: 'systemScreenRecorder', callback?: Callback<ScreenCaptureEvent>): void--><!--Device-ScreenCaptureMonitor-off(type: 'systemScreenRecorder', callback?: Callback<ScreenCaptureEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'systemScreenRecorder' | 是 | Event type, which is **'systemScreenRecorder'** in this case.This event is triggered when the state of the system screen recorder changes. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ScreenCaptureEvent&gt; | 否 | Callback invoked when the event is triggered,where ScreenCaptureEvent indicates the new state. If this parameter is not specified,the last subscription event is canceled. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

**示例：**

```TypeScript
screenCaptureMonitor.off('systemScreenRecorder');
```

## offSystemScreenRecorder

```TypeScript
offSystemScreenRecorder(callback?: Callback<ScreenCaptureEvent>): void
```

Unsubscribes from state change events of the system screen recorder. This event is triggered when the state of the system screen recorder changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ScreenCaptureMonitor-offSystemScreenRecorder(callback?: Callback<ScreenCaptureEvent>): void--><!--Device-ScreenCaptureMonitor-offSystemScreenRecorder(callback?: Callback<ScreenCaptureEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ScreenCaptureEvent&gt; | 否 | Callback invoked when the event is triggered,where ScreenCaptureEvent indicates the new state. If this parameter is not specified,the last subscription event is canceled. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

## on('systemScreenRecorder')

```TypeScript
on(type: 'systemScreenRecorder', callback: Callback<ScreenCaptureEvent>): void
```

Subscribes to state change events of the system screen recorder. From the ScreenCaptureEvent event reported, you can determine whether the system screen recorder is working.

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-ScreenCaptureMonitor-on(type: 'systemScreenRecorder', callback: Callback<ScreenCaptureEvent>): void--><!--Device-ScreenCaptureMonitor-on(type: 'systemScreenRecorder', callback: Callback<ScreenCaptureEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'systemScreenRecorder' | 是 | Event type, which is **'systemScreenRecorder'** in this case.This event is triggered when the state of the system screen recorder changes. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ScreenCaptureEvent&gt; | 是 | Callback invoked when the event is triggered,where ScreenCaptureEvent indicates the new state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

**示例：**

```TypeScript
// 当系统录屏应用的录屏状态发生变化时通过此订阅事件上报。
screenCaptureMonitor.on('systemScreenRecorder', (event: media.ScreenCaptureEvent) => { 
  // 设置'systemScreenRecorder'事件回调。
  console.info(`system ScreenRecorder event: ${event}`);
})
```

## onSystemScreenRecorder

```TypeScript
onSystemScreenRecorder(callback: Callback<ScreenCaptureEvent>): void
```

Subscribes to state change events of the system screen recorder. From the ScreenCaptureEvent event reported, you can determine whether the system screen recorder is working. This event is triggered when the state of the system screen recorder changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ScreenCaptureMonitor-onSystemScreenRecorder(callback: Callback<ScreenCaptureEvent>): void--><!--Device-ScreenCaptureMonitor-onSystemScreenRecorder(callback: Callback<ScreenCaptureEvent>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ScreenCaptureEvent&gt; | 是 | Callback invoked when the event is triggered,where ScreenCaptureEvent indicates the new state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

## isSystemScreenRecorderWorking

```TypeScript
readonly isSystemScreenRecorderWorking: boolean
```

Whether the system screen recorder is working.

**类型：** boolean

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-ScreenCaptureMonitor-readonly isSystemScreenRecorderWorking: boolean--><!--Device-ScreenCaptureMonitor-readonly isSystemScreenRecorderWorking: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

