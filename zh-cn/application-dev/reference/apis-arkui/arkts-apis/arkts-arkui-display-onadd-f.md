# onAdd

## onAdd

```TypeScript
function onAdd(callback: Callback<long>): void
```

Register the callback for display add events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-display-function onAdd(callback: Callback<long>): void--><!--Device-display-function onAdd(callback: Callback<long>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;long&gt; | 是 | the display id of changed |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<long> = (data: long) => {
  console.info(`Listening enabled. Data: ${data}`);
};

display.onAdd(callback);
```

