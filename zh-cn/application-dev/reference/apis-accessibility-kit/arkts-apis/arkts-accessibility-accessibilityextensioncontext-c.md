# AccessibilityExtensionContext

辅助功能扩展的上下文环境，用来配置辅助应用关注信息类型、查询节点信息、手势注入等。

**继承/实现关系：** AccessibilityExtensionContext extends ExtensionContext

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare class AccessibilityExtensionContext--><!--Device-unnamed-declare class AccessibilityExtensionContext-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## getFocusElement

```TypeScript
getFocusElement(isAccessibilityFocus: boolean, callback: AsyncCallback<AccessibilityElement>): void
```

获取焦点元素, 使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityExtensionContext-getFocusElement(isAccessibilityFocus: boolean, callback: AsyncCallback<AccessibilityElement>): void--><!--Device-AccessibilityExtensionContext-getFocusElement(isAccessibilityFocus: boolean, callback: AsyncCallback<AccessibilityElement>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isAccessibilityFocus | boolean | 是 | 获取的是否是无障碍焦点元素，True表示是，False表示否。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | 是 | 回调函数，返回当前对应的焦点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

## 示例

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let isAccessibilityFocus = true;
let rootElement: AccessibilityElement;

// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.getFocusElement(isAccessibilityFocus, (err: BusinessError, data: AccessibilityElement) => {
  if (err) {
    console.error(`Failed to get focus element. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  rootElement = data;
  console.info(`succeeded in getting focus element, ${JSON.stringify(data)}`);
});
```

## getFocusElement

```TypeScript
getFocusElement(isAccessibilityFocus?: boolean): Promise<AccessibilityElement>
```

获取焦点元素, 使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityExtensionContext-getFocusElement(isAccessibilityFocus?: boolean): Promise<AccessibilityElement>--><!--Device-AccessibilityExtensionContext-getFocusElement(isAccessibilityFocus?: boolean): Promise<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isAccessibilityFocus | boolean | 否 | 获取的是否是无障碍焦点元素，true表示是，false表示否，默认为否。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise对象，返回当前对应的焦点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

## 示例

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootElement: AccessibilityElement;

// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.getFocusElement().then((data: AccessibilityElement) => {
  rootElement = data;
  console.info(`succeeded in getting focus element,${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get focus element. Code: ${err.code}, message: ${err.message}`);
});
```

## getFocusElement

```TypeScript
getFocusElement(callback: AsyncCallback<AccessibilityElement>): void
```

获取焦点元素, 使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityExtensionContext-getFocusElement(callback: AsyncCallback<AccessibilityElement>): void--><!--Device-AccessibilityExtensionContext-getFocusElement(callback: AsyncCallback<AccessibilityElement>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | 是 | 回调函数，返回当前对应的焦点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

## 示例

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootElement: AccessibilityElement;

// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.getFocusElement((err: BusinessError, data: AccessibilityElement) => {
  if (err) {
    console.error(`Failed to get focus element. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  rootElement = data;
  console.info(`succeeded in getting focus element, ${JSON.stringify(data)}`);
});
```

## getWindowRootElement

```TypeScript
getWindowRootElement(windowId: int, callback: AsyncCallback<AccessibilityElement>): void
```

获取指定窗口的根节点元素, 使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityExtensionContext-getWindowRootElement(windowId: int, callback: AsyncCallback<AccessibilityElement>): void--><!--Device-AccessibilityExtensionContext-getWindowRootElement(windowId: int, callback: AsyncCallback<AccessibilityElement>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | int | 是 | 指定窗口的编号，未指定则从当前活跃窗口获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | 是 | 回调函数，返回指定窗口的根节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

## 示例

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let windowId = 10;
let rootElement: AccessibilityElement;

// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.getWindowRootElement(windowId, (err: BusinessError, data: AccessibilityElement) => {
  if (err) {
    console.error(`Failed to get root element of the window. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  rootElement = data;
  console.info(`succeeded in getting root element of the window, ${JSON.stringify(data)}`);
});
```

## getWindowRootElement

```TypeScript
getWindowRootElement(windowId?: int): Promise<AccessibilityElement>
```

获取指定窗口的根节点元素, 使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityExtensionContext-getWindowRootElement(windowId?: int): Promise<AccessibilityElement>--><!--Device-AccessibilityExtensionContext-getWindowRootElement(windowId?: int): Promise<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | int | 否 | 指定窗口的编号，未指定则从当前活跃窗口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise对象，返回指定窗口的根节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

## 示例

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootElement: AccessibilityElement;

// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.getWindowRootElement().then((data: AccessibilityElement) => {
  rootElement = data;
  console.info(`succeeded in getting root element of the window, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get root element of the window. Code: ${err.code}, message: ${err.message}`);
});
```

## getWindowRootElement

```TypeScript
getWindowRootElement(callback: AsyncCallback<AccessibilityElement>): void
```

获取指定窗口的根节点元素, 使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityExtensionContext-getWindowRootElement(callback: AsyncCallback<AccessibilityElement>): void--><!--Device-AccessibilityExtensionContext-getWindowRootElement(callback: AsyncCallback<AccessibilityElement>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | 是 | 回调函数，返回指定窗口的根节点元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

## 示例

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rootElement: AccessibilityElement;

// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.getWindowRootElement((err: BusinessError, data: AccessibilityElement) => {
  if (err) {
    console.error(`Failed to get root element of the window. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  rootElement = data;
  console.info(`succeeded in getting root element of the window, ${JSON.stringify(data)}`);
});
```

## getWindows

```TypeScript
getWindows(displayId: long, callback: AsyncCallback<Array<AccessibilityElement>>): void
```

获取指定屏幕中的所有窗口，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityExtensionContext-getWindows(displayId: long, callback: AsyncCallback<Array<AccessibilityElement>>): void--><!--Device-AccessibilityExtensionContext-getWindows(displayId: long, callback: AsyncCallback<Array<AccessibilityElement>>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | long | 是 | 指定的屏幕编号，未指定则从默认主屏幕获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | 是 | 回调函数，返回指定屏幕的所有窗口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

## 示例

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let displayId = 10;
// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.getWindows(displayId, (err: BusinessError, data: AccessibilityElement[]) => {
  if (err) {
    console.error(`Failed to get windows. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting windows, ${JSON.stringify(data)}`);
});
```

## getWindows

```TypeScript
getWindows(displayId?: long): Promise<Array<AccessibilityElement>>
```

获取指定屏幕中的所有窗口，使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityExtensionContext-getWindows(displayId?: long): Promise<Array<AccessibilityElement>>--><!--Device-AccessibilityExtensionContext-getWindows(displayId?: long): Promise<Array<AccessibilityElement>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | long | 否 | 指定的屏幕编号，未指定则从默认主屏幕获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise对象，返回指定屏幕的所有窗口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

## 示例

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.getWindows().then((data: AccessibilityElement[]) => {
  console.info(`succeeded in getting windows, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get windows. Code: ${err.code}, message: ${err.message}`);
});
```

## getWindows

```TypeScript
getWindows(callback: AsyncCallback<Array<AccessibilityElement>>): void
```

获取指定屏幕中的所有窗口，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityExtensionContext-getWindows(callback: AsyncCallback<Array<AccessibilityElement>>): void--><!--Device-AccessibilityExtensionContext-getWindows(callback: AsyncCallback<Array<AccessibilityElement>>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | 是 | 回调函数，返回指定屏幕的所有窗口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

## 示例

```TypeScript
import { AccessibilityElement } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.getWindows((err: BusinessError, data: AccessibilityElement[]) => {
  if (err) {
    console.error(`Failed to get windows. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting windows, ${JSON.stringify(data)}`);
});
```

## injectGesture

```TypeScript
injectGesture(gesturePath: GesturePath, callback: AsyncCallback<void>): void
```

注入手势，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 10

**替代接口：** [injectGestureSync](#injectGestureSync)

<!--Device-AccessibilityExtensionContext-injectGesture(gesturePath: GesturePath, callback: AsyncCallback<void>): void--><!--Device-AccessibilityExtensionContext-injectGesture(gesturePath: GesturePath, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesturePath | [GesturePath](arkts-accessibility-accessibility-gesturepath-gesturepath-c.md) | 是 | 表示手势的路径信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，表示注入手势执行结果的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

## 示例

```TypeScript
import { GesturePath, GesturePoint } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let gesturePath: GesturePath = new GesturePath(100);
for (let i = 0; i < 10; i++) {
  let gesturePoint = new GesturePoint(100, i * 200);
  gesturePath.points.push(gesturePoint);
}
// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.injectGesture(gesturePath, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to inject gesture. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in injecting gesture,gesturePath is ${gesturePath}`);
});
```

## injectGesture

```TypeScript
injectGesture(gesturePath: GesturePath): Promise<void>
```

注入手势，使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 10

**替代接口：** [injectGestureSync](#injectGestureSync)

<!--Device-AccessibilityExtensionContext-injectGesture(gesturePath: GesturePath): Promise<void>--><!--Device-AccessibilityExtensionContext-injectGesture(gesturePath: GesturePath): Promise<void>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesturePath | [GesturePath](arkts-accessibility-accessibility-gesturepath-gesturepath-c.md) | 是 | 表示手势的路径信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

## 示例

```TypeScript
import { GesturePath, GesturePoint } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let gesturePath: GesturePath = new GesturePath(100);

for (let i = 0; i < 10; i++) {
  let gesturePoint = new GesturePoint(100, i * 200);
  gesturePath.points.push(gesturePoint);
}
// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.injectGesture(gesturePath).then(() => {
  console.info(`Succeeded in injecting gesture,gesturePath is ${gesturePath}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to inject gesture. Code: ${err.code}, message: ${err.message}`);
});
```

## injectGestureSync

```TypeScript
injectGestureSync(gesturePath: GesturePath): void
```

注入手势。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 12

<!--Device-AccessibilityExtensionContext-injectGestureSync(gesturePath: GesturePath): void--><!--Device-AccessibilityExtensionContext-injectGestureSync(gesturePath: GesturePath): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesturePath | [GesturePath](arkts-accessibility-accessibility-gesturepath-gesturepath-c.md) | 是 | 表示手势的路径信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

## 示例

```TypeScript
import { GesturePath, GesturePoint } from '@kit.AccessibilityKit';

let gesturePath: GesturePath = new GesturePath(100);
for (let i = 0; i < 10; i++) {
  let gesturePoint = new GesturePoint(100, i * 200);
  gesturePath.points.push(gesturePoint);
}
// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.injectGestureSync(gesturePath);
```

## setTargetBundleName

```TypeScript
setTargetBundleName(targetNames: Array<string>, callback: AsyncCallback<void>): void
```

设置关注的目标包名，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityExtensionContext-setTargetBundleName(targetNames: Array<string>, callback: AsyncCallback<void>): void--><!--Device-AccessibilityExtensionContext-setTargetBundleName(targetNames: Array<string>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetNames | Array&lt;string&gt; | 是 | 设置关注应用的包名，服务接收关注应用的无障碍事件，默认接收所有应用的无障碍事件，取消关注应用则传空数组。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，如果设置关注的目标包名失败，则AsyncCallback中err有数据返回。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let targetNames = ['com.ohos.xyz'];
try {
  // axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
  axContext.setTargetBundleName(targetNames, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to set target bundle names. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`succeeded in setting target bundle names, targetNames is ${targetNames}`);
  });
} catch (error) {
  console.error(`Failed to set target bundle names. Code: ${error.code}, message: ${error.message}`);
}
```

## setTargetBundleName

```TypeScript
setTargetBundleName(targetNames: Array<string>): Promise<void>
```

设置关注的目标包名，使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-AccessibilityExtensionContext-setTargetBundleName(targetNames: Array<string>): Promise<void>--><!--Device-AccessibilityExtensionContext-setTargetBundleName(targetNames: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetNames | Array&lt;string&gt; | 是 | 设置关注应用的包名，服务接收关注应用的无障碍事件，默认接收所有应用的无障碍事件，取消关注应用则传空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let targetNames = ['com.ohos.xyz'];
// axContext为AccessibilityExtensionContext实例，通过AccessibilityExtensionAbility子类的this.context获取，详见使用说明
axContext.setTargetBundleName(targetNames).then(() => {
  console.info(`succeeded in setting target bundle names, targetNames is ${targetNames}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set target bundle names. Code: ${err.code}, message: ${err.message}`);
});
```

