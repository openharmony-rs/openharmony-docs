# getAVSession

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

<a id="getavsession"></a>
## getAVSession

```TypeScript
function getAVSession(context: Context): Promise<AVSession>
```

获取会话对象。使用Promise异步回调。

该接口可将当前进程已创建过的会话对象返回，如果没有创建过会话对象，该接口调用会失败并抛出异常。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-avSession-function getAVSession(context: Context): Promise<AVSession>--><!--Device-avSession-function getAVSession(context: Context): Promise<AVSession>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 需要使用UIAbilityContext，用于系统获取应用组件的相关信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AVSession&gt; | Promise对象。回调返回会话实例对象，可用于获取会话ID、设置元数据及播放状态、发送按键事件等操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |

**示例：**

```TypeScript
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  private avsessioncontroller !: avSession.AVSessionController;
  @State message: string = 'hello world';

  build() {
    Column() {
        Text(this.message)
          .onClick(()=>{
            let currentAVSession: avSession.AVSession;
            let context: Context = this.getUIContext().getHostContext() as Context;
            let sessionId: string;  // 供后续函数入参使用。
            let sessionTag: string;

            avSession.getAVSession(context).then(async (data: avSession.AVSession) => {
              currentAVSession = data;
              sessionId = currentAVSession.sessionId;
              sessionTag = currentAVSession.sessionTag;
              console.info(`Succeeded in getting AV session, sessionId: ${sessionId}, sessionTag: ${sessionTag}`);
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}

```

