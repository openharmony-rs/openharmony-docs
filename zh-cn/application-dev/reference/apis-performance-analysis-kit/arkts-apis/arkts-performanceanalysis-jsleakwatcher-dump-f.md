# dump

## 导入模块

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## dump

```TypeScript
function dump(filePath: string): Array<string>
```

导出泄漏列表和虚拟机内存快照。

**起始版本：** 26.1.0

<!--Device-jsLeakWatcher-function dump(filePath: string): Array<string>--><!--Device-jsLeakWatcher-function dump(filePath: string): Array<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 导出信息生成的文件存放的路径。<br>**说明：**从API version 24开始，进程生命周期内，仅保留最新的一份快照信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 导出结果。分别为文件名后缀为.jsleaklist的泄漏列表和文件名后缀为.heapsnapshot虚拟机内存快照文件。 <br>**说明：**dump成功，返回泄漏列表文件路径和虚拟机内存快照路径；dump失败，返回空数组。 |

**示例**

```TypeScript
let context = this.getUIContext().getHostContext();
let files: Array<string> = jsLeakWatcher.dump(context?.filesDir);
```

