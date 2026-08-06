# MeasureText

定义了测算方法类。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare class MeasureText--><!--Device-unnamed-declare class MeasureText-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## measureText

```TypeScript
static measureText(options: MeasureOptions): double
```

计算指定文本作为单行文本显示时的宽度。如果文本包含多行（由换行符\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_分隔），则返回其中最长的行的宽度。 > **说明：** > > -measureText需要先通过\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_方法获取 > \_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_对象，然后通过该对象进行调用。 > > - 直接使用MeasureText可能导致\_\_\_MD\_LINK\_DESC\_USD\_4\_\_\_的问题，推荐通过 > \_\_\_MD\_LINK\_DESC\_USD\_5\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_6\_\_\_方法获取当前UI上下文关 > 联的\_\_\_MD\_LINK\_DESC\_USD\_7\_\_\_实例。 > > - measureText接口的计算结果始终是单行文本的宽度，入参options中配置的布局约束（如constraintWidth、maxLines）对measureText的结果没有影响。如果需要计算布局约束下的宽度，请使用 > \_\_\_MD\_LINK\_DESC\_USD\_8\_\_\_方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureText-static measureText(options: MeasureOptions): double--><!--Device-MeasureText-static measureText(options: MeasureOptions): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 被计算文本描述信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 文本宽度。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_单位：px |

## measureTextSize

```TypeScript
static measureTextSize(options: MeasureOptions): SizeOptions
```

计算指定文本的宽度和高度。 > **说明：** > > -measureTextSize需要先通过\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_方法获取 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_对象，然后通过该对象进行调用。 > > - 直接使用MeasureText可能导致\_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_的问题，推荐通过 > \_\_\_MD\_LINK\_DESC\_USD\_4\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_5\_\_\_方法获取当前UI上下文关 > 联的\_\_\_MD\_LINK\_DESC\_USD\_6\_\_\_实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureText-static measureTextSize(options: MeasureOptions): SizeOptions--><!--Device-MeasureText-static measureTextSize(options: MeasureOptions): SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 被计算文本描述信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回文本所占布局宽度和高度。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：** \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_文本宽度以及高度返回值单位均为px。 |

