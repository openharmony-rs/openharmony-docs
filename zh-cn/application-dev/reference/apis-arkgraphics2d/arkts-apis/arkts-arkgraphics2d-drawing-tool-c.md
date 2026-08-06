# Tool

本模块定义的工具类，仅提供静态的方法，主要完成其他模块和[common2D]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中定义的数据结构的转换功能等操作。 > **说明：** > > - 本Class首批接口从API version 15开始支持。 > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-drawing-class Tool--><!--Device-drawing-class Tool-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## makeColorFromResourceColor

```TypeScript
static makeColorFromResourceColor(resourceColor: ResourceColor): common2D.Color
```

将ResourceColor类型的值转换为common2D.Color对象。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

<!--Device-Tool-static makeColorFromResourceColor(resourceColor: ResourceColor): common2D.Color--><!--Device-Tool-static makeColorFromResourceColor(resourceColor: ResourceColor): common2D.Color-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceColor | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | ResourceColor格式的颜色值（支持所有的4种输入，示例中提供13个示例输入）。其中第4种类型[Resource]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_只接受\_\_\_INLINE\_CODE\_USD\_0\_\_\_构造方法，需要确保该资源在main/resources/base/element目录下已定义(app支持color、string和integer，sys只支持color)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Color | **Common2D.Color** object. If the conversion fails, a null pointer is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## makeColorFromResourceColor

```TypeScript
static makeColorFromResourceColor(resourceColor: ResourceColor): common2D.Color | undefined
```

Converts a color value of the ResourceColor type to a common2D.Color object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Tool-static makeColorFromResourceColor(resourceColor: ResourceColor): common2D.Color | undefined--><!--Device-Tool-static makeColorFromResourceColor(resourceColor: ResourceColor): common2D.Color | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceColor | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Color value of the ResourceColor type.(All four types of inputs are supported. The following provides 13 example inputs.)The fourth type of Resource supports only the construction method \_\_\_ESCAPED\_DOLLAR\_\_\_r('belonging.type.name').Ensure that the resource has been defined in the main/resources/base/element directory.(The types color, string, and integer are available for the belonging app,whereas only the type color is available for the belonging sys.) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Color | Returns a 32-bit (ARGB) variable that describes the color. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

