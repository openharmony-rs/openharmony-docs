# ScreenCaptureMonitor（系统接口）

```TypeScript
interface ScreenCaptureMonitor
```

录屏状态监控类，用于查询和监听系统录屏的录屏状态。在调用ScreenCaptureMonitor方法前，需要先通过[getScreenCaptureMonitor()](arkts-media-media-getscreencapturemonitor-f-sys.md)构建一个[ScreenCaptureMonitor](arkts-media-media-screencapturemonitor-i-sys.md)实例。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## off('systemScreenRecorder')

```TypeScript
off(type: 'systemScreenRecorder', callback?: Callback<ScreenCaptureEvent>): void
```

取消订阅系统录屏的录屏状态。使用callback异步回调。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'systemScreenRecorder' | 是 | 录屏状态回调类型'systemScreenRecorder'。<br>   - 'systemScreenRecorder'：系统录屏应用的录屏状态发生变化，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScreenCaptureEvent](arkts-media-media-screencaptureevent-e-sys.md)&gt; | 否 | 回调函数，返回系统录屏状态。[ScreenCaptureEvent](arkts-media-media-screencaptureevent-e-sys.md)表示切换到的状态，不填此参数则会取消最后一次订阅事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System App. |

**示例**

```TypeScript
screenCaptureMonitor.off('systemScreenRecorder');
```

## on('systemScreenRecorder')

```TypeScript
on(type: 'systemScreenRecorder', callback: Callback<ScreenCaptureEvent>): void
```

开始订阅系统录屏的录屏状态。当上报ScreenCaptureEvent事件后，用户可以根据ScreenCaptureEvent事件得知系统录屏当前处于开启还是停止的状态。使用callback异步回调。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'systemScreenRecorder' | 是 | 录屏状态回调类型'systemScreenRecorder'。<br>   - 'systemScreenRecorder'：系统录屏应用的录屏状态发生变化，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScreenCaptureEvent](arkts-media-media-screencaptureevent-e-sys.md)&gt; | 是 | 回调函数，返回系统录屏状态。[ScreenCaptureEvent](arkts-media-media-screencaptureevent-e-sys.md)表示切换到的状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System App. |

**示例**

```TypeScript
// 当系统录屏应用的录屏状态发生变化时通过此订阅事件上报。
screenCaptureMonitor.on('systemScreenRecorder', (event: media.ScreenCaptureEvent) => { 
  // 设置'systemScreenRecorder'事件回调。
  console.info(`system ScreenRecorder event: ${event}`);
})
```

## isSystemScreenRecorderWorking

```TypeScript
readonly isSystemScreenRecorderWorking: boolean
```

系统录屏是否处于录屏状态。true表示处于录屏状态；false表示不处于录屏状态。

**类型：** boolean

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。
