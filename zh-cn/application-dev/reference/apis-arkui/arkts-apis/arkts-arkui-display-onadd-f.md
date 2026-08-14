# onAdd

## onAdd

```TypeScript
function onAdd(callback: Callback<long>): void
```

Register the callback for display add events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-display-function onAdd(callback: Callback<long>): void--><!--Device-display-function onAdd(callback: Callback<long>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;long&gt; | 是 | the display id of changed |

## 示例

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<long> = (data: long) => {
  console.info(`Listening enabled. Data: ${data}`);
};

display.onAdd(callback);
```

