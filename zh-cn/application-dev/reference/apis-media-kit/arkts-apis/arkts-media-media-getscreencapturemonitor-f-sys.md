# getScreenCaptureMonitor（系统接口）

## getScreenCaptureMonitor

```TypeScript
function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor>
```

Obtains a **ScreenCaptureMonitor** instance. This API uses a promise to return the result.

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-media-function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor>--><!--Device-media-function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ScreenCaptureMonitor](arkts-media-multimedia-media-screencapturemonitor-i-sys.md)&gt; | Promise used to return the result. The instance can be used to query and monitor the status of the system screen recorder. &lt;br&gt;If the operation is successful, a **ScreenCaptureMonitor** instance is returned; otherwise, **null** is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

## 示例

```TypeScript
let screenCaptureMonitor: media.ScreenCaptureMonitor;
try {
  screenCaptureMonitor = await media.getScreenCaptureMonitor();
} catch (err) {
  console.error(`getScreenCaptureMonitor failed, error message:${err.message}`);
}
```


## getScreenCaptureMonitor

```TypeScript
function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor | undefined>
```

Obtains a **ScreenCaptureMonitor** instance. This API uses a promise to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-media-function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor | undefined>--><!--Device-media-function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ScreenCaptureMonitor](arkts-media-multimedia-media-screencapturemonitor-i-sys.md) \| undefined&gt; | Promise used to return the result. The instance can be used to query and monitor the status of the system screen recorder. &lt;br&gt;If the operation is successful, a **ScreenCaptureMonitor** instance is returned; otherwise, **null** is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

