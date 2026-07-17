# offSystemCommonEvent（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## offSystemCommonEvent

```TypeScript
function offSystemCommonEvent(callback?: EventProcess): void
```

取消注册通用事件回调监听

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avSession-function offSystemCommonEvent(callback?: EventProcess): void--><!--Device-avSession-function offSystemCommonEvent(callback?: EventProcess): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | EventProcess | 否 | 处理事件回调 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

