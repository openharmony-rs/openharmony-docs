# initCurve

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## initCurve

```TypeScript
export function initCurve(curve?: Curve): ICurve
```

插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-curves-export function initCurve(curve?: Curve): ICurve--><!--Device-curves-export function initCurve(curve?: Curve): ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| curve | Curve | 否 | 曲线类型。<br/>默认值：Curve.Linear |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ICurve | 曲线的插值对象。 |

