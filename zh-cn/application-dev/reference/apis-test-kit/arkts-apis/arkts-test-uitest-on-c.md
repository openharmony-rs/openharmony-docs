# On

UiTest框架从API version 9开始，通过On类提供了丰富的控件特征描述API，用于进行控件筛选来匹配/查找出目标控件。On提供的API能力具有以下几个特点：1、支持单属性匹配和多属性组合匹配，例如同时指定目标控件text和id。2、控件属性支持多种匹配模式。3、支持控件绝对定位，相对定位，可通过[ON.isBefore](#isbefore)和[ON.isAfter](#isafter)等API限定邻近控件特征进行辅助定位。On类提供的所有API均为同步接口，建议使用者通过静态构造器ON来链式创建On对象。

**起始版本：** 9

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## afterComponent

```TypeScript
afterComponent(com: Component): On
```

指定目标控件位于给出的特征控件（参数 [Component](arkts-test-uitest-component-c.md)）之后，返回 On 对象自身。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| com | [Component](arkts-test-uitest-component-c.md) | 是 | 特征控件，目标控件须位于该控件之后。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件位于给出的特征控件之后的 On 对象. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000007](../errorcode-uitest.md#17000007-参数不合法) | Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, On, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let component: Component = await driver.findComponent(ON.type('Text'));
  let on: On = ON.text('123').afterComponent(component); // 查找第一个Text组件之后的text为123的组件。
}
```

## beforeComponent

```TypeScript
beforeComponent(com: Component): On
```

指定目标控件位于给出的特征控件（参数 [Component](arkts-test-uitest-component-c.md)）之前，返回 On 对象自身。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| com | [Component](arkts-test-uitest-component-c.md) | 是 | 特征控件，目标控件须位于该控件之前。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件位于给出的特征控件之前的 On 对象. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000007](../errorcode-uitest.md#17000007-参数不合法) | Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, On, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let component: Component = await driver.findComponent(ON.type('Text'));
  let on: On = ON.text('123').beforeComponent(component); // 查找第一个Text组件之前的text为123的组件。
}
```

## belongingDisplay

```TypeScript
belongingDisplay(displayId: number): On
```

指定目标控件所属的屏幕，返回On对象自身。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 指定控件所属屏幕ID，取值范围：大于等于0的整数。 **说明：** 传入displayId不存在时，将抛出17000007异常。可通过 [getAllDisplays](../../apis-arkui/arkts-apis/arkts-arkui-display-getalldisplays-f.md)获取当前所有的 display对象，并由display对象获取对应的屏幕ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定控件所属屏幕的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000007](../errorcode-uitest.md#17000007-参数不合法) | Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.belongingDisplay(0); // 使用静态构造器ON创建On对象，指定目标控件所属屏幕ID。
```

## checkable

```TypeScript
checkable(b?: boolean): On
```

指定目标控件能否被勾选状态属性，返回On对象自身。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 指定控件能否被勾选状态。true：能被勾选。false：不能被勾选。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件能否被勾选状态属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.checkable(true); // 使用静态构造器ON创建On对象，指定目标控件的能否被勾选状态属性。
```

## checked

```TypeScript
checked(b?: boolean): On
```

指定目标控件的被勾选状态属性，返回On对象自身。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 指定控件被勾选状态。true：被勾选。false：未被勾选。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件的被勾选状态属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.checked(true); // 使用静态构造器ON创建On对象，指定目标控件的被勾选状态属性。
```

## clickable

```TypeScript
clickable(b?: boolean): On
```

指定目标控件的可点击状态属性，返回On对象自身。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 指定控件可点击状态。true：可点击。false：不可点击。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件的可点击状态属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.clickable(true); // 使用静态构造器ON创建On对象，指定目标控件的可点击状态属性。
```

## description

```TypeScript
description(val: string, pattern?: MatchPattern): On
```

指定目标控件的描述属性，支持多种匹配模式，返回On对象自身。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | string | 是 | 控件的描述属性。 |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 否 | 指定的文本匹配模式，默认为[EQUALS](arkts-test-uitest-matchpattern-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件description属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.description('123'); // 使用静态构造器ON创建On对象，指定目标控件的description属性。
```

## enabled

```TypeScript
enabled(b?: boolean): On
```

指定目标控件的使能状态属性，返回On对象自身。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 指定控件使能状态。true：使能。false：未使能。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件的使能状态属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.enabled(true); // 使用静态构造器ON创建On对象，指定目标控件的使能状态属性。
```

## focused

```TypeScript
focused(b?: boolean): On
```

指定目标控件的获焦状态属性，返回On对象自身。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 控件获焦状态。true：获焦。false：未获焦。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件的获焦状态属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.focused(true); // 使用静态构造器ON创建On对象，指定目标控件的获焦状态属性。
```

## hint

```TypeScript
hint(val: string, pattern?: MatchPattern): On
```

指定目标控件的提示文本属性，返回On对象自身。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | string | 是 | 指定控件提示文本。 |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 否 | 指定的文本匹配模式，默认为[EQUALS](arkts-test-uitest-matchpattern-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件hint属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { MatchPattern, On, ON } from '@kit.TestKit';

let on: On = ON.hint('welcome', MatchPattern.EQUALS); // 使用静态构造器ON创建On对象，指定目标控件的提示文本属性。
```

## id

```TypeScript
id(id: string): On
```

指定目标控件id属性，返回On对象自身。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 指定控件的id值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件id属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.id('123'); // 使用静态构造器ON创建On对象，指定目标控件的id属性。
```

## id

```TypeScript
id(id: string, pattern: MatchPattern): On
```

指定目标控件id属性和匹配模式，返回On对象自身。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 指定控件的id值。 |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 是 | 指定的文本匹配模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件id属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { MatchPattern, On, ON } from '@kit.TestKit';

let on: On = ON.id('id', MatchPattern.REG_EXP_ICASE); // 忽略大小写匹配控件的id属性值。
```

## inWindow

```TypeScript
inWindow(bundleName: string): On
```

指定目标控件位于给出的应用窗口内，返回On对象自身。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用窗口的包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件位于给出的应用窗口内的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.inWindow('com.uitestScene.acts'); // 使用静态构造器ON创建On对象，指定目标控件位于给出的应用窗口内。
```

## isAfter

```TypeScript
isAfter(on: On): On
```

指定目标控件位于给出的特征属性控件之后，返回On对象自身。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| on | [On](arkts-test-uitest-on-c.md) | 是 | 特征控件的属性要求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件位于给出的特征属性控件之后的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

// 使用静态构造器ON创建On对象，指定目标控件位于给出的特征属性控件之后。
let on: On = ON.type('Text').isAfter(ON.text('123')); // 查找text为123之后的第一个Text组件。
```

## isBefore

```TypeScript
isBefore(on: On): On
```

指定目标控件位于给出的特征属性控件之前，返回On对象自身。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| on | [On](arkts-test-uitest-on-c.md) | 是 | 特征控件的属性要求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件位于给出的特征属性控件之前的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

// 使用静态构造器ON创建On对象，指定目标控件位于给出的特征属性控件之前。
let on: On = ON.type('Button').isBefore(ON.text('123')); // 查找text为123之前的第一个Button组件。
```

## longClickable

```TypeScript
longClickable(b?: boolean): On
```

指定目标控件的可长按点击状态属性，返回On对象自身。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 指定控件可长按点击状态。true：可长按点击。false：不可长按点击。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件的可长按点击状态属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.longClickable(true); // 使用静态构造器ON创建On对象，指定目标控件的可长按点击状态属性。
```

## originalText

```TypeScript
originalText(text: string, pattern?: MatchPattern): On
```

指定控件的文本内容和文本匹配模式，返回On对象自身。

> **说明：**
> 
> 如果控件的无障碍属性
> accessibilityLevel
> 设置为'no'或'no-hide-descendants'，可以使用本接口指定目标控件的文本属性用于查找控件，使用[On.text()](#text)接口不生效。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 指定控件文本，用于匹配目标控件文本。 |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 否 | 指定的文本匹配模式，默认为[EQUALS](arkts-test-uitest-matchpattern-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件文本属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000007](../errorcode-uitest.md#17000007-参数不合法) | Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.originalText('123'); // 使用静态构造器ON创建On对象，指定目标控件的originalText属性。
```

## scrollable

```TypeScript
scrollable(b?: boolean): On
```

指定目标控件的可滑动状态属性，返回On对象自身。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 控件可滑动状态。true：可滑动。false：不可滑动。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件的可滑动状态属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.scrollable(true); // 使用静态构造器ON创建On对象，指定目标控件的可滑动状态属性。
```

## selected

```TypeScript
selected(b?: boolean): On
```

指定目标控件的被选中状态属性，返回On对象自身。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| b | boolean | 否 | 指定控件被选中状态。true：被选中。false：未被选中。默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件的被选中状态属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.selected(true); // 使用静态构造器ON创建On对象，指定目标控件的被选中状态属性。
```

## text

```TypeScript
text(txt: string, pattern?: MatchPattern): On
```

指定目标控件文本属性，支持多种匹配模式，返回On对象自身。

> **说明：**
> 
> 如果控件的无障碍属性
> accessibilityLevel
> 设置为'no'或'no-hide-descendants'，无法使用本接口指定目标控件的文本属性用于查找控件，可以使用[On.originalText()](#originaltext)接口实现。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| txt | string | 是 | 指定控件文本，用于匹配目标控件文本。 |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 否 | 指定的文本匹配模式，默认为[EQUALS](arkts-test-uitest-matchpattern-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件文本属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.text('123'); // 使用静态构造器ON创建On对象，指定目标控件的text属性。
```

## type

```TypeScript
type(tp: string): On
```

指定目标控件的控件类型属性，返回On对象自身。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tp | string | 是 | 指定控件类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件的控件类型属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.type('Button'); // 使用静态构造器ON创建On对象，指定目标控件的控件类型属性。
```

## type

```TypeScript
type(tp: string, pattern: MatchPattern): On
```

指定目标控件的控件类型属性和匹配模式，返回On对象自身。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tp | string | 是 | 指定控件类型。 |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 是 | 指定的文本匹配模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件的控件类型属性的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON, MatchPattern } from '@kit.TestKit';

let on: On = ON.type('Button', MatchPattern.EQUALS); // 使用静态构造器ON创建On对象，指定目标控件的控件类型属性。
```

## within

```TypeScript
within(on: On): On
```

指定目标控件位于给出的特征属性控件之内，返回On对象自身。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| on | [On](arkts-test-uitest-on-c.md) | 是 | 特征控件的属性要求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件位于给出的特征属性控件内的On对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

// 使用静态构造器ON创建On对象，指定目标控件位于给出的特征属性控件之内。
let on: On = ON.text('java').within(ON.type('Scroll')); // 查找Scroller里面的text为java的子组件。
```

## withinComponent

```TypeScript
withinComponent(com: Component): On
```

指定目标控件位于给出的特征控件（参数 [Component](arkts-test-uitest-component-c.md)）之内，返回 On 对象自身。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| com | [Component](arkts-test-uitest-component-c.md) | 是 | 特征控件，目标控件须位于该控件之内。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | 返回指定目标控件位于给出的特征控件之内的 On 对象. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000007](../errorcode-uitest.md#17000007-参数不合法) | Parameter verification failed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, On, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let component: Component = await driver.findComponent(ON.type('Text'));
  let on: On = ON.text('123').withinComponent(component); // 查找第一个Text组件内部的text为123的组件。
}
```
