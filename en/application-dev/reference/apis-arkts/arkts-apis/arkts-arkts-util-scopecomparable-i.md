# ScopeComparable

The values of the **ScopeComparable** type are used to implement the **compareTo** method. Therefore, ensure that the input parameters are comparable.

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## compareTo

```TypeScript
compareTo(other: ScopeComparable): boolean
```

Compares two values and returns a Boolean value.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| other | [ScopeComparable](arkts-arkts-util-scopecomparable-i.md) | Yes | The other value to be compared with the current value. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the current value is greater than or equal to the input value; otherwise, **false** is returned. |

**Examples**

```TypeScript
Create a class to implement the compareTo method. The Temperature class is used as an example in the following sample code.
```
