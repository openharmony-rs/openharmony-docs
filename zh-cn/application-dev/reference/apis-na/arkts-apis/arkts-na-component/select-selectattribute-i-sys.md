# SelectAttribute

除支持[通用属性]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_外，还支持以下属性：

**继承/实现关系：** SelectAttribute extends [CommonMethod](common-commonmethod-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SelectAttribute extends CommonMethod--><!--Device-unnamed-export declare interface SelectAttribute extends CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuDistortionMode

```TypeScript
default menuDistortionMode(mode: DistortionMode | undefined): this
```

Sets the distortion animation mode of the select with the new material.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectAttribute-default menuDistortionMode(mode: DistortionMode | undefined): this--><!--Device-SelectAttribute-default menuDistortionMode(mode: DistortionMode | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Animation mode. The default value is DistortionMode.DISTORTION\_\_\_ESCAPED\_UNDERSCORE\_\_\_AUTO. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | - the attribute of the select. |

## menuEdgeLightMode

```TypeScript
default menuEdgeLightMode(mode: EdgeLightMode | undefined): this
```

Sets the edgelight animation mode of the select with the new material.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectAttribute-default menuEdgeLightMode(mode: EdgeLightMode | undefined): this--><!--Device-SelectAttribute-default menuEdgeLightMode(mode: EdgeLightMode | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Animation mode.The default value is EdgeLightMode.EDGELIGHT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DISABLED. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | - the attribute of the select. |

## menuSystemMaterial

```TypeScript
default menuSystemMaterial(material: SystemUiMaterial | undefined): this
```

Set system-styled materials for select's menu. Different materials have different effects, which can influence the backgroundColor, border, shadow, and other visual attributes of select's menu. Device Behavior Differences:The effect of the same material may vary across different devices depending on their computing power.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectAttribute-default menuSystemMaterial(material: SystemUiMaterial | undefined): this--><!--Device-SelectAttribute-default menuSystemMaterial(material: SystemUiMaterial | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| material | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | The select's menu material, undefined means retaining the original visual style of the select's menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | - The attribute of the select. |

