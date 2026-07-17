# getAVCastController（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## getAVCastController

```TypeScript
function getAVCastController(sessionId: string, callback: AsyncCallback<AVCastController>): void
```

设备建立连接后，获取投播控制器。结果通过callback异步回调方式返回。

此功能在本端和远端都可以使用，通过该接口可以获取一个相同的控制器，进行投播音频的播放控制。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function getAVCastController(sessionId: string, callback: AsyncCallback<AVCastController>): void--><!--Device-avSession-function getAVCastController(sessionId: string, callback: AsyncCallback<AVCastController>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 用于指定要获取的投播控制器的sessionId。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AVCastController> | 是 | 回调函数，返回投播控制器实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | session does not exist |

**示例：**

```TypeScript
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context = this.getUIContext().getHostContext() as Context;
          let sessionId: string = ""; // 供后续函数入参使用。

          let avCastController: avSession.AVCastController;
          avSession.getAVCastController(sessionId, (avcontroller: avSession.AVCastController) => {
              avCastController = avcontroller;
              console.info('Succeeded in getting AV cast controller.');
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}

```


## getAVCastController

```TypeScript
function getAVCastController(sessionId: string): Promise<AVCastController>
```

设备建立连接后，获取投播控制器。结果通过Promise方式返回。

此功能在本端和远端都可以使用，通过该接口可以获取一个相同的控制器，进行投播音频的播放控制。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function getAVCastController(sessionId: string): Promise<AVCastController>--><!--Device-avSession-function getAVCastController(sessionId: string): Promise<AVCastController>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 用于指定要获取的投播控制器的sessionId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<AVCastController> | Promise对象。返回投播控制器实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | server exception |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | session does not exist |

**示例：**

```TypeScript
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context = this.getUIContext().getHostContext() as Context;
          let sessionId: string = ""; // 供后续函数入参使用。

          let avCastController: avSession.AVCastController;
          avSession.getAVCastController(sessionId).then((avcontroller: avSession.AVCastController) => {
            avCastController = avcontroller;
            console.info('Succeeded in getting AV cast controller.');
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}

```

