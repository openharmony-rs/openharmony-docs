# stepsCurve

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## stepsCurve

```TypeScript
function stepsCurve(count: number, end: boolean): ICurve
```

构造阶梯曲线对象，将动画过程划分为若干等距间隔，在每个间隔的起点或终点发生阶跃变化。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | 阶梯的数量，需要为正整数。<br>取值范围：[1, +∞) <br>**说明：** <br>设置小于1的值时，按值为1处理；传入非整数时，向下取整处理。 |
| end | boolean | 是 | 在每个间隔的起点或终点发生阶跃变化。<br>-true：在终点发生阶跃变化。<br>-false：在起点发生阶跃变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | 曲线的插值对象，可通过其interpolate方法获取指定归一化时间点的曲线插值。 |

**示例**

```TypeScript
import { curves } from '@kit.ArkUI';
curves.stepsCurve(9, true);  // 创建一个阶梯曲线
```
