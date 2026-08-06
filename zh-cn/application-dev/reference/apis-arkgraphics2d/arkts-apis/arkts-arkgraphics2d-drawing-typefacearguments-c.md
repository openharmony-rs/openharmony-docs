# TypefaceArguments

提供字体属性配置的结构体。 > **说明：** > > - 本Class首批接口从API version 20开始支持。 > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-drawing-class TypefaceArguments--><!--Device-drawing-class TypefaceArguments-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## addVariation

```TypeScript
addVariation(axis: string, value: number)
```

给字体属性设置字重值。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

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

## addVariation

```TypeScript
addVariation(axis: string, value: double) : void
```

Adds variation axis for the TypefaceArguments.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-TypefaceArguments-addVariation(axis: string, value: double) : void--><!--Device-TypefaceArguments-addVariation(axis: string, value: double) : void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| axis | string | 是 | Indicates the axis tag, which must contain four ASCII characters. |
| value | double | 是 | Indicates the value of the axis field. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## constructor

```TypeScript
constructor()
```

字体属性的构造函数。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TypefaceArguments-constructor()--><!--Device-TypefaceArguments-constructor()-End-->

**系统能力：** SystemCapability.Graphics.Drawing

