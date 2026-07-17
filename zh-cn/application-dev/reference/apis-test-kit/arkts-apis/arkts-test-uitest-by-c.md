# By

UiTest框架通过By类提供了丰富的控件特征描述API，用于进行控件筛选来匹配/查找出目标控件。

By提供的API能力具有以下几个特点:

1、支持单属性匹配和多属性组合匹配，例如同时指定目标控件text和id。

2、控件属性支持多种匹配模式。

3、支持控件绝对定位，相对定位，可通过[By.isBefore<sup>(deprecated)</sup>](arkts-test-uitest-by-c.md#isbefore-1)和[By.isAfter<sup>(deprecated)</sup>](arkts-test-uitest-by-c.md#isafter-1)等API限定邻近控件特征进行辅助定位。

By类提供的所有API均为同步接口，建议使用者通过静态构造器BY来链式创建By对象。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[On<sup>9+</sup>](arkts-test-uitest-on-c.md)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [On](arkts-test-uitest-on-c.md)

<!--Device-unnamed-declare class By--><!--Device-unnamed-declare class By-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { ResizeDirection, WindowMode, PenMode, PenKeyOperation, Driver, MatchPattern, UiDirection, TouchOptions, ComponentEventType, PointerMatrix, WindowChangeType, Component, ON, PenKey, Rect, InputTextMode, UIEventObserver, WindowFilter, WindowChangeOptions, UiWindow, TouchPadSwipeOptions, Point, KeyOptions, DisplayRotation, UIElementInfo, PenKeyOperationOptions, ComponentEventOptions, MouseButton, On } from '@kit.TestKit';
```

## clickable

```TypeScript
clickable(b?: boolean): By
```

指定目标控件的可点击状态属性，返回By对象自身。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[clickable<sup>9+</sup>](arkts-test-uitest-on-c.md#clickable-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [clickable](arkts-test-uitest-on-c.md#clickable-1)

<!--Device-By-clickable(b?: boolean): By--><!--Device-By-clickable(b?: boolean): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 指定控件可点击状态。true：可点击。false：不可点击。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | - 返回指定目标控件的可点击状态属性的By对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.clickable(true); // 使用静态构造器BY创建By对象，指定目标控件的可点击状态属性。

```

## enabled

```TypeScript
enabled(b?: boolean): By
```

指定目标控件的使能状态属性，返回By对象自身。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[enabled<sup>9+</sup>](arkts-test-uitest-on-c.md#enabled-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [enabled](arkts-test-uitest-on-c.md#enabled-1)

<!--Device-By-enabled(b?: boolean): By--><!--Device-By-enabled(b?: boolean): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 指定控件使能状态。true：使能。false：未使能。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | - 返回指定目标控件的使能状态属性的By对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.enabled(true); // 使用静态构造器BY创建By对象，指定目标控件的使能状态属性。

```

## focused

```TypeScript
focused(b?: boolean): By
```

指定目标控件的获焦状态属性，返回By对象自身。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[focused<sup>9+</sup>](arkts-test-uitest-on-c.md#focused-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [focused](arkts-test-uitest-on-c.md#focused-1)

<!--Device-By-focused(b?: boolean): By--><!--Device-By-focused(b?: boolean): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 控件获焦状态。true：获焦。false：未获焦。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | - 返回指定目标控件的获焦状态属性的By对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.focused(true); // 使用静态构造器BY创建By对象，指定目标控件的获焦状态属性。

```

## id

```TypeScript
id(id: number): By
```

指定目标控件id属性，返回By对象自身。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[id<sup>9+</sup>](arkts-test-uitest-on-c.md#id-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** id(id:

<!--Device-By-id(id: number): By--><!--Device-By-id(id: number): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 指定控件的id值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | - 返回指定目标控件id属性的By对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.id(123); // 使用静态构造器BY创建By对象，指定目标控件的id属性。

```

## isAfter

```TypeScript
isAfter(by: By): By
```

指定目标控件位于给出的特征属性控件之后，返回By对象自身。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[isAfter<sup>9+</sup>](arkts-test-uitest-on-c.md#isafter-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isAfter(on:

<!--Device-By-isAfter(by: By): By--><!--Device-By-isAfter(by: By): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| by | [By](arkts-test-uitest-by-c.md) | 是 | 特征控件的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | - 返回指定目标控件位于给出的特征属性控件之后的By对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

// 使用静态构造器BY创建By对象，指定目标控件位于给出的特征属性控件之后。
let by: By = BY.type('Text').isAfter(BY.text('123')); // 查找 text为123之后的第一个Text组件

```

## isBefore

```TypeScript
isBefore(by: By): By
```

指定目标控件位于给出的特征属性控件之前，返回By对象自身。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[isBefore<sup>9+</sup>](arkts-test-uitest-on-c.md#isbefore-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isBefore(on:

<!--Device-By-isBefore(by: By): By--><!--Device-By-isBefore(by: By): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| by | [By](arkts-test-uitest-by-c.md) | 是 | 特征控件的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | - 返回指定目标控件位于给出的特征属性控件之前的By对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

// 使用静态构造器BY创建By对象，指定目标控件位于给出的特征属性控件之前。
let by: By = BY.type('Button').isBefore(BY.text('123')); // 查找text为123之前的第一个Button组件

```

## key

```TypeScript
key(key: string): By
```

指定目标控件key值属性，返回By对象自身。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[id<sup>9+</sup>](arkts-test-uitest-on-c.md#id-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** id(id:

<!--Device-By-key(key: string): By--><!--Device-By-key(key: string): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 指定控件的Key值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | - 返回指定目标控件key值属性的By对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.key('123'); // 使用静态构造器BY创建By对象，指定目标控件的key值属性。

```

## scrollable

```TypeScript
scrollable(b?: boolean): By
```

指定目标控件的可滑动状态属性，返回By对象自身。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[scrollable<sup>9+</sup>](arkts-test-uitest-on-c.md#scrollable-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [scrollable](arkts-test-uitest-on-c.md#scrollable-1)

<!--Device-By-scrollable(b?: boolean): By--><!--Device-By-scrollable(b?: boolean): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 控件可滑动状态。true：可滑动。false：不可滑动。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | - 返回指定目标控件的可滑动状态属性的By对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.scrollable(true); // 使用静态构造器BY创建By对象，指定目标控件的可滑动状态属性。

```

## selected

```TypeScript
selected(b?: boolean): By
```

指定目标控件的被选中状态属性，返回By对象自身。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[selected<sup>9+</sup>](arkts-test-uitest-on-c.md#selected-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [selected](arkts-test-uitest-on-c.md#selected-1)

<!--Device-By-selected(b?: boolean): By--><!--Device-By-selected(b?: boolean): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 指定控件被选中状态。true：被选中。false：未被选中。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | - 返回指定目标控件的被选中状态属性的By对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.selected(true); // 使用静态构造器BY创建By对象，指定目标控件的被选中状态属性。

```

## text

```TypeScript
text(txt: string, pattern?: MatchPattern): By
```

指定目标控件文本属性，支持多种匹配模式，返回By对象自身。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[text<sup>9+</sup>](arkts-test-uitest-on-c.md#text-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [text](arkts-test-uitest-on-c.md#text-1)

<!--Device-By-text(txt: string, pattern?: MatchPattern): By--><!--Device-By-text(txt: string, pattern?: MatchPattern): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| txt | string | 是 | 指定控件文本，用于匹配目标控件文本。 |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 否 | 指定的文本匹配模式，默认为[EQUALS](arkts-test-uitest-matchpattern-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | - 返回指定目标控件文本属性的By对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { BY, By } from '@kit.TestKit';

let by: By = BY.text('123'); // 使用静态构造器BY创建By对象，指定目标控件的text属性。

```

## type

```TypeScript
type(tp: string): By
```

指定目标控件的控件类型属性，返回By对象自身。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[type<sup>9+</sup>](arkts-test-uitest-on-c.md#type-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** type(tp:

<!--Device-By-type(tp: string): By--><!--Device-By-type(tp: string): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tp | string | 是 | 指定控件类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | - 返回指定目标控件的控件类型属性的By对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.type('Button'); // 使用静态构造器BY创建By对象，指定目标控件的控件类型属性。

```

