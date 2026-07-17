# on（系统接口）

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

## on

```TypeScript
function on(type: string, listener: EventListener): void
```

注册事件。

**起始版本：** 7

<!--Device-process-function on(type: string, listener: EventListener): void--><!--Device-process-function on(type: string, listener: EventListener): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 表示注册的事件类型。 |
| listener | [EventListener](arkts-arkts-process-eventlistener-t.md) | 是 | 表示注册的事件函数。 |

