# onActiveSessionChanged（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## onActiveSessionChanged

```TypeScript
function onActiveSessionChanged(callback: Callback<Array<AVSessionDescriptor>>): void
```

允许在系统控制入口显示的会话变更的监听事件。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function onActiveSessionChanged(callback: Callback<Array<AVSessionDescriptor>>): void--><!--Device-avSession-function onActiveSessionChanged(callback: Callback<Array<AVSessionDescriptor>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<Array<AVSessionDescriptor>> | 是 | 回调函数。参数为允许在系统控制入口显示的会话信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

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
          avSession.onActiveSessionChanged((descs: Array<avSession.AVSessionDescriptor>) => {
            descs.forEach((desc, index) => {
              console.info(`=== 会话 ${index + 1}/${descs.length} ===`);
              console.info(`on onActiveSessionChanged : isActive : ${desc.isActive}`);
              console.info(`on onActiveSessionChanged : type : ${desc.type}`);
              console.info(`on onActiveSessionChanged : sessionTag : ${desc.sessionTag}`);
            });
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}

```

