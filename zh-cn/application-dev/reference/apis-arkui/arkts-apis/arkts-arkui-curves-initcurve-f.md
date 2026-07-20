# initCurve

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

<a id="initcurve"></a>
## initCurve

```TypeScript
function initCurve(curve?: Curve): ICurve
```

插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-curves-function initCurve(curve?: Curve): ICurve--><!--Device-curves-function initCurve(curve?: Curve): ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| curve | [Curve](arkts-arkui-curve-e.md) | 否 | 曲线类型。<br/>默认值：Curve.Linear |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ICurve](../arkts-components/arkts-arkui-icurve-i.md) | 曲线的插值对象。 |

