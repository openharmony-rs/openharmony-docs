# off（系统接口）

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

## off

```TypeScript
function off(type: string): boolean
```

移除已注册的事件。

**起始版本：** 7

<!--Device-process-function off(type: string): boolean--><!--Device-process-function off(type: string): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要移除的已注册事件类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回移除结果。 |

