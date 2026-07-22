# steps

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## steps

```TypeScript
function steps(count: number, end: boolean): string
```

构造阶梯曲线对象。
> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃。建议使用[Curves. stepsCurve](arkts-arkui-curves-stepscurve-f.md#stepscurve)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [stepsCurve](arkts-arkui-curves-stepscurve-f.md#stepscurve)

<!--Device-curves-function steps(count: number, end: boolean): string--><!--Device-curves-function steps(count: number, end: boolean): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | 阶梯的数量，需要为正整数。 |
| end | boolean | 是 | 在每个间隔的起点或是终点发生阶跃变化。<br>-true：在终点发生阶跃变化。<br>-false：在起点发生阶跃变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回阶梯曲线对象。 |

