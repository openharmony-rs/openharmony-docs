# init

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

<a id="init"></a>
## init

```TypeScript
function init(curve?: Curve): string
```

插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃。建议使用[Curves.initCurve](arkts-arkui-curves-initcurve-f.md#initcurve-1)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [initCurve](arkts-arkui-curves-initcurve-f.md#initcurve-1)

<!--Device-curves-function init(curve?: Curve): string--><!--Device-curves-function init(curve?: Curve): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| curve | [Curve](arkts-arkui-curve-e.md) | 否 | 曲线类型。<br/>默认值：Curve.Linear |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回插值曲线对象。 |

