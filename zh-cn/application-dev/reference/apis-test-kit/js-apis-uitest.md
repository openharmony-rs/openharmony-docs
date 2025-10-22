**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

| bundleName | string | 是   | 否   | 归属应用的包名。      |
| type       | string | 是   | 否   | 控件/窗口类型。       |
| text       | string | 是   | 否   | 控件/窗口的文本信息。 |


## TouchPadSwipeOptions<sup>18+</sup>

触摸板多指滑动手势选项相关信息。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

| 名称       | 类型   | 只读 | 可选 | 说明                                                     |
| ---------- | ------ |----|----|--------------------------------------------------------|
| stay | boolean | 否  | 是  | 触摸板多指滑动结束是否停留1s后再抬起，默认为false（不停留1s），true：停留，false：不停留。 |
| speed       | number | 否  | 是  | 滑动速率，取值范围为200-40000的整数，默认值为2000，不在范围内设为默认值为2000，单位：px/s。  |


## InputTextMode<sup>20+</sup>

输入文本的方式。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

| 名称       | 类型   | 只读 | 可选 | 说明                                                       |
| ---------- | ------ |----|----|----------------------------------------------------------|
| paste | boolean | 否  | 是  | 输入文本时是否指定以复制粘贴方式输入。true：指定以复制粘贴方式输入。false：指定以逐字键入方式输入。默认为false。<br /> **说明：** 当输入文本中包含中文、特殊字符或文本长度超过200字符时，无论该参数取值为何，均以复制粘贴方式输入。|
| addition       | boolean | 否  | 是  | 输入文本时是否以追加的方式进行输入。true：以追加方式输入。false：不以追加方式输入。默认为false。|


## On<sup>9+</sup>

UiTest框架从API version 9开始，通过On类提供了丰富的控件特征描述API，用于进行控件筛选来匹配/查找出目标控件。<br>
On提供的API能力具有以下几个特点:<br>1、支持单属性匹配和多属性组合匹配，例如同时指定目标控件text和id。<br>2、控件属性支持多种匹配模式。<br>3、支持控件绝对定位，相对定位，可通过[ON.isBefore](#isbefore9)和[ON.isAfter](#isafter9)等API限定邻近控件特征进行辅助定位。<br>On类提供的所有API均为同步接口，建议使用者通过静态构造器ON来链式创建On对象。

```ts
import { ON } from '@kit.TestKit';

ON.text('123').type('Button');
```

### text<sup>9+</sup>

text(txt: string, pattern?: MatchPattern): On

指定目标控件文本属性，支持多种匹配模式，返回On对象自身。

> **说明**
>
> 如果控件的无障碍属性[accessibilityLevel](../apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitylevel)设置为'no'或'no-hide-descendants'，无法使用本接口指定目标控件的文本属性用于查找控件，可以使用[On.originalText()](#originaltext20)接口实现。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

**参数：**

| 参数名  | 类型                          | 必填 | 说明                                                |
| ------- | ----------------------------- | ---- | --------------------------------------------------- |
| txt     | string                        | 是   | 指定控件文本，用于匹配目标控件文本。<!--RP2--><!--RP2End--> |
| pattern | [MatchPattern](#matchpattern) | 否   | 指定的文本匹配模式，默认为[EQUALS](#matchpattern)。 |

**返回值：**

| 类型       | 说明                               |
| ---------- | ---------------------------------- |
| [On](#on9) | 返回指定目标控件文本属性的On对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.|

**示例：**

```ts
import { On, ON } from '@kit.TestKit';
let on:On = ON.text('123'); // 使用静态构造器ON创建On对象，指定目标控件的text属性。
```

### id<sup>9+</sup>

id(id: string): On

指定目标控件id属性，返回On对象自身。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型   | 必填 | 说明             |
| ------ | ------ | ---- | ---------------- |
| id     | string | 是   | 指定控件的id值。<!--RP2--><!--RP2End-->  |

**返回值：**

| 类型       | 说明                             |
| ---------- | -------------------------------- |
| [On](#on9) | 返回指定目标控件id属性的On对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.|

**示例：**

```ts
import { On, ON } from '@kit.TestKit';

let on:On = ON.id('123'); // 使用静态构造器ON创建On对象，指定目标控件的id属性。
```

### id<sup>18+</sup>

id(id: string, pattern: MatchPattern): On

指定目标控件id属性和匹配模式，返回On对象自身。
指定目标控件的控件类型属性和匹配模式，返回On对象自身。
在控件上滑动查找目标控件（适用支持滑动的控件），支持指定滑动方向和滑动起止点与组件边框的偏移量，使用Promise异步回调。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

**参数：**

| 参数名                    | 类型       | 必填 | 说明                                |
|------------------------| ---------- | ---- |-----------------------------------|
| on                     | [On](#on9) | 是   | 目标控件的属性要求。                        |
| vertical |    boolean | 否 | 默认为true，表示查找方向是纵向。false表示查找方向为横向。 |
| offset   | number| 否 | 滑动起点/终点到组件边框的偏移，默认80，单位：px，取值范围：大于等于0的整数。    |

**返回值：**

| 类型                               | 说明                                  |
| ---------------------------------- | ------------------------------------- |
| Promise\<[Component](#component9)> | Promise对象，返回目标控件对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[uitest测试框架错误码](errorcode-uitest.md)。

| 错误码ID | 错误信息                               |
| -------- | ---------------------------------------- |
| 17000002 | The async function is not called with await. |
| 17000004 | The window or component is invisible or destroyed.           |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.|

**示例：**

```ts
import { Component, Driver, ON } from '@kit.TestKit';
async function demo() {
  let driver: Driver = Driver.create();
  let scrollBar: Component = await driver.findComponent(ON.type('Scroll'));
  let button = await scrollBar.scrollSearch(ON.text('next page'));
}
```

### scrollToTop<sup>9+</sup>

scrollToTop(speed?: number): Promise\<void>

在控件上滑动到顶部（适用支持滑动的控件），使用Promise异步回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                     |
| ------ | ------ | ---- |--------------------------------------------------------|
| speed  | number | 否   | 滑动速率，取值范围为200-40000的整数，默认值为600，不在范围内设为默认值为600，单位：px/s。 |

**返回值：**

| 类型             | 说明              |
|----------------|-----------------|
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[uitest测试框架错误码](errorcode-uitest.md)。

| 错误码ID | 错误信息                               |
| -------- | ---------------------------------------- |
| 17000002 | The async function is not called with await. |
| 17000004 | The window or component is invisible or destroyed.           |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed.|

**示例：**

```ts
import { Component, Driver, ON } from '@kit.TestKit';
async function demo() {
  let driver: Driver = Driver.create();
  let scrollBar: Component = await driver.findComponent(ON.type('Scroll'));
  await scrollBar.scrollToTop();
}
```

### scrollToBottom<sup>9+</sup>

scrollToBottom(speed?: number): Promise\<void>

在控件上滑动到底部（适用支持滑动的控件），使用Promise异步回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                     |
| ------ | ------ | ---- |--------------------------------------------------------|
| speed  | number | 否   | 滑动速率，取值范围为200-40000的整数，默认值为600，不在范围内设为默认值为600，单位：px/s。 |

**返回值：**

| 类型             | 说明              |
|----------------|-----------------|
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[uitest测试框架错误码](errorcode-uitest.md)。

| 错误码ID | 错误信息                               |
| -------- | ---------------------------------------- |
| 17000002 | The async function is not called with await. |
| 17000004 | The window or component is invisible or destroyed.           |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed.|

**示例：**

```ts
import { Component, Driver, ON } from '@kit.TestKit';
async function demo() {
  let driver: Driver = Driver.create();
  let scrollBar: Component = await driver.findComponent(ON.type('Scroll'));
  await scrollBar.scrollToBottom();
}
```

### dragTo<sup>9+</sup>

dragTo(target: Component): Promise\<void>

将控件拖拽至目标控件处，使用Promise异步回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

**设备行为差异**：该接口在Phone、Tablet、PC/2in1、TV设备上生效，在其他设备中调用无效果。

**参数：**

| 参数名 | 类型                     | 必填 | 说明       |
| ------ | ------------------------ | ---- | ---------- |
| target | [Component](#component9) | 是   | 目标控件。 |

**返回值：**

| 类型             | 说明              |
|----------------|-----------------|
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[uitest测试框架错误码](errorcode-uitest.md)。

| 错误码ID | 错误信息                               |
| -------- | ---------------------------------------- |
| 17000002 | The async function is not called with await. |
| 17000004 | The window or component is invisible or destroyed.           |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.|

**示例：**

```ts
import { Component, Driver, ON } from '@kit.TestKit';
async function demo() {
  let driver: Driver = Driver.create();
  let button: Component = await driver.findComponent(ON.type('Button'));
  let text: Component = await driver.findComponent(ON.text('hello world'));
  await button.dragTo(text);
}
```

### pinchOut<sup>9+</sup>

pinchOut(scale: number): Promise\<void>

将控件按指定的比例进行捏合放大，使用Promise异步回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型   | 必填 | 说明                            |
| ------ | ------ | ---- | ------------------------------- |
| scale  | number | 是   | 指定放大的比例。取值范围大于1。 |

**返回值：**

| 类型             | 说明              |
|----------------|-----------------|
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[uitest测试框架错误码](errorcode-uitest.md)。

| 错误码ID | 错误信息                               |
| -------- | ---------------------------------------- |
| 17000002 | The async function is not called with await. |
| 17000004 | The window or component is invisible or destroyed.           |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.|

**示例：**

```ts
import { Component, Driver, ON } from '@kit.TestKit';
async function demo() {
  let driver: Driver = Driver.create();
  let image: Component = await driver.findComponent(ON.type('Image'));
  await image.pinchOut(1.5);
}
```

### pinchIn<sup>9+</sup>

pinchIn(scale: number): Promise\<void>

将控件按指定的比例进行捏合缩小，使用Promise异步回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型   | 必填 | 说明                            |
| ------ | ------ | ---- | ------------------------------- |
| scale  | number | 是   | 指定缩小的比例。取值范围为0~1。 |

**返回值：**

| 类型             | 说明              |
|----------------|-----------------|
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[uitest测试框架错误码](errorcode-uitest.md)。

| 错误码ID | 错误信息                               |
| -------- | ---------------------------------------- |
| 17000002 | The async function is not called with await. |
| 17000004 | The window or component is invisible or destroyed.           |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.|

**示例：**

```ts
import { Component, Driver, ON } from '@kit.TestKit';
async function demo() {
  let driver: Driver = Driver.create();
  let image: Component = await driver.findComponent(ON.type('Image'));
  await image.pinchIn(0.5);
}
```

### getDescription<sup>11+</sup>

getDescription(): Promise\<string>

获取控件对象的描述信息，使用Promise异步回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

**返回值：**

| 类型             | 说明                              |
| ---------------- | --------------------------------- |
| Promise\<string> | Promise对象，返回控件的描述信息。 |

**错误码：**

以下错误码的详细介绍请参见[uitest测试框架错误码](errorcode-uitest.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 17000002 | The async function is not called with await.             |
| 17000004 | The window or component is invisible or destroyed.                  |

**示例：**

```ts
import { Component, Driver, ON } from '@kit.TestKit';
async function demo() {
  let driver: Driver = Driver.create();
  let button: Component = await driver.findComponent(ON.type('Button'));
  let description = await button.getDescription();
}
```
### getHint<sup>18+</sup>

getHint(): Promise\<string>

获取控件对象的提示文本，使用Promise异步回调。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

**返回值：**

| 类型             | 说明                   |
| ---------------- |----------------------|
| Promise\<string> | Promise对象，返回控件的提示文本。 |

**错误码：**

以下错误码的详细介绍请参见[uitest测试框架错误码](errorcode-uitest.md)。

| 错误码ID | 错误信息                                 |
| -------- | ---------------------------------------- |
| 17000002 | The async function is not called with await. |
| 17000004 | The window or component is invisible or destroyed.           |

**示例：**

```ts
import { Component, Driver, ON } from '@kit.TestKit';
async function demo() {
  let driver: Driver = Driver.create();
  let button: Component = await driver.findComponent(ON.type('TextInput'));
  let hints = await button.getHint();
}
```
### getDisplayId<sup>20+</sup>

getDisplayId(): Promise\<number>

获取控件对象所属的屏幕ID，使用Promise异步回调。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.UiTest

**返回值：**

| 类型             | 说明                   |
| ---------------- |----------------------|
| Promise\<number> | Promise对象，返回控件所属的屏幕ID。 |

**错误码：**

以下错误码的详细介绍请参见[uitest测试框架错误码](errorcode-uitest.md)。

| 错误码ID | 错误信息                                 |
| -------- | ---------------------------------------- |
| 17000002 | The async function is not called with await. |
| 17000004 | The window or component is invisible or destroyed.           |

**示例：**

```ts
import { Component, Driver, ON } from '@kit.TestKit';

async function demo() {
  let driver: Driver = Driver.create();
  let button: Component = await driver.findComponent(ON.type('TextInput'));
  let displayId = await button.getDisplayId();
}
```

### getOriginalText<sup>20+</sup>

getOriginalText(): Promise\<string>

获取控件对象的文本信息，使用Promise异步回调。如果控件的无障碍属性[accessibilityLevel](../apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitylevel)设置为'no'或'no-hide-descendants'，可以使用本接口获取控件的文本信息，无法使用[Component.getText()](#gettext9)获取控件的文本信息。
指定方向和滑动速率，模拟手指滑动后脱离屏幕的快速滑动操作，使用Promise异步回调。
指定方向、滑动速率和操作屏幕，模拟手指滑动后脱离屏幕的快速滑动操作，使用Promise异步回调。
