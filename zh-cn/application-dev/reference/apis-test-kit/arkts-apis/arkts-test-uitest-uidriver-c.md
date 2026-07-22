# UiDriver

UiDriver类为uitest测试框架的总入口，提供控件匹配/查找，按键注入，坐标点击/滑动，截图等API。该类提供的方法除UiDriver.create()以外的所有方法都使用Promise方式作为异步方法，需使用await调用。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[Driver<sup>9+</sup>](arkts-test-uitest-driver-c.md)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [Driver](arkts-test-uitest-driver-c.md)

<!--Device-unnamed-declare class UiDriver--><!--Device-unnamed-declare class UiDriver-End-->

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { ResizeDirection, WindowMode, PenMode, PenKeyOperation, Driver, MatchPattern, UiDirection, TouchOptions, ComponentEventType, PointerMatrix, WindowChangeType, Component, ON, PenKey, Rect, InputTextMode, UIEventObserver, WindowFilter, WindowChangeOptions, UiWindow, TouchPadSwipeOptions, Point, KeyOptions, DisplayRotation, UIElementInfo, PenKeyOperationOptions, ComponentEventOptions, MouseButton, On } from '@kit.TestKit';
```

## assertComponentExist

```TypeScript
assertComponentExist(by: By): Promise<void>
```

断言API，用于断言当前界面存在满足给出的目标控件属性的控件; 如果控件不存在，该API将抛出JS异常，使当前测试用例失败。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[assertComponentExist<sup>9+</sup>](arkts-test-uitest-driver-c.md#assertcomponentexist)替  
> 代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [assertComponentExist](arkts-test-uitest-driver-c.md#assertcomponentexist)

<!--Device-UiDriver-assertComponentExist(by: By): Promise<void>--><!--Device-UiDriver-assertComponentExist(by: By): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| by | [By](arkts-test-uitest-by-c.md) | 是 | 目标控件的属性要求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | if the input parameters are invalid. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000003](../errorcode-uitest.md#17000003-断言失败) | if the assertion failed. |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  await driver.assertComponentExist(BY.text('next page'));
}

```

## click

```TypeScript
click(x: number, y: number): Promise<void>
```

UiDriver对象采取如下操作：在目标坐标点单击。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[click<sup>9+</sup>](arkts-test-uitest-component-c.md#click)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [click](arkts-test-uitest-component-c.md#click)

<!--Device-UiDriver-click(x: number, y: number): Promise<void>--><!--Device-UiDriver-click(x: number, y: number): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 以number的形式传入目标点的横坐标信息，取值范围：大于等于0的整数。 |
| y | number | 是 | 以number的形式传入目标点的纵坐标信息，取值范围：大于等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  await driver.click(100, 100);
}

```

## create

```TypeScript
static create(): UiDriver
```

静态方法，构造一个UiDriver对象，并返回该对象。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[create<sup>9+</sup>](arkts-test-uitest-driver-c.md#create)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [create](arkts-test-uitest-driver-c.md#create)

<!--Device-UiDriver-static create(): UiDriver--><!--Device-UiDriver-static create(): UiDriver-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UiDriver](arkts-test-uitest-uidriver-c.md) | - 返回构造的UiDriver对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
}

```

## delayMs

```TypeScript
delayMs(duration: number): Promise<void>
```

UiDriver对象在给定的时间内延时。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[delayMs<sup>9+</sup>](arkts-test-uitest-driver-c.md#delayms)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [delayMs](arkts-test-uitest-driver-c.md#delayms)

<!--Device-UiDriver-delayMs(duration: number): Promise<void>--><!--Device-UiDriver-delayMs(duration: number): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | number | 是 | 给定的时间。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  await driver.delayMs(1000);
}

```

## doubleClick

```TypeScript
doubleClick(x: number, y: number): Promise<void>
```

UiDriver对象采取如下操作：在目标坐标点双击。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[doubleClick<sup>9+</sup>](arkts-test-uitest-component-c.md#doubleclick)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [doubleClick](arkts-test-uitest-component-c.md#doubleclick)

<!--Device-UiDriver-doubleClick(x: number, y: number): Promise<void>--><!--Device-UiDriver-doubleClick(x: number, y: number): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 以number的形式传入目标点的横坐标信息，取值范围：大于等于0的整数。 |
| y | number | 是 | 以number的形式传入目标点的纵坐标信息，取值范围：大于等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  await driver.doubleClick(100, 100);
}

```

## findComponent

```TypeScript
findComponent(by: By): Promise<UiComponent>
```

在UiDriver对象中，根据给出的目标控件属性要求查找目标控件。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[findComponent<sup>9+</sup>](arkts-test-uitest-driver-c.md#findcomponent)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [findComponent(on:](arkts-test-uitest-driver-c.md#findcomponent)

<!--Device-UiDriver-findComponent(by: By): Promise<UiComponent>--><!--Device-UiDriver-findComponent(by: By): Promise<UiComponent>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| by | [By](arkts-test-uitest-by-c.md) | 是 | 目标控件的属性要求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;UiComponent&gt; | - Promise对象，返回控件对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let button: UiComponent = await driver.findComponent(BY.text('next page'));
}

```

## findComponents

```TypeScript
findComponents(by: By): Promise<Array<UiComponent>>
```

在UiDriver对象中，根据给出的目标控件属性要求查找出所有匹配控件，以列表保存。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[findComponents<sup>9+</sup>](arkts-test-uitest-driver-c.md#findcomponents)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [findComponents(on:](arkts-test-uitest-driver-c.md#findcomponents)

<!--Device-UiDriver-findComponents(by: By): Promise<Array<UiComponent>>--><!--Device-UiDriver-findComponents(by: By): Promise<Array<UiComponent>>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| by | [By](arkts-test-uitest-by-c.md) | 是 | 目标控件的属性要求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;UiComponent&gt;&gt; | - Promise对象，返回控件对象的列表。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver, BY, UiComponent } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  let buttonList: Array<UiComponent> = await driver.findComponents(BY.text('next page'));
}

```

## longClick

```TypeScript
longClick(x: number, y: number): Promise<void>
```

UiDriver对象采取如下操作：在目标坐标点长按下鼠标左键。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[longClick<sup>9+</sup>](arkts-test-uitest-component-c.md#longclick)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [longClick](arkts-test-uitest-component-c.md#longclick)

<!--Device-UiDriver-longClick(x: number, y: number): Promise<void>--><!--Device-UiDriver-longClick(x: number, y: number): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 以number的形式传入目标点的横坐标信息，取值范围：大于等于0的整数。 |
| y | number | 是 | 以number的形式传入目标点的纵坐标信息，取值范围：大于等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  await driver.longClick(100, 100);
}

```

## pressBack

```TypeScript
pressBack(): Promise<void>
```

UiDriver对象进行点击BACK键的操作。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[pressBack<sup>9+</sup>](arkts-test-uitest-driver-c.md#pressback)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [pressBack()](arkts-test-uitest-driver-c.md#pressback)

<!--Device-UiDriver-pressBack(): Promise<void>--><!--Device-UiDriver-pressBack(): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  await driver.pressBack();
}

```

## screenCap

```TypeScript
screenCap(savePath: string): Promise<boolean>
```

UiDriver对象采取如下操作：捕获当前屏幕，并保存为PNG格式的图片至给出的保存路径中。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[screenCap<sup>9+</sup>](arkts-test-uitest-driver-c.md#screencap)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [screenCap(savePath:](arkts-test-uitest-driver-c.md#screencap)

<!--Device-UiDriver-screenCap(savePath: string): Promise<boolean>--><!--Device-UiDriver-screenCap(savePath: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| savePath | string | 是 | 文件保存路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | - Promise对象，返回截图操作是否成功完成。true：成功完成，false：未成功完成。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  await driver.screenCap('/data/storage/el2/base/cache/1.png');
}

```

## swipe

```TypeScript
swipe(startx: number, starty: number, endx: number, endy: number): Promise<void>
```

UiDriver对象采取如下操作：从给出的起始坐标点滑向给出的目的坐标点。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[swipe<sup>9+</sup>](arkts-test-uitest-driver-c.md#swipe)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [swipe](arkts-test-uitest-driver-c.md#swipe)

<!--Device-UiDriver-swipe(startx: number, starty: number, endx: number, endy: number): Promise<void>--><!--Device-UiDriver-swipe(startx: number, starty: number, endx: number, endy: number): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startx | number | 是 | 以number的形式传入起始点的横坐标信息，取值范围：大于等于0的整数。 |
| starty | number | 是 | 以number的形式传入起始点的纵坐标信息，取值范围：大于等于0的整数。 |
| endx | number | 是 | 以number的形式传入目的点的横坐标信息，取值范围：大于等于0的整数。 |
| endy | number | 是 | 以number的形式传入目的点的纵坐标信息，取值范围：大于等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver } from '@kit.TestKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  await driver.swipe(100, 100, 200, 200);
}

```

## triggerKey

```TypeScript
triggerKey(keyCode: number): Promise<void>
```

UiDriver对象采取如下操作：通过key值找到对应键并点击。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[triggerKey<sup>9+</sup>](arkts-test-uitest-driver-c.md#triggerkey)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [triggerKey(keyCode:](arkts-test-uitest-driver-c.md#triggerkey)

<!--Device-UiDriver-triggerKey(keyCode: number): Promise<void>--><!--Device-UiDriver-triggerKey(keyCode: number): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyCode | number | 是 | 指定的key值，取值大于等于0的整数，取值范围：[KeyCode键码值](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keycode-keycode-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
// xxx.test.ets
import { UiDriver } from '@kit.TestKit';
import { KeyCode } from '@kit.InputKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  await driver.triggerKey(KeyCode.KEYCODE_BACK); // 返回键
}

```

