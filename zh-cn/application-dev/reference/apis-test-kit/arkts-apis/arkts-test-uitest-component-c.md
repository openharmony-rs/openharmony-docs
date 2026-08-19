# Component

UiTest框架在API9中，Component类代表了UI界面上的一个控件，提供控件属性获取，控件点击，滑动查找，文本注入等API。 该类对象可通过[findComponent](arkts-test-uitest-driver-c.md#findcomponent)、[findComponents](arkts-test-uitest-driver-c.md#findcomponents)、[waitForComponent](arkts-test-uitest-driver-c.md#waitforcomponent)等接口获取。 该类提供的所有方法都使用Promise方式作为异步方法，需使用await调用。

**起始版本：** 23

<!--Device-unnamed-declare class Component--><!--Device-unnamed-declare class Component-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## clearText

```TypeScript
clearText(): Promise<void>
```

清除控件的文本信息，仅针对可编辑的文本组件生效。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-clearText(): Promise<void>--><!--Device-Component-clearText(): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let text: Component | null = await driver.findComponent(ON.text('hello world'));
  if (text) {
    await text.clearText();
  }
}
```

## click

```TypeScript
click(): Promise<void>
```

控件对象进行点击操作。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-click(): Promise<void>--><!--Device-Component-click(): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Driver, ON, Component } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button) {
    await button.click();
  }
}
```

## doubleClick

```TypeScript
doubleClick(): Promise<void>
```

控件对象进行双击操作。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-doubleClick(): Promise<void>--><!--Device-Component-doubleClick(): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button) {
    await button.doubleClick();
  }
}
```

## dragTo

```TypeScript
dragTo(target: Component): Promise<void>
```

将控件拖拽至目标控件处。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-dragTo(target: Component): Promise<void>--><!--Device-Component-dragTo(target: Component): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | [Component](arkts-test-uitest-component-c.md) | 是 | 目标控件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  let text: Component | null = await driver.findComponent(ON.text('hello world'));
  if (button && text) {
    await button.dragTo(text);
  }
}
```

## getBounds

```TypeScript
getBounds(): Promise<Rect>
```

获取控件对象的边框信息。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-getBounds(): Promise<Rect>--><!--Device-Component-getBounds(): Promise<Rect>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Rect](arkts-test-uitest-rect-i.md)&gt; | Promise对象，返回控件对象的边框信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button) {
    let rect = await button.getBounds();
  }
}
```

## getBoundsCenter

```TypeScript
getBoundsCenter(): Promise<Point>
```

获取控件对象所占区域的中心点信息。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-getBoundsCenter(): Promise<Point>--><!--Device-Component-getBoundsCenter(): Promise<Point>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Point](arkts-test-uitest-point-i.md)&gt; | Promise对象，返回控件对象所占区域的中心点信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button) {
    let point = await button.getBoundsCenter();
  }
}
```

## getDescription

```TypeScript
getDescription(): Promise<string>
```

获取控件对象的描述信息。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Component-getDescription(): Promise<string>--><!--Device-Component-getDescription(): Promise<string>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回控件的描述信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button) {
    let description = await button.getDescription();
  }
}
```

## getDisplayId

```TypeScript
getDisplayId(): Promise<int>
```

获取控件对象所属的屏幕ID。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Component-getDisplayId(): Promise<int>--><!--Device-Component-getDisplayId(): Promise<int>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回控件所属的屏幕ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('TextInput'));
  if (button) {
    let displayId = await button.getDisplayId();
  }
}
```

## getHint

```TypeScript
getHint(): Promise<string>
```

获取控件对象的提示文本。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Component-getHint(): Promise<string>--><!--Device-Component-getHint(): Promise<string>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回控件的提示文本。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('TextInput'));
  if (button) {
    let hints = await button.getHint();
  }
}
```

## getId

```TypeScript
getId(): Promise<string>
```

获取控件对象的id值。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-getId(): Promise<string>--><!--Device-Component-getId(): Promise<string>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回控件的id值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button) {
    let id = await button.getId();
  }
}
```

## getOriginalText

```TypeScript
getOriginalText(): Promise<string>
```

获取控件对象的文本信息。使用Promise异步回调。如果控件的无障碍属性 [accessibilityLevel](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitylevel) 设置为'no'或'no-hide-descendants'，可以使用本接口获取控件的文本信息，无法使用[Component.getText()](#gettext)获取控件的文本信息。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Component-getOriginalText(): Promise<string>--><!--Device-Component-getOriginalText(): Promise<string>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回控件的文本信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button) {
    let text = await button.getOriginalText();
  }
}
```

## getText

```TypeScript
getText(): Promise<string>
```

获取控件对象的文本信息。使用Promise异步回调。 > **说明：**> > 如果控件的无障碍属性 > [accessibilityLevel](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitylevel) > 设置为'no'或'no-hide-descendants'，无法使用本接口获取控件的文本信息，可以使用[Component.getOriginalText()](#getoriginaltext) > 获取控件的文本信息。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-getText(): Promise<string>--><!--Device-Component-getText(): Promise<string>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回控件的文本信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button) {
    let text = await button.getText();
  }
}
```

## getType

```TypeScript
getType(): Promise<string>
```

获取控件对象的控件类型。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-getType(): Promise<string>--><!--Device-Component-getType(): Promise<string>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回控件的类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button) {
    let type = await button.getType();
  }
}
```

## inputText

```TypeScript
inputText(text: string): Promise<void>
```

清空组件内原有文本并输入指定文本内容，仅针对可编辑的文本组件生效。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-inputText(text: string): Promise<void>--><!--Device-Component-inputText(text: string): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 输入的文本信息，当前支持英文、中文和特殊字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let text: Component | null = await driver.findComponent(ON.text('hello world'));
  if (text) {
    await text.inputText('123');
  }
}
```

## inputText

```TypeScript
inputText(text: string, mode: InputTextMode): Promise<void>
```

向控件中输入文本，并支持指定文本输入方式，仅针对可编辑的文本组件生效。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Component-inputText(text: string, mode: InputTextMode): Promise<void>--><!--Device-Component-inputText(text: string, mode: InputTextMode): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 输入的文本信息，当前支持英文、中文和特殊字符。 |
| mode | [InputTextMode](arkts-test-uitest-inputtextmode-i.md) | 是 | 输入文本的方式，取值请参考[InputTextMode](arkts-test-uitest-inputtextmode-i.md)。  **说明：** InputTextMode.addition取值为true时，在控件已有文本末尾后追加指定文本。取值为false时，指定文本将覆盖控件已有文本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited device capabilities. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function mode_demo() {
  let driver: Driver = Driver.create();
  let text: Component | null = await driver.findComponent(ON.text('hello world'));
  if (text) {
    await text.inputText('123', { paste: true, addition: false });
  }
}
```

## isCheckable

```TypeScript
isCheckable(): Promise<boolean>
```

获取控件对象能否被勾选属性。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-isCheckable(): Promise<boolean>--><!--Device-Component-isCheckable(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回控件对象能否可被勾选属性。true：可被勾选。false：不可被勾选。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let checkBox: Component | null = await driver.findComponent(ON.type('Checkbox'));
  if (checkBox && await checkBox.isCheckable()) {
    console.info('This checkBox is checkable');
  } else {
    console.info('This checkBox is not checkable');
  }
}
```

## isChecked

```TypeScript
isChecked(): Promise<boolean>
```

获取控件对象被勾选状态。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-isChecked(): Promise<boolean>--><!--Device-Component-isChecked(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回控件对象被勾选状态。true：被勾选。false：未被勾选。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let checkBox: Component | null = await driver.findComponent(ON.type('Checkbox'));
  if (checkBox && await checkBox.isChecked()) {
    console.info('This checkBox is checked');
  } else {
    console.info('This checkBox is not checked');
  }
}
```

## isClickable

```TypeScript
isClickable(): Promise<boolean>
```

获取控件对象可点击属性。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-isClickable(): Promise<boolean>--><!--Device-Component-isClickable(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回控件对象是否可点击。true：可点击。false：不可点击。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button && await button.isClickable()) {
    console.info('This button can be Clicked');
  } else {
    console.info('This button can not be Clicked');
  }
}
```

## isEnabled

```TypeScript
isEnabled(): Promise<boolean>
```

获取控件使能状态。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-isEnabled(): Promise<boolean>--><!--Device-Component-isEnabled(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回控件使能状态。true：使能。false：未使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button && await button.isEnabled()) {
    console.info('This button can be operated');
  } else {
    console.info('This button can not be operated');
  }
}
```

## isFocused

```TypeScript
isFocused(): Promise<boolean>
```

判断控件对象获焦状态。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-isFocused(): Promise<boolean>--><!--Device-Component-isFocused(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回控件对象获焦状态。true：获焦。false：未获焦。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button && await button.isFocused()) {
    console.info('This button is focused');
  } else {
    console.info('This button is not focused');
  }
}
```

## isLongClickable

```TypeScript
isLongClickable(): Promise<boolean>
```

获取控件对象可点击属性。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-isLongClickable(): Promise<boolean>--><!--Device-Component-isLongClickable(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回控件对象是否可点击。true：可点击。false：不可点击。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button && await button.isLongClickable()) {
    console.info('This button can longClick');
  } else {
    console.info('This button can not longClick');
  }
}
```

## isScrollable

```TypeScript
isScrollable(): Promise<boolean>
```

获取控件对象可滑动属性。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-isScrollable(): Promise<boolean>--><!--Device-Component-isScrollable(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回控件对象是否可滑动。true：可滑动。false：不可滑动。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let scrollBar: Component | null = await driver.findComponent(ON.scrollable(true));
  if (scrollBar && await scrollBar.isScrollable()) {
    console.info('This scrollBar can be operated');
  } else {
    console.info('This scrollBar can not be operated');
  }
}
```

## isSelected

```TypeScript
isSelected(): Promise<boolean>
```

获取控件对象被选中状态。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-isSelected(): Promise<boolean>--><!--Device-Component-isSelected(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回控件对象被选中状态。true：被选中。false：未被选中。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button && await button.isSelected()) {
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

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-longClick(): Promise<void>--><!--Device-Component-longClick(): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component | null = await driver.findComponent(ON.type('Button'));
  if (button) {
    await button.longClick();
  }
}
```

## pinchIn

```TypeScript
pinchIn(scale: double): Promise<void>
```

将控件按指定的比例进行捏合缩小。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-pinchIn(scale: double): Promise<void>--><!--Device-Component-pinchIn(scale: double): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | double | 是 | 指定缩小的比例。取值范围为0~1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let image: Component | null = await driver.findComponent(ON.type('Image'));
  if (image) {
    await image.pinchIn(0.5);
  }
}
```

## pinchOut

```TypeScript
pinchOut(scale: double): Promise<void>
```

将控件按指定的比例进行捏合放大。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-pinchOut(scale: double): Promise<void>--><!--Device-Component-pinchOut(scale: double): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | double | 是 | 指定放大的比例。取值范围大于1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let image: Component | null = await driver.findComponent(ON.type('Image'));
  if (image) {
    await image.pinchOut(1.5);
  }
}
```

## scrollSearch

```TypeScript
scrollSearch(on: On): Promise<Component>
```

在控件上滑动查找目标控件（适用支持滑动的控件）。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-scrollSearch(on: On): Promise<Component>--><!--Device-Component-scrollSearch(on: On): Promise<Component>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| on | [On](arkts-test-uitest-on-c.md) | 是 | 目标控件的属性要求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Component](arkts-test-uitest-component-c.md)&gt; | Promise对象，返回目标控件对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let scrollBar: Component | null = await driver.findComponent(ON.type('Scroll'));
  if (scrollBar) {
  let button = await scrollBar.scrollSearch(ON.text('next page'));
    if (button) {
      await button.click();
    }
  }
}
```

## scrollSearch

```TypeScript
scrollSearch(on: On, vertical?: boolean, offset?: number): Promise<Component>
```

在控件上滑动查找目标控件（适用支持滑动的控件），支持指定滑动方向和滑动起止点与组件边框的偏移量。使用Promise异步回调。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Component-scrollSearch(on: On, vertical?: boolean, offset?: number): Promise<Component>--><!--Device-Component-scrollSearch(on: On, vertical?: boolean, offset?: number): Promise<Component>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| on | [On](arkts-test-uitest-on-c.md) | 是 | 目标控件的属性要求。 |
| vertical | boolean | 否 | 默认为true，表示查找方向是纵向。false表示查找方向为横向。 |
| offset | number | 否 | 滑动起点/终点到组件边框的偏移，默认80，单位：px，取值范围：大于等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Component](arkts-test-uitest-component-c.md)&gt; | Promise对象，返回目标控件对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let scrollBar: Component | null = await driver.findComponent(ON.type('Scroll'));
  if (scrollBar) {
  let button = await scrollBar.scrollSearch(ON.text('next page'));
    if (button) {
      await button.click();
    }
  }
}
```

## scrollSearch

```TypeScript
scrollSearch(on: On, vertical?: boolean, offset?: int): Promise<Component | null>
```

Scroll on this [Component](#component)to find matched [Component](#component),applicable to scrollable one.

**起始版本：** 23

<!--Device-Component-scrollSearch(on: On, vertical?: boolean, offset?: int): Promise<Component | null>--><!--Device-Component-scrollSearch(on: On, vertical?: boolean, offset?: int): Promise<Component | null>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| on | [On](arkts-test-uitest-on-c.md) | 是 | the attribute requirements of the target [Component](#component). |
| vertical | boolean | 否 | Whether the swipe direction is vertical, default is true. |
| offset | int | 否 | Offset from the swipe start/end point to the component border, default is 80. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Component](arkts-test-uitest-component-c.md) \| null&gt; | the found result,or null if not found. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let scrollBar: Component = await driver.findComponent(ON.type('Scroll'));
  let button = await scrollBar.scrollSearch(ON.text('next page'));
}
```

## scrollToBottom

```TypeScript
scrollToBottom(speed?: int): Promise<void>
```

在控件上滑动到底部（适用支持滑动的控件）。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-scrollToBottom(speed?: int): Promise<void>--><!--Device-Component-scrollToBottom(speed?: int): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speed | int | 否 | 滑动速率，取值范围为200-40000的整数，默认值为600，单位：px/s。为不在范围内的非负数或为null/undefined时设为默认值600。为负数时抛出401错误码。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let scrollBar: Component | null = await driver.findComponent(ON.type('Scroll'));
  if (scrollBar) {
    await scrollBar.scrollToBottom();
  }
}
```

## scrollToTop

```TypeScript
scrollToTop(speed?: int): Promise<void>
```

在控件上滑动到顶部（适用支持滑动的控件）。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Component-scrollToTop(speed?: int): Promise<void>--><!--Device-Component-scrollToTop(speed?: int): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speed | int | 否 | 滑动速率，取值范围为200-40000的整数，默认值为600，单位：px/s。为不在范围内的非负数或为null/undefined时设为默认值600。为负数时抛出401错误码。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例**

```TypeScript
// xxx.test.ets
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let scrollBar: Component | null = await driver.findComponent(ON.type('Scroll'));
  if (scrollBar) {
    await scrollBar.scrollToTop();
  }
}
```

