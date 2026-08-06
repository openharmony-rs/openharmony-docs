# getScreenCaptureMonitor（系统接口）

## getScreenCaptureMonitor

```TypeScript
function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor>
```

Obtains a **ScreenCaptureMonitor** instance. This API uses a promise to return the result.

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-media-function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor>--><!--Device-media-function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ScreenCaptureMonitor&gt; | Promise used to return the result. The instance can be used to query |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

**示例：**

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-media-function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor | undefined>--><!--Device-media-function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ScreenCaptureMonitor \| undefined&gt; | Promise used to return the result. The instance can be used |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

