# By

The UiTest framework provides a wide range of UI component feature description APIs in the **By** class to filter and match components.

The APIs provided by the **By** class exhibit the following features:

1. Allow one or more attributes as the match conditions.
For example, you can specify both the **text** and **id** attributes to find the target component.
2. Provide multiple match patterns for component attributes.
3. Support absolute positioning and relative positioning for components.
APIs such as [By.isBefore&lt;sup&gt;(deprecated)&lt;/sup&gt;](#isbefore) and [By.isAfter&lt;sup&gt;(deprecated)&lt;/sup&gt;](#isafter) can be used to specify the features of adjacent components to assist positioning.

All APIs provided in the **By** class are synchronous. You are advised to use the static constructor **BY** to create a **By** object in chain mode.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [On](arkts-test-uitest-on-c.md)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## clickable

```TypeScript
clickable(b?: boolean): By
```

Specifies the clickable attribute of the target component.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [clickable](arkts-test-uitest-on-c.md#clickable)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| b | boolean | No | Clickable status of the component. The value **true** indicates that the component is clickable, and **false** indicates the opposite. Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | **By** object that matches the clickable attribute of the target component. |

**Examples**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.clickable(true); // Use the static constructor BY to create a By object and specify the clickable attribute of the target component.
```

## enabled

```TypeScript
enabled(b?: boolean): By
```

Specifies the enabled attribute of the target component.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [enabled](arkts-test-uitest-on-c.md#enabled)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| b | boolean | No | Enabled status of the component. The value **true** indicates that the component is enabled, and **false** indicates the opposite. Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | **By** object that matches the enabled attribute of the target component. |

**Examples**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.enabled(true); // Use the static constructor BY to create a By object and specify the enabled attribute of the target component.
```

## focused

```TypeScript
focused(b?: boolean): By
```

Specifies the focused attribute of the target component.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [focused](arkts-test-uitest-on-c.md#focused)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| b | boolean | No | Focused status of the component. The value **true** indicates that the component is focused, and **false** indicates the opposite. Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | **By** object that matches the focused attribute of the target component. |

**Examples**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.focused(true); // Use the static constructor BY to create a By object and specify the focused attribute of the target component.
```

## id

```TypeScript
id(id: number): By
```

Specifies the ID attribute of the target component.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [id](arkts-test-uitest-on-c.md#id)(id: string)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Component ID. |

**Return value:**

| Type | Description |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | **By** object that matches the ID attribute of the target component. |

**Examples**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.id(123); // Use the static constructor BY to create a By object and specify the id attribute of the target component.
```

## isAfter

```TypeScript
isAfter(by: By): By
```

Specifies that the target component is located after the given attribute component.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isAfter](arkts-test-uitest-on-c.md#isafter)(on: On)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| by | [By](arkts-test-uitest-by-c.md) | Yes | Information about the attribute component. |

**Return value:**

| Type | Description |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | **By** object. |

**Examples**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

// Use the static constructor BY to create a by object and specify that the target component is located before the given attribute component.
let by: By = BY.type('Text').isAfter(BY.text('123')); // Search for the first Text component located after the component whose text is 123.
```

## isBefore

```TypeScript
isBefore(by: By): By
```

Specifies that the target component is located before the given attribute component.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isBefore](arkts-test-uitest-on-c.md#isbefore)(on: On)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| by | [By](arkts-test-uitest-by-c.md) | Yes | Information about the attribute component. |

**Return value:**

| Type | Description |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | **By** object. |

**Examples**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

// Use the static constructor BY to create a by object and specify that the target component is located before the given attribute component.
let by: By = BY.type('Button').isBefore(BY.text('123')); // Search for the first Button component located before the component whose text is 123.
```

## key

```TypeScript
key(key: string): By
```

Specifies the key attribute of the target component.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [id](arkts-test-uitest-on-c.md#id)(id: string)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Component key. |

**Return value:**

| Type | Description |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | **By** object that matches the key attribute of the target component. |

**Examples**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.key('123'); // Use the static constructor BY to create a By object and specify the key attribute of the target component.
```

## scrollable

```TypeScript
scrollable(b?: boolean): By
```

Specifies the scrollable attribute of the target component.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [scrollable](arkts-test-uitest-on-c.md#scrollable)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| b | boolean | No | Whether the specified component is scrollable. The value **true** indicates that the component is scrollable, and **false** indicates the opposite. Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | **By** object that matches the scrollable attribute of the target component. |

**Examples**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.scrollable(true); // Use the static constructor BY to create a By object and specify the scrollable attribute of the target component.
```

## selected

```TypeScript
selected(b?: boolean): By
```

Specifies the selected status of the target component.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [selected](arkts-test-uitest-on-c.md#selected)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| b | boolean | No | Selected status of the component. The value **true** indicates that the component is selected, and **false** indicates the opposite. Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | **By** object that matches the selected attribute of the target component. |

**Examples**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.selected(true); // Use the static constructor BY to create a By object and specify the selected attribute of the target component.
```

## text

```TypeScript
text(txt: string, pattern?: MatchPattern): By
```

Specifies the text attribute of the target component. Multiple match patterns are supported.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [text](arkts-test-uitest-on-c.md#text)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| txt | string | Yes | Component text, used to match the target component. |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | No | Match pattern [MatchPattern](arkts-test-uitest-matchpattern-e.md). <br>Default value: [EQUALS](arkts-test-uitest-matchpattern-e.md#equals) |

**Return value:**

| Type | Description |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | **By** object that matches the text attribute of the target component. |

**Examples**

```TypeScript
// xxx.test.ets
import { BY, By } from '@kit.TestKit';

let by: By = BY.text('123'); // Use the static constructor BY to create a By object and specify the text attribute of the target component.
```

## type

```TypeScript
type(tp: string): By
```

Specifies the type attribute of the target component.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [type](arkts-test-uitest-on-c.md#type)(tp: string)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tp | string | Yes | Component type. |

**Return value:**

| Type | Description |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | **By** object that matches the type attribute of the target component. |

**Examples**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.type('Button'); // Use the static constructor BY to create a By object and specify the type attribute of the target component.
```
