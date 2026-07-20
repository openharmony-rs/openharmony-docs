# isIsolatedProcess

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

<a id="isisolatedprocess"></a>
## isIsolatedProcess

```TypeScript
function isIsolatedProcess(): boolean
```

检查进程是否已被隔离。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-process-function isIsolatedProcess(): boolean--><!--Device-process-function isIsolatedProcess(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回判断结果。如果进程被隔离则返回 true；否则，返回 false。 |

**示例：**

```TypeScript
let result = process.isIsolatedProcess();

```

