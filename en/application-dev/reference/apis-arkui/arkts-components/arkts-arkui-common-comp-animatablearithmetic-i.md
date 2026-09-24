# AnimatableArithmetic

```TypeScript
declare interface AnimatableArithmetic<T>
```

The **AnimatableArithmetic** API defines animation calculation rules for non-number data types. To animate non-number data (such as arrays, structs, and colors), you need to implement the addition, subtraction, multiplication, and equality checking functions in the **AnimatableArithmetic\&lt;T\&gt;** API. This enables the data to participate in animation interpolation calculations and to detect whether the data has changed. In other words, the non-number data is defined as types that implement the **AnimatableArithmetic\&lt;T\&gt;** API.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## equals

```TypeScript
equals(rhs: AnimatableArithmetic<T>): boolean
```

Defines the equality check rule for the data type.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rhs | [AnimatableArithmetic](arkts-arkui-common-comp-animatablearithmetic-i.md)&lt;T&gt; | Yes | Another data object to compare for equality with the current object. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the objects are equal. Returns **true** if they are equal; returns **false** otherwise. |

## multiply

```TypeScript
multiply(scale: number): AnimatableArithmetic<T>
```

Defines the multiplication rule for the data type.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number | Yes | Coefficient for the multiplication operation. |

**Return value:**

| Type | Description |
| --- | --- |
| [AnimatableArithmetic](arkts-arkui-common-comp-animatablearithmetic-i.md)&lt;T&gt; | Result of the multiplication operation. |

## plus

```TypeScript
plus(rhs: AnimatableArithmetic<T>): AnimatableArithmetic<T>
```

Defines the addition rule for the data type.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rhs | [AnimatableArithmetic](arkts-arkui-common-comp-animatablearithmetic-i.md)&lt;T&gt; | Yes | Object for the addition operation. |

**Return value:**

| Type | Description |
| --- | --- |
| [AnimatableArithmetic](arkts-arkui-common-comp-animatablearithmetic-i.md)&lt;T&gt; | Result of the addition operation. |

## subtract

```TypeScript
subtract(rhs: AnimatableArithmetic<T>): AnimatableArithmetic<T>
```

Defines the subtraction rule for the data type.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rhs | [AnimatableArithmetic](arkts-arkui-common-comp-animatablearithmetic-i.md)&lt;T&gt; | Yes | Object for the subtraction operation. |

**Return value:**

| Type | Description |
| --- | --- |
| [AnimatableArithmetic](arkts-arkui-common-comp-animatablearithmetic-i.md)&lt;T&gt; | Result of the subtraction operation. |
