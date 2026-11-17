# getMemoryFrequency

## 导入模块

```TypeScript
import { meminfo } from '@kit.KernelEnhanceKit';
```

## getMemoryFrequency

```TypeScript
function getMemoryFrequency(): number
```

获取内存频率。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-meminfo-function getMemoryFrequency(): int--><!--Device-meminfo-function getMemoryFrequency(): int-End-->

**系统能力：** SystemCapability.Kernel.Memory

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 内存频率，单位为MHz。如果不存在，则返回0。 |
