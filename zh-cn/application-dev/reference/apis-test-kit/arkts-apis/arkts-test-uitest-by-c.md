# By

UiTest框架通过By类提供了丰富的控件特征描述API，用于进行控件筛选来匹配/查找出目标控件。 By提供的API能力具有以下几个特点： 1、支持单属性匹配和多属性组合匹配，例如同时指定目标控件text和id。 2、控件属性支持多种匹配模式。 3、支持控件绝对定位，相对定位，可通过[By.isBefore&lt;sup&gt;(deprecated)&lt;/sup&gt;](#isBefore)和 [By.isAfter&lt;sup&gt;(deprecated)&lt;/sup&gt;](#isAfter)等API限定邻近控件特征进行辅助定位。 By类提供的所有API均为同步接口，建议使用者通过静态构造器BY来链式创建By对象。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[On&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-on-c.md#On)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [On](arkts-test-uitest-on-c.md#On)

<!--Device-unnamed-declare class By--><!--Device-unnamed-declare class By-End-->

**系统能力：** SystemCapability.Test.UiTest

## clickable

```TypeScript
clickable(b?: boolean): By
```

指定目标控件的可点击状态属性，返回By对象自身。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[clickable&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-on-c.md#clickable)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [clickable](arkts-test-uitest-on-c.md#clickable)

<!--Device-By-clickable(b?: boolean): By--><!--Device-By-clickable(b?: boolean): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 指定控件可点击状态。true：可点击。false：不可点击。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | 返回指定目标控件的可点击状态属性的By对象。 |

## 示例

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.clickable(true); // 使用静态构造器BY创建by对象，指定目标控件的可点击状态属性。
```

## enabled

```TypeScript
enabled(b?: boolean): By
```

指定目标控件的使能状态属性，返回By对象自身。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[enabled&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-on-c.md#enabled)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [enabled](arkts-test-uitest-on-c.md#enabled)

<!--Device-By-enabled(b?: boolean): By--><!--Device-By-enabled(b?: boolean): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 指定控件使能状态。true：使能。false：未使能。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | 返回指定目标控件的使能状态属性的By对象。 |

## 示例

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.enabled(true); // 使用静态构造器BY创建by对象，指定目标控件的使能状态属性。
```

## focused

```TypeScript
focused(b?: boolean): By
```

指定目标控件的获焦状态属性，返回By对象自身。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[focused&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-on-c.md#focused)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [focused](arkts-test-uitest-on-c.md#focused)

<!--Device-By-focused(b?: boolean): By--><!--Device-By-focused(b?: boolean): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 控件获焦状态。true：获焦。false：未获焦。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | 返回指定目标控件的获焦状态属性的By对象。 |

## 示例

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.focused(true); // 使用静态构造器BY创建by对象，指定目标控件的获焦状态属性。
```

## id

```TypeScript
id(id: number): By
```

指定目标控件id属性，返回By对象自身。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[id&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-on-c.md#id)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [id](arkts-test-uitest-on-c.md#id)(id: string)

<!--Device-By-id(id: number): By--><!--Device-By-id(id: number): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 指定控件的id值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | 返回指定目标控件id属性的By对象。 |

## 示例

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.id(123); // 使用静态构造器BY创建by对象，指定目标控件的id属性。
```

## isAfter

```TypeScript
isAfter(by: By): By
```

指定目标控件位于给出的特征属性控件之后，返回By对象自身。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[isAfter&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-on-c.md#isAfter)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [isAfter](arkts-test-uitest-on-c.md#isAfter)(on: On)

<!--Device-By-isAfter(by: By): By--><!--Device-By-isAfter(by: By): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| by | [By](arkts-test-uitest-by-c.md) | 是 | 特征控件的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | 返回指定目标控件位于给出的特征属性控件之后的By对象。 |

## 示例

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

// 使用静态构造器BY创建by对象，指定目标控件位于给出的特征属性控件之后。
let by: By = BY.type('Text').isAfter(BY.text('123')); // 查找text为123之后的第一个Text组件。
```

## isBefore

```TypeScript
isBefore(by: By): By
```

指定目标控件位于给出的特征属性控件之前，返回By对象自身。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[isBefore&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-on-c.md#isBefore)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [isBefore](arkts-test-uitest-on-c.md#isBefore)(on: On)

<!--Device-By-isBefore(by: By): By--><!--Device-By-isBefore(by: By): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| by | [By](arkts-test-uitest-by-c.md) | 是 | 特征控件的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | 返回指定目标控件位于给出的特征属性控件之前的By对象。 |

## 示例

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

// 使用静态构造器BY创建by对象，指定目标控件位于给出的特征属性控件之前。
let by: By = BY.type('Button').isBefore(BY.text('123')); // 查找text为123之前的第一个Button组件。
```

## key

```TypeScript
key(key: string): By
```

指定目标控件key值属性，返回By对象自身。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[id&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-on-c.md#id)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [id](arkts-test-uitest-on-c.md#id)(id: string)

<!--Device-By-key(key: string): By--><!--Device-By-key(key: string): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 指定控件的Key值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | 返回指定目标控件key值属性的By对象。 |

## 示例

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.key('123'); // 使用静态构造器BY创建by对象，指定目标控件的key值属性。
```

## scrollable

```TypeScript
scrollable(b?: boolean): By
```

指定目标控件的可滑动状态属性，返回By对象自身。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[scrollable&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-on-c.md#scrollable)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [scrollable](arkts-test-uitest-on-c.md#scrollable)

<!--Device-By-scrollable(b?: boolean): By--><!--Device-By-scrollable(b?: boolean): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 控件可滑动状态。true：可滑动。false：不可滑动。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | 返回指定目标控件的可滑动状态属性的By对象。 |

## 示例

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.scrollable(true); // 使用静态构造器BY创建by对象，指定目标控件的可滑动状态属性。
```

## selected

```TypeScript
selected(b?: boolean): By
```

指定目标控件的被选中状态属性，返回By对象自身。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[selected&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-on-c.md#selected)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [selected](arkts-test-uitest-on-c.md#selected)

<!--Device-By-selected(b?: boolean): By--><!--Device-By-selected(b?: boolean): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 指定控件被选中状态。true：被选中。false：未被选中。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | 返回指定目标控件的被选中状态属性的By对象。 |

## 示例

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.selected(true); // 使用静态构造器BY创建by对象，指定目标控件的被选中状态属性。
```

## text

```TypeScript
text(txt: string, pattern?: MatchPattern): By
```

指定目标控件文本属性，支持多种匹配模式，返回By对象自身。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[text&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-on-c.md#text)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [text](arkts-test-uitest-on-c.md#text)

<!--Device-By-text(txt: string, pattern?: MatchPattern): By--><!--Device-By-text(txt: string, pattern?: MatchPattern): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| txt | string | 是 | 指定控件文本，用于匹配目标控件文本。 |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 否 | 指定的文本匹配模式，默认为[EQUALS](arkts-test-uitest-matchpattern-e.md#MatchPattern)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | 返回指定目标控件文本属性的By对象。 |

## 示例

```TypeScript
// xxx.test.ets
import { BY, By } from '@kit.TestKit';

let by: By = BY.text('123'); // 使用静态构造器BY创建by对象，指定目标控件的text属性。
```

## type

```TypeScript
type(tp: string): By
```

指定目标控件的控件类型属性，返回By对象自身。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用[type&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-on-c.md#type)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [type](arkts-test-uitest-on-c.md#type)(tp: string)

<!--Device-By-type(tp: string): By--><!--Device-By-type(tp: string): By-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tp | string | 是 | 指定控件类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | 返回指定目标控件的控件类型属性的By对象。 |

## 示例

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.type('Button'); // 使用静态构造器BY创建by对象，指定目标控件的控件类型属性。
```

