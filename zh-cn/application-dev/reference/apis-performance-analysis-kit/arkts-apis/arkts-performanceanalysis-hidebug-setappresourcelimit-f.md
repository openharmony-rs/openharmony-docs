# setAppResourceLimit

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## setAppResourceLimit

```TypeScript
function setAppResourceLimit(type: string, value: int, enableDebugLog: boolean): void
```

设置应用的文件描述符数量、线程数量、JS内存或Native内存资源限制。 主要应用场景在于构造内存泄漏故障。 > **注意** > > 打开设置中的开发者选项后，在开发者选项列表中找到"系统资源泄漏日志"并启用，重启设备后接口生效。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-hidebug-function setAppResourceLimit(type: string, value: int, enableDebugLog: boolean): void--><!--Device-hidebug-function setAppResourceLimit(type: string, value: int, enableDebugLog: boolean): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 泄漏资源类型，共四种： - pss_memory（native内存） - js_heap（js堆内存） - fd（文件描述符） - thread（线程） |
| value | int | 是 | 对应泄漏资源类型的最大值，范围： - pss_memory类型：[1024, 4 1024 1024]（单位：KB） - js_heap类型：[85, 95]（分配给JS堆内存上限的85%~95%） - fd类型：[10, 10000] - thread类型：[1, 1000]。超出范围会导致功能失效。 |
| enableDebugLog | boolean | 是 | 是否启用外部调试日志。外部调试日志请仅在灰度版本（正式版本发布之前，先向一小部分用户推出的测试版本）中启用，因为收集调试日志会占用大量的cpu资源和内存资源，可能会引起应用流畅性问题。 true：启用外部调试日志。 false：禁用外部调试日志。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid argument, Possible causes: 1.The limit parameter is too small 2.The parameter is not in the specified type 3.The parameter type error or parameter order error |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | Set limit failed due to remote exception |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let type: string = 'js_heap';
let value: number = 85;
let enableDebugLog: boolean = false;
try {
  hidebug.setAppResourceLimit(type, value, enableDebugLog);
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}
```

