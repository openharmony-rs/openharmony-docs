# UiComponent

UiTest中，UiComponent类代表了UI界面上的一个控件，提供控件属性获取，控件点击，滑动查找，文本注入等API。
该类提供的所有方法都使用Promise方式作为异步方法，需使用await调用。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[Component<sup>9+</sup>](arkts-test-component-c.md)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [Component](arkts-test-component-c.md)

**系统能力：** SystemCapability.Test.UiTest

## click

```TypeScript
click(): Promise<void>
```

控件对象进行点击操作。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[click<sup>9+</sup>](arkts-test-component-c.md#click-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [click](arkts-test-component-c.md#click-1)

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let button: UiComponent = await driver.findComponent(BY.type('Button'));
  await button.click();
}

```

## doubleClick

```TypeScript
doubleClick(): Promise<void>
```

控件对象进行双击操作。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[doubleClick<sup>9+</sup>](arkts-test-component-c.md#doubleclick-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [doubleClick](arkts-test-component-c.md#doubleclick-1)

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let button: UiComponent = await driver.findComponent(BY.type('Button'));
  await button.doubleClick();
}

```

## getId

```TypeScript
getId(): Promise<number>
```

获取控件对象的id值。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[getId<sup>9+</sup>](arkts-test-component-c.md#getid-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getId](arkts-test-component-c.md#getid-1)

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | - Promise对象，返回控件的id值。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let button: UiComponent = await driver.findComponent(BY.type('Button'));
  let id = await button.getId();
}

```

## getKey

```TypeScript
getKey(): Promise<string>
```

获取控件对象的key值。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[getId<sup>9+</sup>](arkts-test-component-c.md#getid-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getId](arkts-test-component-c.md#getid-1)

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | - Promise对象，返回控件的key值。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let button: UiComponent = await driver.findComponent(BY.type('Button'));
  let str_key = await button.getKey();
}

```

## getText

```TypeScript
getText(): Promise<string>
```

获取控件对象的文本信息。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[getText<sup>9+</sup>](arkts-test-component-c.md#gettext-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getText](arkts-test-component-c.md#gettext-1)

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | - Promise对象，返回控件的文本信息。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let button: UiComponent = await driver.findComponent(BY.type('Button'));
  let text = await button.getText();
}

```

## getType

```TypeScript
getType(): Promise<string>
```

获取控件对象的控件类型。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[getType<sup>9+</sup>](arkts-test-component-c.md#gettype-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getType](arkts-test-component-c.md#gettype-1)

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | - Promise对象，返回控件的类型。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let button: UiComponent = await driver.findComponent(BY.type('Button'));
  let type = await button.getType();
}

```

## inputText

```TypeScript
inputText(text: string): Promise<void>
```

向控件中输入文本，仅针对可编辑的文本组件生效。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[inputText<sup>9+</sup>](arkts-test-component-c.md#inputtext-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** inputText(text:

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 输入的文本信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let text: UiComponent = await driver.findComponent(BY.text('hello world'));
  await text.inputText('123');
}

```

## isClickable

```TypeScript
isClickable(): Promise<boolean>
```

获取控件对象可点击状态。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[isClickable<sup>9+</sup>](arkts-test-component-c.md#isclickable-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isClickable](arkts-test-component-c.md#isclickable-1)

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | - Promise对象，返回控件对象可点击状态。true：可点击。false：不可点击。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let button: UiComponent = await driver.findComponent(BY.type('Button'));
  if (await button.isClickable()) {
    console.info('This button can be Clicked');
  } else {
    console.info('This button cannot be Clicked');
  }
}

```

## isEnabled

```TypeScript
isEnabled(): Promise<boolean>
```

获取控件使能状态。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[isEnabled<sup>9+</sup>](arkts-test-component-c.md#isenabled-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isEnabled](arkts-test-component-c.md#isenabled-1)

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | - Promise对象，返回控件使能状态。true：使能。false：未使能。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let button: UiComponent = await driver.findComponent(BY.type('Button'));
  if (await button.isEnabled()) {
    console.info('This button can be operated');
  } else {
    console.info('This button cannot be operated');
  }
}


```

## isFocused

```TypeScript
isFocused(): Promise<boolean>
```

判断控件对象是否获焦。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[isFocused<sup>9+</sup>](arkts-test-component-c.md#isfocused-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isFocused](arkts-test-component-c.md#isfocused-1)

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | - Promise对象，返回控件对象是否获焦。true：获焦。false：未获焦。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let button: UiComponent = await driver.findComponent(BY.type('Button'));
  if (await button.isFocused()) {
    console.info('This button is focused');
  } else {
    console.info('This button is not focused');
  }
}

```

## isScrollable

```TypeScript
isScrollable(): Promise<boolean>
```

获取控件对象可滑动状态。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[isScrollable<sup>9+</sup>](arkts-test-component-c.md#isscrollable-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isScrollable](arkts-test-component-c.md#isscrollable-1)

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | - Promise对象，返回控件对象可滑动状态。true：可滑动。false：不可滑动。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let scrollBar: UiComponent = await driver.findComponent(BY.scrollable(true));
  if (await scrollBar.isScrollable()) {
    console.info('This scrollBar can be operated');
  } else {
    console.info('This scrollBar cannot be operated');
  }
}

```

## isSelected

```TypeScript
isSelected(): Promise<boolean>
```

获取控件对象被选中状态。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[isSelected<sup>9+</sup>](arkts-test-component-c.md#isselected-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isSelected](arkts-test-component-c.md#isselected-1)

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | - Promise对象，返回控件对象被选中的状态。true：被选中。false：未被选中。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let button: UiComponent = await driver.findComponent(BY.type('Button'));
  if (await button.isSelected()) {
    console.info('This button is selected');
  } else {
    console.info('This button is not selected');
  }
}

```

## longClick

```TypeScript
longClick(): Promise<void>
```

控件对象进行长按操作。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[longClick<sup>9+</sup>](arkts-test-component-c.md#longclick-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [longClick](arkts-test-component-c.md#longclick-1)

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let button: UiComponent = await driver.findComponent(BY.type('Button'));
  await button.longClick();
}

```

## scrollSearch

```TypeScript
scrollSearch(by: By): Promise<UiComponent>
```

在控件上滑动查找目标控件（适用于List等支持滑动的控件）。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用[scrollSearch<sup>9+</sup>](arkts-test-component-c.md#scrollsearch-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** scrollSearch(on:

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| by | By | 是 | 目标控件的属性要求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;UiComponent&gt; | - Promise对象，返回目标控件对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let scrollBar: UiComponent = await driver.findComponent(BY.type('Scroll'));
  let button = await scrollBar.scrollSearch(BY.text('next page'));
}

```

