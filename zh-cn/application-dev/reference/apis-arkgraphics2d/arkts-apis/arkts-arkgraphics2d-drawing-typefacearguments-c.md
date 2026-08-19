# TypefaceArguments

提供字体属性配置的类，用于配置可变字体的属性参数（如字重维度等轴标签及对应属性值）。 > **说明：** > > - 本Class首批接口从API version 20开始支持。 > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 23

<!--Device-drawing-class TypefaceArguments--><!--Device-drawing-class TypefaceArguments-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## addVariation

```TypeScript
addVariation(axis: string, value: number)
```

给字体属性添加可变维度轴标签及对应的属性值。

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypefaceArguments-addVariation(axis: string, value: number)--><!--Device-TypefaceArguments-addVariation(axis: string, value: number)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| axis | string | 是 | 字体属性对象可变维度轴标签。具体支持哪些标签取决于加载的字体文件。具体支持的属性及标签值请参考对应的字体文件。 |
| value | number | 是 | 字体属性对象可变维度字重的标签'wght'对应的属性值，需要在字体文件支持的范围内，否则不会生效。 如果属性值小于支持的最小值，则默认和最小值一致。如果属性值大于支持的最大值，则默认和最大值效果一致。请打开对应的字体文件具体查看支持的属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## addVariation

```TypeScript
addVariation(axis: string, value: double) : void
```

给字体属性添加可变维度轴标签及对应的属性值。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-TypefaceArguments-addVariation(axis: string, value: double) : void--><!--Device-TypefaceArguments-addVariation(axis: string, value: double) : void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| axis | string | 是 | 字体属性对象可变维度轴标签。具体支持哪些标签取决于加载的字体文件。具体支持的属性及标签值请参考对应的字体文件。 |
| value | double | 是 | 字体属性对象可变维度字重的标签'wght'对应的属性值，需要在字体文件支持的范围内，否则不会生效。 如果属性值小于支持的最小值，则默认和最小值一致。如果属性值大于支持的最大值，则默认和最大值效果一致。请打开对应的字体文件具体查看支持的属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## constructor

```TypeScript
constructor()
```

字体属性的构造函数。

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypefaceArguments-constructor()--><!--Device-TypefaceArguments-constructor()-End-->

**系统能力：** SystemCapability.Graphics.Drawing

