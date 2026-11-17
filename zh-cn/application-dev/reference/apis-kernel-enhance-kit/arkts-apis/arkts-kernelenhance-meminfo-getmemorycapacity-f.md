# getMemoryCapacity

## 导入模块

```TypeScript
import { meminfo } from '@kit.KernelEnhanceKit';
```

## getMemoryCapacity

```TypeScript
function getMemoryCapacity(): number
```

获取系统总内存容量。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-meminfo-function getMemoryCapacity(): int--><!--Device-meminfo-function getMemoryCapacity(): int-End-->

**系统能力：** SystemCapability.Kernel.Memory

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 内存总容量，单位为MB。如果不存在，则返回0。 |
