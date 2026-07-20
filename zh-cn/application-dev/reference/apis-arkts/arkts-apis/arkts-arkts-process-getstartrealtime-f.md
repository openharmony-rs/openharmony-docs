# getStartRealtime

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

<a id="getstartrealtime"></a>
## getStartRealtime

```TypeScript
function getStartRealtime(): number
```

获取系统启动到进程启动的实时时间（以毫秒为单位，不包含系统休眠时间）。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-process-function getStartRealtime(): number--><!--Device-process-function getStartRealtime(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回经过的实时时间。单位：毫秒。 |

**示例：**

```TypeScript
let realtime = process.getStartRealtime();

```

