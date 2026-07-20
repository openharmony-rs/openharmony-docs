# offActiveSessionChanged（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

<a id="offactivesessionchanged"></a>
## offActiveSessionChanged

```TypeScript
function offActiveSessionChanged(callback?: Callback<Array<AVSessionDescriptor>>): void
```

取消允许在系统控制入口显示的会话变更事件监听，取消后将不再对该事件进行监听。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function offActiveSessionChanged(callback?: Callback<Array<AVSessionDescriptor>>): void--><!--Device-avSession-function offActiveSessionChanged(callback?: Callback<Array<AVSessionDescriptor>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Array&lt;AVSessionDescriptor&gt;&gt; | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有允许在系统控制入口显示的会话变更事件监听。 |

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
          avSession.onActiveSessionChanged((descriptors: Array<avSession.AVSessionDescriptor>) => {
          });
          avSession.offActiveSessionChanged();
        })
    }
    .width('100%')
    .height('100%')
  }
}

```

