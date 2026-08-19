# on_sessionDestroy（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## on('sessionDestroy')

```TypeScript
function on(type: 'sessionDestroy', callback: (session: AVSessionDescriptor) => void): void
```

会话的销毁事件监听。使用callback异步回调。

**起始版本：** 9

<!--Device-avSession-function on(type: 'sessionDestroy', callback: (session: AVSessionDescriptor) => void): void--><!--Device-avSession-function on(type: 'sessionDestroy', callback: (session: AVSessionDescriptor) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionDestroy' | 是 | 事件回调类型，支持的事件是`'sessionDestroy'`：会话销毁事件，检测到会话销毁时触发。 |
| callback | (session: AVSessionDescriptor) =&gt; void | 是 | 回调函数。参数为会话相关描述。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

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
            avSession.on('topSessionChange', (descriptor: avSession.AVSessionDescriptor) => {
              console.info(`on topSessionChange : isActive : ${descriptor.isActive}`);
              console.info(`on topSessionChange : type : ${descriptor.type}`);
              console.info(`on topSessionChange : sessionTag : ${descriptor.sessionTag}`);
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

