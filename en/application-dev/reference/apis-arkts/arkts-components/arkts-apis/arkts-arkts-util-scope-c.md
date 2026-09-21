# Scope

```TypeScript
class Scope
```

The Scope interface is used to describe the valid range of a field.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [ScopeHelper](arkts-arkts-util-scopehelper-c.md)

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## clamp

```TypeScript
clamp(value: ScopeType): ScopeType
```

Limits a value to this **Scope**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [clamp](arkts-arkts-util-scopehelper-c.md#clamp)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ScopeType](arkts-arkts-util-scopetype-t.md) | Yes | Value specified. |

**Return value:**

| Type | Description |
| --- | --- |
| [ScopeType](arkts-arkts-util-scopetype-t.md) | Returns **lowerObj** if the specified value is less than the lower limit; returns **upperObj** if the specified value is greater than the upper limit; returns the specified value if it is within this **Scope**. |

**Examples**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let tempMiDF = new Temperature(35);
let range = new util.Scope(tempLower, tempUpper);
let result = range.clamp(tempMiDF);
console.info("result = " + result);
// Output: result = 35
```

## constructor

```TypeScript
constructor(lowerObj: ScopeType, upperObj: ScopeType)
```

A constructor used to create a **Scope** object with the specified upper and lower limits.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** constructor

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lowerObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | Yes | Lower limit of the **Scope** object. |
| upperObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | Yes | Upper limit of the **Scope** object. |

**Examples**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let range = new util.Scope(tempLower, tempUpper);
console.info("range = " + range);
// Output: range = [30, 40]
```

## contains

```TypeScript
contains(value: ScopeType): boolean
```

Checks whether a value is within this **Scope**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [contains](arkts-arkts-util-lrucache-c.md#contains)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ScopeType](arkts-arkts-util-scopetype-t.md) | Yes | Value specified. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is within this **Scope**; otherwise, **false** is returned. |

**Examples**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let tempMiDF = new Temperature(35);
let range = new util.Scope(tempLower, tempUpper);
let result = range.contains(tempMiDF);
console.info("result = " + result);
// Output: result = true
```

<a id="contains-1"></a>

## contains

```TypeScript
contains(range: Scope): boolean
```

Checks whether a range is within this **Scope**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [contains](arkts-arkts-util-lrucache-c.md#contains)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [Scope](arkts-arkts-util-scope-c.md) | Yes | **Scope** specified. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the range is within this **Scope**; otherwise, **false** is returned. |

**Examples**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let range = new util.Scope(tempLower, tempUpper);
let tempLess = new Temperature(20);
let tempMore = new Temperature(45);
let rangeSec = new util.Scope(tempLess, tempMore);
let result = range.contains(rangeSec);
console.info("result = " + result);
// Output: result = false
```

## expand

```TypeScript
expand(lowerObj: ScopeType, upperObj: ScopeType): Scope
```

Obtains the union set of this **Scope** and the given lower and upper limits.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** expand

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lowerObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | Yes | Lower limit. |
| upperObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | Yes | Upper limit. |

**Return value:**

| Type | Description |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | Union set of this **Scope** and the given lower and upper limits. |

**Examples**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let tempMiDF = new Temperature(35);
let tempMidS = new Temperature(39);
let range = new util.Scope(tempLower, tempUpper);
let result = range.expand(tempMiDF, tempMidS);
console.info("result = " + result);
// Output: result = [30, 40]
```

<a id="expand-1"></a>

## expand

```TypeScript
expand(range: Scope): Scope
```

Obtains the union set of this **Scope** and the given **Scope**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** expand

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [Scope](arkts-arkts-util-scope-c.md) | Yes | **Scope** specified. |

**Return value:**

| Type | Description |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | Union set of this **Scope** and the given **Scope**. |

**Examples**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let tempMiDF = new Temperature(35);
let tempMidS = new Temperature(39);
let range = new util.Scope(tempLower, tempUpper);
let rangeFir = new util.Scope(tempMiDF, tempMidS);
let result = range.expand(rangeFir);
console.info("result = " + result);
// Output: result = [30, 40]
```

<a id="expand-2"></a>

## expand

```TypeScript
expand(value: ScopeType): Scope
```

Obtains the union set of this **Scope** and the given value.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** expand

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ScopeType](arkts-arkts-util-scopetype-t.md) | Yes | Value specified. |

**Return value:**

| Type | Description |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | Union set of this **Scope** and the given value. |

**Examples**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let tempMiDF = new Temperature(35);
let range = new util.Scope(tempLower, tempUpper);
let result = range.expand(tempMiDF);
console.info("result = " + result);
// Output: result = [30, 40]
```

## getLower

```TypeScript
getLower(): ScopeType
```

Obtains the lower limit of this **Scope**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getLower](arkts-arkts-util-scopehelper-c.md#getlower)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [ScopeType](arkts-arkts-util-scopetype-t.md) | Lower limit of this **Scope**. |

**Examples**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let range = new util.Scope(tempLower, tempUpper);
let result = range.getLower();
console.info("result = " + result);
// Output: result = 30
```

## getUpper

```TypeScript
getUpper(): ScopeType
```

Obtains the upper limit of this **Scope**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getUpper](arkts-arkts-util-scopehelper-c.md#getupper)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [ScopeType](arkts-arkts-util-scopetype-t.md) | Upper limit of this **Scope**. |

**Examples**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let range = new util.Scope(tempLower, tempUpper);
let result = range.getUpper();
console.info("result = " + result);
// Output: result = 40
```

## intersect

```TypeScript
intersect(range: Scope): Scope
```

Obtains the intersection of this **Scope** and the given **Scope**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** intersect

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [Scope](arkts-arkts-util-scope-c.md) | Yes | **Scope** specified. |

**Return value:**

| Type | Description |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | Intersection of this **Scope** and the given **Scope**. |

**Examples**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let range = new util.Scope(tempLower, tempUpper);
let tempMiDF = new Temperature(35);
let tempMidS = new Temperature(39);
let rangeFir = new util.Scope(tempMiDF, tempMidS);
let result = range.intersect(rangeFir );
console.info("result = " + result);
  // Output: result = [35, 39]
```

<a id="intersect-1"></a>

## intersect

```TypeScript
intersect(lowerObj: ScopeType, upperObj: ScopeType): Scope
```

Obtains the intersection of this **Scope** and the given lower and upper limits.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** intersect

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lowerObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | Yes | Lower limit. |
| upperObj | [ScopeType](arkts-arkts-util-scopetype-t.md) | Yes | Upper limit. |

**Return value:**

| Type | Description |
| --- | --- |
| [Scope](arkts-arkts-util-scope-c.md) | Intersection of this **Scope** and the given lower and upper limits. |

**Examples**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let tempMiDF = new Temperature(35);
let tempMidS = new Temperature(39);
let range = new util.Scope(tempLower, tempUpper);
let result = range.intersect(tempMiDF, tempMidS);
console.info("result = " + result);
// Output: result = [35, 39]
```

## toString

```TypeScript
toString(): string
```

Obtains a string representation that contains this **Scope**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [toString](arkts-arkts-util-lrucache-c.md#tostring)

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | String representation containing the **Scope**. |

**Examples**

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

let tempLower = new Temperature(30);
let tempUpper = new Temperature(40);
let range = new util.Scope(tempLower, tempUpper);
let result = range.toString();
console.info("result = " + result);
// Output: result = [30, 40]
```
