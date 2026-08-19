# onChange

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## onChange

```TypeScript
function onChange(callback: Callback<long>): void
```

Register the callback for display changes.

**起始版本：** 23

<!--Device-display-function onChange(callback: Callback<long>): void--><!--Device-display-function onChange(callback: Callback<long>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;long&gt; | 是 | the display id of changed |

**示例**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<long> = (data: long) => {
  console.info(`Listening enabled. Data: ${data}`);
};

display.onChange(callback);
```

