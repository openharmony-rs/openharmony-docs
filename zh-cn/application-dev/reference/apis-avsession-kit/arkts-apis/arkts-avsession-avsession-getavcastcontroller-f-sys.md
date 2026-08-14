# getAVCastController（系统接口）

## getAVCastController

```TypeScript
function getAVCastController(sessionId: string, callback: AsyncCallback<AVCastController>): void
```

设备建立连接后，获取投播控制器。结果通过callback异步回调方式返回。 此功能在本端和远端都可以使用，通过该接口可以获取一个相同的控制器，进行投播音频的播放控制。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function getAVCastController(sessionId: string, callback: AsyncCallback<AVCastController>): void--><!--Device-avSession-function getAVCastController(sessionId: string, callback: AsyncCallback<AVCastController>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 用于指定要获取的投播控制器的sessionId。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AVCastController](arkts-avsession-avsession-avcastcontroller-i.md)&gt; | 是 | 回调函数，返回投播控制器实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | session does not exist |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

## 示例

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
function getAVCastController(sessionId: string, callback: AsyncCallback<AVCastController | undefined>): void
```

Register a callback to retrieve an avsession cast controller. This function can be used at both side to get the same controller to do the playback control.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function getAVCastController(sessionId: string, callback: AsyncCallback<AVCastController | undefined>): void--><!--Device-avSession-function getAVCastController(sessionId: string, callback: AsyncCallback<AVCastController | undefined>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | Specifies the sessionId to get controller. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AVCastController](arkts-avsession-avsession-avcastcontroller-i.md) \| undefined&gt; | 是 | async callback for the AVCastController. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | session does not exist |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |


## getAVCastController

```TypeScript
function getAVCastController(sessionId: string): Promise<AVCastController>
```

设备建立连接后，获取投播控制器。结果通过Promise方式返回。 此功能在本端和远端都可以使用，通过该接口可以获取一个相同的控制器，进行投播音频的播放控制。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

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
| Promise&lt;[AVCastController](arkts-avsession-avsession-avcastcontroller-i.md)&gt; | Promise对象。返回投播控制器实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | server exception |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | session does not exist |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |


## getAVCastController

```TypeScript
function getAVCastController(sessionId: string): Promise<AVCastController | undefined>
```

Get the current session's remote controller client. If the avsession is not under casting state, the controller will return undefined.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function getAVCastController(sessionId: string): Promise<AVCastController | undefined>--><!--Device-avSession-function getAVCastController(sessionId: string): Promise<AVCastController | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | Specifies the sessionId to get controller. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVCastController](arkts-avsession-avsession-avcastcontroller-i.md) \| undefined&gt; | Promise for the AVCastController |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | server exception |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | session does not exist |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

