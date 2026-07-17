# getPastCpuTime

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

## getPastCpuTime

```TypeScript
function getPastCpuTime(): number
```

获取进程启动到当前时间的 CPU 时间（以毫秒为单位）。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-process-function getPastCpuTime(): number--><!--Device-process-function getPastCpuTime(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回经过的 CPU 时间。单位：毫秒。 |

**示例：**

```TypeScript
let result = process.getPastCpuTime();

```

