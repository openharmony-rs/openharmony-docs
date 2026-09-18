# BreakIterator

Provides text line breaking capabilities, such as obtaining, moving, and identifying break points.

**Since:** 8

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## current

```TypeScript
current(): number
```

Obtains the position of the break iterator in the text.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| number | Position of the break iterator in the text. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let currentPos: number = iterator.current(); // currentPos = 0
```

## first

```TypeScript
first(): number
```

Moves the break iterator to the first line break point, which is always at the beginning of the processed text.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset of the first line break point in the processed text. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let firstPos: number = iterator.first(); // firstPos = 0
```

## following

```TypeScript
following(offset: number): number
```

Moves the line break iterator to the line break point after the specified position.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Offset of the line break point. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Position of the break iterator in the text after movement. The value **-1** is returned if the position of the break iterator is outside of the processed text after movement. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let pos: number = iterator.following(0); // pos = 6
pos = iterator.following(100); // pos = -1
pos = iterator.current(); // pos = 27
```

## getLineBreakText

```TypeScript
getLineBreakText(): string
```

Obtains the text processed by the **BreakIterator** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | Text being processed by the **BreakIterator** object. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let breakText: string = iterator.getLineBreakText(); // breakText = 'Apple is my favorite fruit.'
```

## isBoundary

```TypeScript
isBoundary(offset: number): boolean
```

Checks whether the specified position is a line break point.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Specified position in the text. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the specified position is a line break point. The value **true** indicates that the specified position is a line break point, and the value **false** indicates the opposite. If **true** is returned, the break iterator is moved to the position specified by **offset**. Otherwise, the break iterator is moved to the text line break point after the position specified by **offset**, which is equivalent to calling **following**. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let isBoundary: boolean = iterator.isBoundary(0); // isBoundary = true;
isBoundary = iterator.isBoundary(5); // isBoundary = false;
```

## last

```TypeScript
last(): number
```

Moves the break iterator to the last line break point, which is always the next position after the end of the processed text.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| number | Offset of the last line break point in the processed text. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let lastPos: number = iterator.last(); // lastPos = 27
```

## next

```TypeScript
next(index?: number): number
```

Moves the break iterator backward by the specified number of line break points.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | No | Number of line break points for moving the break iterator. The value is an integer. A positive number means to move the break iterator backward, and a negative number means to move the break iterator forward. The default value is **1**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Position of the break iterator in the text after movement. The value **-1** is returned if the position of the break iterator is outside of the processed text after movement. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let pos: number = iterator.first(); // pos = 0
pos = iterator.next(); // pos = 6
pos = iterator.next(10); // pos = -1
```

## previous

```TypeScript
previous(): number
```

Moves the break iterator foreward by one line break point.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| number | Position of the break iterator in the text after movement. The value **-1** is returned if the position of the break iterator is outside of the processed text after movement. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.');
let pos: number = iterator.first(); // pos = 0
pos = iterator.next(3); // pos = 12
pos = iterator.previous(); // pos = 9
```

## setLineBreakText

```TypeScript
setLineBreakText(text: string): void
```

Sets the text to be processed by the **BreakIterator** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Input text. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
iterator.setLineBreakText('Apple is my favorite fruit.'); // Set the text to be processed.
```
