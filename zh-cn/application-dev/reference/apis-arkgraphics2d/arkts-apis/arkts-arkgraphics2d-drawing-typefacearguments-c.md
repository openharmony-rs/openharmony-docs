# TypefaceArguments

提供字体属性配置的结构体。

> **说明：**  
>  
> - 本Class首批接口从API version 20开始支持。  
>  
> - 本模块使用屏幕物理像素单位px。  
>  
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 20

<!--Device-drawing-class TypefaceArguments--><!--Device-drawing-class TypefaceArguments-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

<a id="addvariation"></a>
## addVariation

```TypeScript
addVariation(axis: string, value: number)
```

给字体属性设置字重值。

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypefaceArguments-addVariation(axis: string, value: number)--><!--Device-TypefaceArguments-addVariation(axis: string, value: number)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| axis | string | 是 | Indicates the axis tag, which must contain four ASCII characters. |
| value | number | 是 | Indicates the value of the axis field. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

字体属性的构造函数。

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypefaceArguments-constructor()--><!--Device-TypefaceArguments-constructor()-End-->

**系统能力：** SystemCapability.Graphics.Drawing

