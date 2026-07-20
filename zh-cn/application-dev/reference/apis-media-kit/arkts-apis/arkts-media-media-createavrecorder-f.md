# createAVRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

<a id="createavrecorder"></a>
## createAVRecorder

```TypeScript
function createAVRecorder(callback: AsyncCallback<AVRecorder>): void
```

创建音视频录制实例。使用callback异步回调。

> **说明：**  
>  
> 应用可创建多个音视频录制实例，但由于设备共用音频通路，一个设备仅能有一个实例进行音频录制。创建第二个实例录制音频时，将会因为音频通路冲突导致创建失败。

**起始版本：** 9

<!--Device-media-function createAVRecorder(callback: AsyncCallback<AVRecorder>): void--><!--Device-media-function createAVRecorder(callback: AsyncCallback<AVRecorder>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AVRecorder&gt; | 是 | 回调函数，返回AVRecorder实例，可用于录制音视频媒体。失败时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by callback. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let avRecorder: media.AVRecorder;

media.createAVRecorder((error: BusinessError, recorder: media.AVRecorder) => {
  if (recorder) {
    avRecorder = recorder;
    console.info('Succeeded in creating AVRecorder');
  } else {
    console.error(`Failed to create AVRecorder, error message:${error.message}`);
  }
});

```


<a id="createavrecorder-1"></a>
## createAVRecorder

```TypeScript
function createAVRecorder(): Promise<AVRecorder>
```

创建音视频录制实例。使用Promise异步回调。

> **说明：**  
>  
> 应用可创建多个音视频录制实例，但由于设备共用音频通路，一个设备仅能有一个实例进行音频录制。创建第二个实例录制音频时，将会因为音频通路冲突导致创建失败。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-media-function createAVRecorder(): Promise<AVRecorder>--><!--Device-media-function createAVRecorder(): Promise<AVRecorder>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AVRecorder&gt; | Promise对象，返回AVRecorder实例，可用于录制音视频媒体。失败时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let avRecorder: media.AVRecorder;
media.createAVRecorder().then((recorder: media.AVRecorder) => {
  if (recorder) {
    avRecorder = recorder;
    console.info('Succeeded in creating AVRecorder');
  } else {
    console.error('Failed to create AVRecorder');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create AVRecorder, error message:${error.message}`);
});

```

