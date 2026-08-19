# onUnhandledRejection

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## onUnhandledRejection

```TypeScript
function onUnhandledRejection(observer: UnhandledRejectionObserver): void
```

Register unhandled rejection observer.

**起始版本：** 24

<!--Device-errorManager-function onUnhandledRejection(observer: UnhandledRejectionObserver): void--><!--Device-errorManager-function onUnhandledRejection(observer: UnhandledRejectionObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [UnhandledRejectionObserver](arkts-ability-errormanager-unhandledrejectionobserver-t.md) | 是 | 注册被拒绝promise监听器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：1. 必填参数未填写； 2. 参数类型不正确；3. 参数校验失败。 |

