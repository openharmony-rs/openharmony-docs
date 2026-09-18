# UiDriver

The **UiDriver** class is the main entry to the UiTest framework. It provides APIs for features such as component matching/search, key injection, coordinate clicking/sliding, and screenshot. All APIs provided by this class, except **UiDriver.create()**, use a promise to return the result and must be invoked using **await**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [Driver](arkts-test-uitest-driver-c.md)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## assertComponentExist

```TypeScript
assertComponentExist(by: By): Promise<void>
```

Asserts that a component that matches the given attributes exists on the current page. If the component does not exist, the API throws a JS exception, causing the current test case to fail. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [assertComponentExist](arkts-test-uitest-driver-c.md#assertcomponentexist)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| by | [By](arkts-test-uitest-by-c.md) | Yes | Attributes of the target component. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | if the input parameters are invalid. |
| [17000002](../errorcode-uitest.md#17000002-api-does-not-support-concurrent-calls) | The API does not support concurrent calls. |
| [17000003](../errorcode-uitest.md#17000003-assertion-failure) | if the assertion failed. |

**Examples**

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

Clicks a specific point of this **UiDriver** object based on the given coordinates. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [click](arkts-test-uitest-component-c.md#click)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Horizontal coordinate of the target point, in pixels. The value is an integer greater than or equal to 0. |
| y | number | Yes | Vertical coordinate of the target point, in pixels. The value is an integer greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

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

Creates a **UiDriver** object and returns the object created. This API is a static API.

> **NOTE:** 
> 
> This method is supported since API version 8 and deprecated since API version 9. You are advised to use
> [create&lt;sup&gt;9+&lt;/sup&gt;](arkts-test-uitest-driver-c.md#create) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [create](arkts-test-uitest-driver-c.md#create)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| [UiDriver](arkts-test-uitest-uidriver-c.md) | **UiDriver** object created. |

**Examples**

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

Delays a duration of time. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [delayMs](arkts-test-uitest-driver-c.md#delayms)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| duration | number | Yes | Specified time, in ms. The value is an integer greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

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

Double-clicks a specific point of this **UiDriver** object based on the given coordinates. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [doubleClick](arkts-test-uitest-component-c.md#doubleclick)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Horizontal coordinate of the target point, in pixels. The value is an integer greater than or equal to 0. |
| y | number | Yes | Vertical coordinate of the target point, in pixels. The value is an integer greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

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

Searches this **UiDriver** object for the target component that matches the given attributes. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [findComponent](arkts-test-uitest-driver-c.md#findcomponent)(on: On)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| by | [By](arkts-test-uitest-by-c.md) | Yes | Attributes of the target component. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[UiComponent](arkts-test-uitest-uicomponent-c.md)&gt; | Promise used to return the component. |

**Examples**

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

Searches this **UiDriver** object for all components that match the given attributes. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [findComponents](arkts-test-uitest-driver-c.md#findcomponents)(on: On)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| by | [By](arkts-test-uitest-by-c.md) | Yes | Attributes of the target component. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[UiComponent](arkts-test-uitest-uicomponent-c.md)&gt;&gt; | Promise used to return the list of components. |

**Examples**

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

Long-clicks a specific point of this **UiDriver** object based on the given coordinates. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [longClick](arkts-test-uitest-component-c.md#longclick)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Horizontal coordinate of the target point, in pixels. The value is an integer greater than or equal to 0. |
| y | number | Yes | Vertical coordinate of the target point, in pixels. The value is an integer greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

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

Presses the Back button on this **UiDriver** object. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [pressBack](arkts-test-uitest-driver-c.md#pressback)()

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

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

Captures the current screen of this **UiDriver** object and saves it as a PNG image to the given save path. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [screenCap](arkts-test-uitest-driver-c.md#screencap)(savePath: string)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| savePath | string | Yes | File save path. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return whether the screenshot operation is successful. The value **true** indicates the screenshot operation is successful, and **false** indicates the opposite. |

**Examples**

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

Swipes on this **UiDriver** object from the start point to the end point based on the given coordinates. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [swipe](arkts-test-uitest-driver-c.md#swipe)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startx | number | Yes | Horizontal coordinate of the start point, in pixels. The value is an integer greater than or equal to 0. |
| starty | number | Yes | Vertical coordinate of the start point, in pixels. The value is an integer greater than or equal to 0. |
| endx | number | Yes | Horizontal coordinate of the end point, in pixels. The value is an integer greater than or equal to 0. |
| endy | number | Yes | Vertical coordinate of the end point, in pixels. The value is an integer greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

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

Triggers a key event by passing the key code value. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [triggerKey](arkts-test-uitest-driver-c.md#triggerkey)(keyCode: number)

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyCode | number | Yes | Key code value. The value is an integer greater than or equal to 0. For details, see [KeyCode](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keycode-keycode-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
// xxx.test.ets
import { UiDriver } from '@kit.TestKit';
import { KeyCode } from '@kit.InputKit';

async function demo() {
  let driver: UiDriver = UiDriver.create();
  await driver.triggerKey(KeyCode.KEYCODE_BACK); // Back button
}
```
