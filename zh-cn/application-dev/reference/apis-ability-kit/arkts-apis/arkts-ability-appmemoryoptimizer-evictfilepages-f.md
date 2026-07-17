# evictFilePages

## 导入模块

```TypeScript
import { appMemoryOptimizer } from '@kit.AbilityKit';
```

## evictFilePages

```TypeScript
function evictFilePages(fileNames: Array<string>): Promise<void>
```

向系统发出释放指定文件的文件页缓存请求，系统会根据当前内存状况决定是否真正执行释放，不保证一定释放成功。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-appMemoryOptimizer-function evictFilePages(fileNames: Array<string>): Promise<void>--><!--Device-appMemoryOptimizer-function evictFilePages(fileNames: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileNames | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 需要释放文件页缓存的文件名数组，文件名必须以.so、.hap 或.hsp结尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000163](../errorcode-ability.md#16000163-文件类型错误) | 文件类型错误。文件名未以.so、.hap或.hsp结尾。 |

