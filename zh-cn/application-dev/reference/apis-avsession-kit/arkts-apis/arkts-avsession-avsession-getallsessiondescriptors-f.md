# getAllSessionDescriptors

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## getAllSessionDescriptors

```TypeScript
function getAllSessionDescriptors(): Promise<Array<Readonly<AVSessionDescriptor>>>
```

获取所有设置过媒体信息且注册过控制回调的会话的描述符信息。结果通过Promise异步回调方式返回。

**起始版本：** 23

**需要权限：** 
- API版本23+：ohos.permission.MANAGE_MEDIA_RESOURCES or ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC
- API版本9 - 22：ohos.permission.MANAGE_MEDIA_RESOURCES

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Readonly&lt;[AVSessionDescriptor](arkts-avsession-avsession-avsessiondescriptor-i.md)&gt;&gt;&gt; | Promise对象。返回所有会话描述的只读对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 9 - 22 |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

**示例**

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
                console.info(`Succeeded in getting session descriptor, isActive: ${descriptors[0].isActive}`);
                console.info(`Succeeded in getting session descriptor, type: ${descriptors[0].type}`);
                console.info(`Succeeded in getting session descriptor, sessionTag: ${descriptors[0].sessionTag}`);
              }
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}
```
