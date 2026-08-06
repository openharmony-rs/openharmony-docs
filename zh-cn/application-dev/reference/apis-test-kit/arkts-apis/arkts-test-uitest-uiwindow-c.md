# UiWindow

UiWindow代表了UI界面上的一个窗口，提供窗口属性获取，窗口拖动、调整窗口大小等能力。 该类提供的所有方法都使用Promise方式作为异步方法，需使用await方式调用。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare class UiWindow--><!--Device-unnamed-declare class UiWindow-End-->

**系统能力：** SystemCapability.Test.UiTest

## close

```TypeScript
close(): Promise<void>
```

将窗口关闭。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-close(): Promise<void>--><!--Device-UiWindow-close(): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |
| [17000005](../errorcode-uitest.md#17000005-操作不支持) | This operation is not supported. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    await window.close();
  }
}
```

## focus

```TypeScript
focus(): Promise<void>
```

让窗口获焦。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-focus(): Promise<void>--><!--Device-UiWindow-focus(): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，返回无结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    await window.focus();
  }
}
```

## getBounds

```TypeScript
getBounds(): Promise<Rect>
```

获取窗口的边框信息。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-getBounds(): Promise<Rect>--><!--Device-UiWindow-getBounds(): Promise<Rect>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Rect&gt; | - Promise对象，返回窗口的边框信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    let rect = await window.getBounds();
  }
}
```

## getBundleName

```TypeScript
getBundleName(): Promise<string>
```

获取窗口归属应用的包名信息。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-getBundleName(): Promise<string>--><!--Device-UiWindow-getBundleName(): Promise<string>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | - Promise对象，返回窗口归属应用的包名信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    let name: string = await window.getBundleName();
  }
}
```

## getDisplayId

ArkTS-Dyn:
```TypeScript
getDisplayId(): Promise<number>
```

ArkTS-Sta:
```TypeScript
getDisplayId(): Promise<int>
```

获取窗口所属的屏幕ID。使用Promise异步回调。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-getDisplayId(): Promise<int>--><!--Device-UiWindow-getDisplayId(): Promise<int>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;int&gt; | - Promise对象，返回窗口所属的屏幕ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例：**

```TypeScript
// xxx.test.ets
import { UiWindow, Driver } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    let id = await window.getDisplayId();
  }
}
```

## getTitle

```TypeScript
getTitle(): Promise<string>
```

获取窗口的标题信息。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-getTitle(): Promise<string>--><!--Device-UiWindow-getTitle(): Promise<string>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | - Promise对象，返回窗口的标题信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    let title = await window.getTitle();
  }
}
```

## getWindowMode

```TypeScript
getWindowMode(): Promise<WindowMode>
```

获取窗口的窗口模式信息。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-getWindowMode(): Promise<WindowMode>--><!--Device-UiWindow-getWindowMode(): Promise<WindowMode>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;WindowMode&gt; | - Promise对象，返回窗口的窗口模式信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    let mode = await window.getWindowMode();
  }
}
```

## isActive

```TypeScript
isActive(): Promise<boolean>
```

判断窗口是否为用户正在交互窗口。使用Promise异步回调。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-isActive(): Promise<boolean>--><!--Device-UiWindow-isActive(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | - Promise对象，返回窗口对象是否为用户正在交互窗口。true：交互窗口。false：非交互窗口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    let focused = await window.isActive();
  }
}
```

## isActived

```TypeScript
isActived(): Promise<boolean>
```

判断窗口是否为用户正在交互窗口。使用Promise异步回调。 > **说明：** > > 从API version 9开始支持，从API version 11开始废弃，建议使用[isActive\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_11+\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 11

**替代接口：** [UiWindow#isActive](arkts-test-uitest-uiwindow-c.md#isactive)

<!--Device-UiWindow-isActived(): Promise<boolean>--><!--Device-UiWindow-isActived(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | - Promise对象，返回窗口对象是否为用户正在交互窗口。true表示是交互窗口。false表示非交互窗口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    let focused = await window.isActived();
  }
}
```

## isFocused

```TypeScript
isFocused(): Promise<boolean>
```

判断窗口是否处于获焦状态。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-isFocused(): Promise<boolean>--><!--Device-UiWindow-isFocused(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | - Promise对象，返回窗口对象是否获取获焦状态。true：获焦。false：未获焦。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    let focused = await window.isFocused();
  }
}
```

## maximize

```TypeScript
maximize(): Promise<void>
```

将窗口最大化。使用Promise异步回调。适用于支持窗口最大化操作的窗口。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-maximize(): Promise<void>--><!--Device-UiWindow-maximize(): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，返回无结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |
| [17000005](../errorcode-uitest.md#17000005-操作不支持) | This operation is not supported. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    await window.maximize();
  }
}
```

## minimize

```TypeScript
minimize(): Promise<void>
```

将窗口最小化。使用Promise异步回调。适用于支持窗口最小化操作的窗口。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-minimize(): Promise<void>--><!--Device-UiWindow-minimize(): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，返回无结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |
| [17000005](../errorcode-uitest.md#17000005-操作不支持) | This operation is not supported. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    await window.minimize();
  }
}
```

## moveTo

ArkTS-Dyn:
```TypeScript
moveTo(x: number, y: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
moveTo(x: int, y: int): Promise<void>
```

将窗口移动到目标点。使用Promise异步回调。适用于支持移动的窗口。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-moveTo(x: int, y: int): Promise<void>--><!--Device-UiWindow-moveTo(x: int, y: int): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 以number的形式传入目标点的横坐标信息，取值范围：大于等于0的整数。 |
| y | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 以number的形式传入目标点的纵坐标信息，取值范围：大于等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，返回无结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |
| [17000005](../errorcode-uitest.md#17000005-操作不支持) | This operation is not supported. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    await window.moveTo(100, 100);
  }
}
```

## resize

ArkTS-Dyn:
```TypeScript
resize(wide: number, height: number, direction: ResizeDirection): Promise<void>
```

ArkTS-Sta:
```TypeScript
resize(wide: int, height: int, direction: ResizeDirection): Promise<void>
```

根据传入的宽、高和调整方向来调整窗口的大小。使用Promise异步回调。适用于支持调整大小的窗口。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-resize(wide: int, height: int, direction: ResizeDirection): Promise<void>--><!--Device-UiWindow-resize(wide: int, height: int, direction: ResizeDirection): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wide | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 以number的形式传入调整后窗口的宽度，取值范围：大于等于0的整数。 |
| height | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 以number的形式传入调整后窗口的高度，取值范围：大于等于0的整数。 |
| direction | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 以[ResizeDirection]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的形式传入窗口调整的方向。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，返回无结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed. |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |
| [17000005](../errorcode-uitest.md#17000005-操作不支持) | This operation is not supported. |

## resume

```TypeScript
resume(): Promise<void>
```

将窗口恢复到之前的窗口模式。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-resume(): Promise<void>--><!--Device-UiWindow-resume(): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |
| [17000005](../errorcode-uitest.md#17000005-操作不支持) | This operation is not supported. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    await window.resume();
  }
}
```

## split

```TypeScript
split(): Promise<void>
```

将窗口模式切换成分屏模式。使用Promise异步回调。适用于支持切换分屏模式的窗口。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UiWindow-split(): Promise<void>--><!--Device-UiWindow-split(): Promise<void>-End-->

**系统能力：** SystemCapability.Test.UiTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，返回无结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000002](../errorcode-uitest.md#17000002-接口不支持并发调用) | The API does not support concurrent calls. |
| [17000004](../errorcode-uitest.md#17000004-目标控件窗口不可见或已销毁) | The window or component is invisible or destroyed. |
| [17000005](../errorcode-uitest.md#17000005-操作不支持) | This operation is not supported. |

**示例：**

```TypeScript
// xxx.test.ets
import { Driver, UiWindow } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let window: UiWindow | null = await driver.findWindow({ active: true });
  if (window) {
    await window.split();
  }
}
```

