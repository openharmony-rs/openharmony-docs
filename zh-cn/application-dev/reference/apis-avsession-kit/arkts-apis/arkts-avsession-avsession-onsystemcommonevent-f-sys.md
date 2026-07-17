# onSystemCommonEvent（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## onSystemCommonEvent

```TypeScript
function onSystemCommonEvent(callback: EventProcess): void
```

监听系统通用事件命令回调

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avSession-function onSystemCommonEvent(callback: EventProcess): void--><!--Device-avSession-function onSystemCommonEvent(callback: EventProcess): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | EventProcess | 是 | 监听通用事件命令回调 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

