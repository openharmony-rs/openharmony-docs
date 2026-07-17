# createController（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## createController

```TypeScript
function createController(sessionId: string, callback: AsyncCallback<AVSessionController>): void
```

根据会话ID创建会话控制器。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function createController(sessionId: string, callback: AsyncCallback<AVSessionController>): void--><!--Device-avSession-function createController(sessionId: string, callback: AsyncCallback<AVSessionController>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 会话ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AVSessionController> | 是 | 回调函数。返回会话控制器实例，可查看会话ID，<br>并完成对会话发送命令及事件，获取元数据、播放状态信息等操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |

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
          .onClick(()=>{
            avSession.getAllSessionDescriptors().then((descriptors: avSession.AVSessionDescriptor[]) => {
              console.info(`Succeeded in getting all session descriptors, length: ${descriptors.length}`);
              if (descriptors.length > 0 ) {
avSession.createController(descriptors[0]?.sessionId, (avcontroller: avSession.AVSessionController) => { 
                    console.info('Succeeded in creating controller.'); 
                });
              }
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}

```


## createController

```TypeScript
function createController(sessionId: string): Promise<AVSessionController>
```

根据会话ID创建会话控制器。使用Promise异步回调。

**起始版本：** 23

**需要权限：** 
- API版本23+：ohos.permission.MANAGE_MEDIA_RESOURCES or ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC
- API版本9 - 22：ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function createController(sessionId: string): Promise<AVSessionController>--><!--Device-avSession-function createController(sessionId: string): Promise<AVSessionController>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 会话ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<AVSessionController> | Promise对象。返回会话控制器实例，可查看会话ID，<br>并完成对会话发送命令及事件，获取元数据、播放状态信息等操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 9 - 22 |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |

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
          .onClick(()=>{
            avSession.getAllSessionDescriptors().then((descriptors: avSession.AVSessionDescriptor[]) => {
              console.info(`Succeeded in getting all session descriptors, length: ${descriptors.length}`);
              if (descriptors.length > 0 ) {
                avSession.createController(descriptors[0]?.sessionId).then((avcontroller: avSession.AVSessionController) => {
                  console.info('Succeeded in creating controller.');
                });
              }
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}

```

