# isDebugState

## isDebugState

```TypeScript
function isDebugState(): boolean
```

获取应用进程的调试状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hidebug-function isDebugState(): boolean--><!--Device-hidebug-function isDebugState(): boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 应用进程的Ark层或Native层是否处于调试状态。true：处于调试状态。false：未处于调试状态。 |

## 示例

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

console.info(`isDebugState = ${hidebug.isDebugState()}`)
```

