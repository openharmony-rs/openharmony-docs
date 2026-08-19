# AttributeModifier

Defines the attribute modifier.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface AttributeModifier--><!--Device-unnamed-export declare interface AttributeModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## applyDisabledAttribute

```TypeScript
applyDisabledAttribute(instance: T) : void
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-AttributeModifier-applyDisabledAttribute(instance: T) : void--><!--Device-AttributeModifier-applyDisabledAttribute(instance: T) : void-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 |  |

## applyFocusedAttribute

```TypeScript
applyFocusedAttribute(instance: T) : void
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-AttributeModifier-applyFocusedAttribute(instance: T) : void--><!--Device-AttributeModifier-applyFocusedAttribute(instance: T) : void-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 |  |

## applyHoveredAttribute

```TypeScript
applyHoveredAttribute(instance: T) : void
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-AttributeModifier-applyHoveredAttribute(instance: T) : void--><!--Device-AttributeModifier-applyHoveredAttribute(instance: T) : void-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 |  |

## applyNormalAttribute

```TypeScript
applyNormalAttribute(instance: T) : void
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-AttributeModifier-applyNormalAttribute(instance: T) : void--><!--Device-AttributeModifier-applyNormalAttribute(instance: T) : void-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 |  |

## applyPressedAttribute

```TypeScript
applyPressedAttribute(instance: T) : void
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-AttributeModifier-applyPressedAttribute(instance: T) : void--><!--Device-AttributeModifier-applyPressedAttribute(instance: T) : void-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 |  |

## applySelectedAttribute

```TypeScript
applySelectedAttribute(instance: T) : void
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-AttributeModifier-applySelectedAttribute(instance: T) : void--><!--Device-AttributeModifier-applySelectedAttribute(instance: T) : void-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 |  |

## monitoredStates

```TypeScript
monitoredStates(): int
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-AttributeModifier-monitoredStates(): int--><!--Device-AttributeModifier-monitoredStates(): int-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int |  |

## default

```TypeScript
default
```

Specifies the states to be monitored. Override this method to specify which states (Normal, Pressed, Focused, Disabled, Selected) should be monitoredby returning a bitmask of ModifierState enum values.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AttributeModifier-default--><!--Device-AttributeModifier-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

