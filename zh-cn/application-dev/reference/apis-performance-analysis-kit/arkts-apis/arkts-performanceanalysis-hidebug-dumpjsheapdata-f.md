# dumpJsHeapData

## 导入模块

```TypeScript
```

## dumpJsHeapData

```TypeScript
function dumpJsHeapData(filename : string) : void
```

虚拟机堆数据转储。

> **注意**：
> 
> 由于虚拟机堆导出极其耗时，且该接口为同步接口，建议不要在上架版本中调用该接口，以避免应用冻屏，影响用户体验。

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | 用户自定义的虚拟机堆数据转储输出的文件名，将在应用的`files`目录下生成以该参数命名的heapsnapshot文件。string长度的最大值为128字节。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | the parameter check failed, Parameter type error |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  hidebug.dumpJsHeapData("heapData");
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}
```


## dumpJsHeapData

```TypeScript
function dumpJsHeapData(filename : string, needClean : boolean) : void
```

虚拟机堆数据转储，支持清除nodeId缓存。

> **注意**：
> 
> 由于虚拟机堆导出极其耗时，且该接口为同步接口，建议不要在上架版本中调用该接口，以避免应用冻屏，影响用户体验。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | 用户自定义的虚拟机堆转储文件名，将在应用的files目录下生成fileName.heapsnapshot格式文件。string长度的最大值为128字节。 |
| needClean | boolean | 是 | 转储堆快照前是否需要清除nodeId缓存。true：需要清除；false：不需要清除。 |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  hidebug.dumpJsHeapData("heapData", true);
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}
```
