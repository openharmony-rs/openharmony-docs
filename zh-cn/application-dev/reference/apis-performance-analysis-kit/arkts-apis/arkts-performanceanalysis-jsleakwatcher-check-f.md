# check

## 导入模块

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## check

```TypeScript
function check(): string
```

获取已通过jsLeakWatcher.watch注册发生泄漏的对象列表，触发GC后未被回收的对象会被标记为泄漏。

**起始版本：** 26.1.0

<!--Device-jsLeakWatcher-function check(): string--><!--Device-jsLeakWatcher-function check(): string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 触发GC后未被回收的泄漏对象列表。 <br>**说明：**check成功，返回JSON格式的泄漏对象列表；check失败，返回空字符串。 |

**示例**

```TypeScript
let leakObjlist:string = jsLeakWatcher.check();
```

