# offSessionDestroy

## offSessionDestroy

```TypeScript
function offSessionDestroy(callback?: Callback<AVSessionDescriptor>): void
```

Unregister session destroy callback

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC

<!--Device-avSession-function offSessionDestroy(callback?: Callback<AVSessionDescriptor>): void--><!--Device-avSession-function offSessionDestroy(callback?: Callback<AVSessionDescriptor>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVSessionDescriptor&gt; | 否 | 会话销毁回调函数 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
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
          .onClick(()=>{
            avSession.onSessionDestroy((descriptor: avSession.AVSessionDescriptor) => {
            });
            avSession.offSessionDestroy();
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

```TypeScript
avSession.offSessionDestroy();
```

