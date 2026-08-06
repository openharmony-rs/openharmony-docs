# AttributeModifier

Defines the attribute modifier.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface AttributeModifier<T>--><!--Device-unnamed-export declare interface AttributeModifier<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## applyDisabledAttribute

```TypeScript
default applyDisabledAttribute(instance: T) : void
```

Defines the disabled update attribute function.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AttributeModifier-default applyDisabledAttribute(instance: T) : void--><!--Device-AttributeModifier-default applyDisabledAttribute(instance: T) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 |  |

## applyFocusedAttribute

```TypeScript
default applyFocusedAttribute(instance: T) : void
```

Defines the focused update attribute function.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AttributeModifier-default applyFocusedAttribute(instance: T) : void--><!--Device-AttributeModifier-default applyFocusedAttribute(instance: T) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 |  |

## applyHoveredAttribute

```TypeScript
default applyHoveredAttribute(instance: T) : void
```

Defines the function that updates the hovered attribute.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AttributeModifier-default applyHoveredAttribute(instance: T) : void--><!--Device-AttributeModifier-default applyHoveredAttribute(instance: T) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 |  |

## applyNormalAttribute

```TypeScript
default applyNormalAttribute(instance: T) : void
```

Defines the normal update attribute function.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AttributeModifier-default applyNormalAttribute(instance: T) : void--><!--Device-AttributeModifier-default applyNormalAttribute(instance: T) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 |  |

## applyPressedAttribute

```TypeScript
default applyPressedAttribute(instance: T) : void
```

Defines the pressed update attribute function.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AttributeModifier-default applyPressedAttribute(instance: T) : void--><!--Device-AttributeModifier-default applyPressedAttribute(instance: T) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 |  |

## applySelectedAttribute

```TypeScript
default applySelectedAttribute(instance: T) : void
```

Defines the selected update attribute function.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AttributeModifier-default applySelectedAttribute(instance: T) : void--><!--Device-AttributeModifier-default applySelectedAttribute(instance: T) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 |  |

## monitoredStates

```TypeScript
default monitoredStates(): int
```

Specifies the states to be monitored. Override this method to specify which states (Normal, Pressed, Focused, Disabled, Selected) should be monitoredby returning a bitmask of ModifierState enum values.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AttributeModifier-default monitoredStates(): int--><!--Device-AttributeModifier-default monitoredStates(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | - Bitmask combination of states to be monitored |

