# SamplingOptions

采样选项对象。

> **说明：**  
>  
> - 本Class首批接口从API version 12开始支持。  
>  
> - 本模块使用屏幕物理像素单位px。  
>  
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 12

<!--Device-drawing-class SamplingOptions--><!--Device-drawing-class SamplingOptions-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

构造一个新的采样选项对象，[FilterMode](arkts-arkgraphics2d-drawing-filtermode-e.md)的默认值为FILTER_MODE_NEAREST。

**起始版本：** 12

<!--Device-SamplingOptions-constructor()--><!--Device-SamplingOptions-constructor()-End-->

**系统能力：** SystemCapability.Graphics.Drawing

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(filterMode: FilterMode)
```

构造一个新的采样选项对象。

**起始版本：** 12

<!--Device-SamplingOptions-constructor(filterMode: FilterMode)--><!--Device-SamplingOptions-constructor(filterMode: FilterMode)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filterMode | [FilterMode](arkts-arkgraphics2d-drawing-filtermode-e.md) | 是 | 过滤模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

