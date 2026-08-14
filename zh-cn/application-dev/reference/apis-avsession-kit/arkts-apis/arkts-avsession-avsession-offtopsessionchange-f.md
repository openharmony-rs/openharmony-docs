# offTopSessionChange

## offTopSessionChange

```TypeScript
function offTopSessionChange(callback?: Callback<AVSessionDescriptor>): void
```

Unregister top session changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC

<!--Device-avSession-function offTopSessionChange(callback?: Callback<AVSessionDescriptor>): void--><!--Device-avSession-function offTopSessionChange(callback?: Callback<AVSessionDescriptor>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AVSessionDescriptor](arkts-avsession-avsession-avsessiondescriptor-i-sys.md)&gt; | 否 | Top会话变化回调函数 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |

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
          .onClick(()=>{
            avSession.offTopSessionChange((descriptor: avSession.AVSessionDescriptor) => {
            });
            avSession.offTopSessionChange();
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

```TypeScript
avSession.offTopSessionChange();
```

