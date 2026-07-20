# AVCastController

在投播建立后，调用[avSession.getAVCastController](arkts-avsession-avsession-getavcastcontroller-f-sys.md#getavcastcontroller-1)后，返回会话控制器实例。控制器可查看会话ID，并可完成对会话发送命令及事件，获取会话元数据，播放状态信息等操作。

> **说明：**  
>  
> - 本Interface首批接口从API version 10开始支持。

**起始版本：** 10

<!--Device-avSession-interface AVCastController--><!--Device-avSession-interface AVCastController-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

<a id="setdisplaysurface"></a>
## setDisplaySurface

```TypeScript
setDisplaySurface(surfaceId: string, callback: AsyncCallback<void>): void
```

设置播放的surfaceId，在投播sink端使用。结果通过callback异步回调方式返回。

**起始版本：** 10

<!--Device-AVCastController-setDisplaySurface(surfaceId: string, callback: AsyncCallback<void>): void--><!--Device-AVCastController-setDisplaySurface(surfaceId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 设置播放的surfaceId。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，返回当前设置结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

**示例：**

```TypeScript
import { media } from '@kit.MediaKit';

let surfaceID: string = '';
media.createAVRecorder().then((avRecorder) => {
  avRecorder.getInputSurface((surfaceId: string) => {
    console.info('Succeeded in getting input surface.');
    surfaceID = surfaceId;
    if (surfaceID) {
      avCastController.setDisplaySurface(surfaceID, () => {
          console.info('Succeeded in setting display surface.');
      });
    }
  });
})

```

<a id="setdisplaysurface-1"></a>
## setDisplaySurface

```TypeScript
setDisplaySurface(surfaceId: string): Promise<void>
```

设置播放的surfaceId，在投播sink端使用。结果通过Promise异步回调方式返回。

**起始版本：** 10

<!--Device-AVCastController-setDisplaySurface(surfaceId: string): Promise<void>--><!--Device-AVCastController-setDisplaySurface(surfaceId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 设置播放的surfaceId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。返回设置结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

**示例：**

```TypeScript
import { media } from '@kit.MediaKit';

let surfaceID: string = '';
media.createAVRecorder().then((avRecorder) => {
  avRecorder.getInputSurface((surfaceId: string) => {
    console.info('Succeeded in getting input surface.');
    surfaceID = surfaceId;
    if (surfaceID) {
      avCastController.setDisplaySurface(surfaceID).then(() => {
        console.info('Succeeded in setting display surface.');
      });
    }
  });
})

```

