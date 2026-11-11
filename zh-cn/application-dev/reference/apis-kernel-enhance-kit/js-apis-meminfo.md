# @ohos.meminfo (内存硬件信息)

<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @wl92-->
<!--Designer: @wl92-->
<!--Tester: @lianxuanself-->
<!--Adviser: @fang-jinxu-->

提供内存硬件信息查询能力，包括内存总容量、内存频率等。适用于需要获取设备内存硬件规格的场景，例如设备信息展示。

## 导入模块

```ts
import { meminfo } from '@kit.KernelEnhanceKit';
```

## meminfo.getMemoryCapacity

getMemoryCapacity(): int

获取系统内存总容量。

**起始版本**：26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Kernel.Memory

**返回值**：

| 类型 | 说明                                   |
| ---- | -------------------------------------- |
| int  | 内存总容量，单位为MB。如果不存在，则返回0。 |

**示例**：

```ts
import { meminfo } from '@kit.KernelEnhanceKit';

let memoryCapacity: int = meminfo.getMemoryCapacity();
console.info(`memoryCapacity = ${memoryCapacity} MB`);
```

## meminfo.getMemoryFrequency

getMemoryFrequency(): int

获取内存频率。

**起始版本**：26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Kernel.Memory

**返回值**：

| 类型 | 说明                                 |
| ---- | ------------------------------------ |
| int  | 内存频率，单位为MHz。如果不存在，则返回0。 |

**示例**：

```ts
import { meminfo } from '@kit.KernelEnhanceKit';

let memoryFrequency: int = meminfo.getMemoryFrequency();
console.info(`memoryFrequency = ${memoryFrequency} MHz`);
```
