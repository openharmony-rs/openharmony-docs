# stopProfiler

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## stopProfiler

```TypeScript
function stopProfiler(): Promise<void>
```

停止已经启动的Profiler。

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-hidebug-function stopProfiler(): Promise<void>--><!--Device-hidebug-function stopProfiler(): Promise<void>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 11400422 | Failed to stop resource profiling because it is not started. |
| 11400430 | Other profiling errors. |
