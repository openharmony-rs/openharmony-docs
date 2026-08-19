# AccessibilityExtensionContext

AccessibilityExtensionContext是AccessibilityExtensionAbility上下文环境，继承自ExtensionContext。 辅助功能扩展上下文模块提供辅助功能扩展的相关能力，包括配置关注信息类型、查询节点信息、手势注入等。

**继承/实现关系：** AccessibilityExtensionContext extends ExtensionContext

**起始版本：** 23

<!--Device-unnamed-declare class AccessibilityExtensionContext--><!--Device-unnamed-declare class AccessibilityExtensionContext-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## addAccessibilityVirtualNodes

```TypeScript
addAccessibilityVirtualNodes(elementId: long, windowId: int, nodes: Array<AccessibilityVirtualNode>): Promise<OperateVirtualNodeResult>
```

新增无障碍虚拟节点树。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityExtensionContext-addAccessibilityVirtualNodes(elementId: long, windowId: int, nodes: Array<AccessibilityVirtualNode>): Promise<OperateVirtualNodeResult>--><!--Device-AccessibilityExtensionContext-addAccessibilityVirtualNodes(elementId: long, windowId: int, nodes: Array<AccessibilityVirtualNode>): Promise<OperateVirtualNodeResult>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementId | long | 是 | 表示新增虚拟节点树的父节点ID。 |
| windowId | int | 是 | 表示新增虚拟节点树的父节点窗口ID。 |
| nodes | Array&lt;[AccessibilityVirtualNode](arkts-accessibility-accessibilityextensioncontext-accessibilityvirtualnode-i-sys.md)&gt; | 是 | 新增虚拟节点数组。 数组中的虚拟节点按parentId、childNodeIds父子关系构建成一棵树。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OperateVirtualNodeResult](arkts-accessibility-accessibility-operatevirtualnoderesult-e-sys.md)&gt; | Promise对象，返回执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300000](../errorcode-accessibility.md#9300000-无障碍系统服务工作异常) | System abnormality.Possible causes: <br>1.Internal operation failed. <br>2.Failed to obtain the required service or client object (null pointer). <br>3.IPC communication failed. <br>4.Failed to obtain the accessibility service proxy. <br>5.Timed out while waiting for the result of an asynchronous operation. |

**示例**

```TypeScript
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext,
  AccessibilityVirtualNode,
  OperateVirtualNodeResult
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let elementId: number = 10; // 请使用需要新增虚拟节点树的父节点ID。
    let windowId: number = 10; // 请使用需要新增虚拟节点树的窗口ID。
    let accessibilityVirtualNode: AccessibilityVirtualNode = {
      virtualNodeId: 1,
      accessibilityText: "accessibilityTextNew"
    }
    this.context.addAccessibilityVirtualNodes(elementId, windowId, [accessibilityVirtualNode]).then((data: OperateVirtualNodeResult)=>{
      console.info(`addAccessibilityVirtualNodes: elementId:${elementId} windowId:${windowId}, result:${data}`)
    }).catch((err: BusinessError) => {
      console.error(`failed to add virtual nodes, Code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

## getAccessibilityFocusedElement

```TypeScript
getAccessibilityFocusedElement(): Promise<AccessibilityElement>
```

获取当前获得无障碍焦点的元素。使用Promise异步回调。 无障碍焦点是指无障碍服务当前聚焦的节点，与输入焦点不同。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionContext-getAccessibilityFocusedElement(): Promise<AccessibilityElement>--><!--Device-AccessibilityExtensionContext-getAccessibilityFocusedElement(): Promise<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise对象，返回当前获得焦点的元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-目标应用和无障碍服务建立连接失败) | The target application failed to connect to accessibility service. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

**示例**

```TypeScript
import {
  AccessibilityElement,
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    this.context.getAccessibilityFocusedElement().then((element: AccessibilityElement) => {
      console.info(`succeeded in getting accessibility focused element, ${element.bundleName}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to get accessibility focused element. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## getAccessibilityWindowsSync

```TypeScript
getAccessibilityWindowsSync(displayId?: long): Array<AccessibilityElement>
```

获取当前显示设备上所有无障碍可访问的窗口列表。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionContext-getAccessibilityWindowsSync(displayId?: long): Array<AccessibilityElement>--><!--Device-AccessibilityExtensionContext-getAccessibilityWindowsSync(displayId?: long): Array<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | long | 否 | 显示ID。如果未提供此参数，则表示默认displayId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | 窗口列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

**示例**

```TypeScript
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      let displayId: number = 0;
      let windowList = this.context.getAccessibilityWindowsSync(displayId);
      if (windowList) {
        for (let window of windowList) {
          console.info(`getAccessibilityWindowsSync: windowId: ${window.windowId}`);
        }
      }
    } catch (err) {
     console.error(`Failed to get accessibility windows sync. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## getDefaultFocusedElementIds

```TypeScript
getDefaultFocusedElementIds(windowId: int): Promise<Array<long>>
```

查询应用自定义设置的默认焦点元素ID列表。使用Promise异步回调。 默认焦点是指窗口打开时无障碍服务优先聚焦的元素。

**起始版本：** 23

<!--Device-AccessibilityExtensionContext-getDefaultFocusedElementIds(windowId: int): Promise<Array<long>>--><!--Device-AccessibilityExtensionContext-getDefaultFocusedElementIds(windowId: int): Promise<Array<long>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | int | 是 | 表示查询的窗口ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;long&gt;&gt; | Promise对象，返回当前窗口下的自定义默认焦点列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let windowId: number = 10;

    this.context.getDefaultFocusedElementIds(windowId).then((data: number[]) => {
      console.info(`succeeded in getting default focus, ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to get default focus. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

ArkTS-Sta示例：

```TypeScript
import {
  AccessibilityEventInfo, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext): void {
    this.context = context;
  }

  onStop(): void {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEventInfo): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let windowId: int = 10;

    this.context.getDefaultFocusedElementIds(windowId).then((data: long[]) => {
      console.info(`Succeeded in get default focus, ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to get default focus, Code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

## getElements

```TypeScript
getElements(windowId: int, elementId?: long): Promise<Array<AccessibilityElement>>
```

批量查询指定窗口或指定节点下的所有后代无障碍节点。使用Promise异步回调。

**起始版本：** 23

<!--Device-AccessibilityExtensionContext-getElements(windowId: int, elementId?: long): Promise<Array<AccessibilityElement>>--><!--Device-AccessibilityExtensionContext-getElements(windowId: int, elementId?: long): Promise<Array<AccessibilityElement>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | int | 是 | 表示查询的窗口ID。 |
| elementId | long | 否 | 表示查询的节点ID。传入此参数表示查询该节点下的所有子节点列表（不包含该节点本身）；不传或传-1表示查询指定窗口下的完整节点树（包含根节点）。默认值为-1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt;&gt; | Promise对象，返回当前窗口或者当前节点下的所有子节点列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import {
  AccessibilityElement,
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let windowId: number = 10;
    let elementId: number = 10;

    this.context.getElements(windowId, elementId).then((data:AccessibilityElement[]) => {
      console.info(`succeeded in finding element, ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to find element. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

ArkTS-Sta示例：

```TypeScript
import {
  AccessibilityElement,
  AccessibilityEventInfo, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext): void {
    this.context = context;
  }

  onStop(): void {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEventInfo): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let windowId: int = 10;
    let elementId: long = 10;

    this.context.getElements(windowId, elementId).then((data:AccessibilityElement[]) => {
      console.info(`Succeeded in find element, ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to find element, Code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

## getRootInActiveWindow

```TypeScript
getRootInActiveWindow(windowId?: int): Promise<AccessibilityElement>
```

获取当前活动窗口的无障碍节点树根元素。使用Promise异步回调。 活动窗口是指当前获得焦点的前台应用窗口。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionContext-getRootInActiveWindow(windowId?: int): Promise<AccessibilityElement>--><!--Device-AccessibilityExtensionContext-getRootInActiveWindow(windowId?: int): Promise<AccessibilityElement>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | int | 否 | 表示查询的窗口ID。如果未提供此参数，则默认查询当前活动窗口的根元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)&gt; | Promise对象，返回活动窗口的根元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300006](../errorcode-accessibility.md#9300006-目标应用和无障碍服务建立连接失败) | The target application failed to connect to accessibility service. |
| [9300003](../errorcode-accessibility.md#9300003-不具备执行该操作的无障碍权限) | No accessibility permission to perform the operation. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import {
  AccessibilityElement,
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let windowId: number = 0;

    this.context.getRootInActiveWindow(windowId).then((element: AccessibilityElement) => {
      console.info(`succeeded in getting root in active window element, ${element.bundleName}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to get root in active window element. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

ArkTS-Sta示例：

```TypeScript
import {
  AccessibilityElement,
  AccessibilityEventInfo, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext): void {
    this.context = context;
  }

  onStop(): void {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEventInfo): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let windowId: int = 0;

    this.context.getRootInActiveWindow(windowId).then((element: AccessibilityElement) => {
      console.info(`Succeeded in getting root inactive window element, ${element.bundleName}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to get root inactive window element, Code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

## holdRunningLockSync

```TypeScript
holdRunningLockSync(): void
```

持有RunningLock锁，持锁后，屏幕不会自动灭屏。调用此方法后，在不需要保持屏幕常亮时调用 [unholdRunningLockSync](#unholdrunninglocksync)释放锁，恢复自动灭屏机制。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionContext-holdRunningLockSync(): void--><!--Device-AccessibilityExtensionContext-holdRunningLockSync(): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      this.context.holdRunningLockSync();
    } catch (err) {
      console.error(`Failed to hold RunningLock. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## notifyDisconnect

```TypeScript
notifyDisconnect(): void
```

通知无障碍服务可以关闭该辅助功能扩展服务。 此函数需要与注册预关闭接口 [on('preDisconnect')](#onpredisconnect)配合使用， 如果没有调用过注册预关闭函数，直接调用此函数不生效。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionContext-notifyDisconnect(): void--><!--Device-AccessibilityExtensionContext-notifyDisconnect(): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      this.context.notifyDisconnect();
    } catch (err) {
      console.error(`Failed to notify accessibility. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## offPreDisconnect

```TypeScript
offPreDisconnect(callback?: Callback<void>): void
```

Unregister accessibilityExtensionAbility disconnect callback.

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionContext-offPreDisconnect(callback?: Callback<void>): void--><!--Device-AccessibilityExtensionContext-offPreDisconnect(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | Indicates the callback function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import {
  AccessibilityEventInfo, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext): void {
    this.context = context;
  }

  onStop(): void {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEventInfo): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      this.context.offPreDisconnect(() => {
        console.info(`To do something before accessibilityExtension disconnect.`);
      });
    } catch (err: BusinessError) {
      console.error(`Failed to register, code is ${err.code}, message is ${err.message}`);
    }
  }
}
```

## off('preDisconnect')

```TypeScript
off(type: 'preDisconnect', callback?: Callback<void>): void
```

取消已经向无障碍服务注册的预关闭回调函数，需先通过on('preDisconnect')注册后才能取消。取消后，无障碍服务关闭该扩展服务前不再执行该回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionContext-off(type: 'preDisconnect', callback?: Callback<void>): void--><!--Device-AccessibilityExtensionContext-off(type: 'preDisconnect', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'preDisconnect' | 是 | 监听事件名，固定为‘preDisconnect’，即辅助功能扩展服务即将关闭的事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数，取消指定辅助功能扩展服务即将关闭时的回调。需与 [on('preDisconnect')](#onpredisconnect)的 callback一致。缺省时，表示注销所有已注册事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      this.context.off('preDisconnect');
    } catch (err) {
      console.error(`Failed to unRegister. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## onPreDisconnect

```TypeScript
onPreDisconnect(callback: Callback<void>): void
```

Register accessibilityExtensionAbility disconnect callback.

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionContext-onPreDisconnect(callback: Callback<void>): void--><!--Device-AccessibilityExtensionContext-onPreDisconnect(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | Indicates the callback function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import {
  AccessibilityEventInfo, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext): void {
    this.context = context;
  }

  onStop(): void {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEventInfo): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      this.context.onPreDisconnect(() => {
        console.info(`To do something before accessibilityExtension disconnect.`);
      });
    } catch (err: BusinessError) {
      console.error(`Failed to register, code is ${err.code}, message is ${err.message}`);
    }
  }
}
```

## on('preDisconnect')

```TypeScript
on(type: 'preDisconnect', callback: Callback<void>): void
```

向无障碍服务注册回调函数，在无障碍服务关闭该辅助功能扩展服务前会执行该回调函数。使用callback异步回调。 此注册函数需要与[notifyDisconnect](#notifydisconnect)配合使用，如果不调用 [notifyDisconnect](#notifydisconnect)，则默认等待30秒后，辅助功能扩展服务会自动关闭。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionContext-on(type: 'preDisconnect', callback: Callback<void>): void--><!--Device-AccessibilityExtensionContext-on(type: 'preDisconnect', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'preDisconnect' | 是 | 监听事件名，固定为‘preDisconnect’，即辅助功能扩展服务即将关闭的事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数，在辅助功能扩展服务即将关闭时回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      this.context.on('preDisconnect', () => {
        console.info(`To do something before accessibilityExtension disconnect.`);
      });
    } catch (err) {
      console.error(`Failed to register. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## removeAccessibilityVirtualNodes

```TypeScript
removeAccessibilityVirtualNodes(elementId: long, windowId: int): Promise<OperateVirtualNodeResult>
```

删除新增的无障碍虚拟节点树。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityExtensionContext-removeAccessibilityVirtualNodes(elementId: long, windowId: int): Promise<OperateVirtualNodeResult>--><!--Device-AccessibilityExtensionContext-removeAccessibilityVirtualNodes(elementId: long, windowId: int): Promise<OperateVirtualNodeResult>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementId | long | 是 | 表示待删除的虚拟节点树所在的节点ID。 |
| windowId | int | 是 | 表示待删除的虚拟节点树所在的窗口ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OperateVirtualNodeResult](arkts-accessibility-accessibility-operatevirtualnoderesult-e-sys.md)&gt; | Promise对象，返回执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300000](../errorcode-accessibility.md#9300000-无障碍系统服务工作异常) | System abnormality.Possible causes: <br>1.Internal operation failed. <br>2.Failed to obtain the required service or client object (null pointer). <br>3.IPC communication failed. <br>4.Failed to obtain the accessibility service proxy. <br>5.Timed out while waiting for the result of an asynchronous operation. |

**示例**

```TypeScript
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext,
  OperateVirtualNodeResult
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let elementId: number = 10; // 请使用需要删除虚拟节点树的父节点ID。
    let windowId: number = 10; // 请使用需要删除虚拟节点树的窗口ID。
    this.context.removeAccessibilityVirtualNodes(elementId, windowId).then((data: OperateVirtualNodeResult)=>{
      console.info(`removeAccessibilityVirtualNodes: elementId:${elementId} windowId:${windowId}, result:${data}`)
    }).catch((err: BusinessError) => {
      console.error(`failed to remove virtual nodes, Code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

## startAbility

```TypeScript
startAbility(want: Want): Promise<void>
```

拉起前台页面。使用Promise异步回调。

**起始版本：** 23

<!--Device-AccessibilityExtensionContext-startAbility(want: Want): Promise<void>--><!--Device-AccessibilityExtensionContext-startAbility(want: Want): Promise<void>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Want类型参数，传入需要启动的Ability的信息，如Ability名称、Bundle名称等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have the permission required to call the API. |

**示例**

```TypeScript
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let want: Want = {
      bundleName: 'com.huawei.hmos.photos',
      abilityName: 'com.huawei.hmos.photos.MainAbility'
    };

    this.context.startAbility(want).then(() => {
      console.info(`succeeded in starting ability`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to start ability. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## unholdRunningLockSync

```TypeScript
unholdRunningLockSync(): void
```

释放RunningLock锁，恢复自动灭屏。与[holdRunningLockSync](#holdrunninglocksync)配对使用。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

<!--Device-AccessibilityExtensionContext-unholdRunningLockSync(): void--><!--Device-AccessibilityExtensionContext-unholdRunningLockSync(): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext
} from '@kit.AccessibilityKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    try {
      this.context.unholdRunningLockSync();
    } catch (err) {
      console.error(`Failed to unhold RunningLock. Code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## updateAccessibilityElementProperty

```TypeScript
updateAccessibilityElementProperty(elementId: long, windowId: int, node: AccessibilityVirtualNode): Promise<OperateVirtualNodeResult>
```

修改无障碍节点属性。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityExtensionContext-updateAccessibilityElementProperty(elementId: long, windowId: int, node: AccessibilityVirtualNode): Promise<OperateVirtualNodeResult>--><!--Device-AccessibilityExtensionContext-updateAccessibilityElementProperty(elementId: long, windowId: int, node: AccessibilityVirtualNode): Promise<OperateVirtualNodeResult>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementId | long | 是 | 表示修改无障碍节点的节点ID。 |
| windowId | int | 是 | 表示修改无障碍节点的窗口ID。 |
| node | [AccessibilityVirtualNode](arkts-accessibility-accessibilityextensioncontext-accessibilityvirtualnode-i-sys.md) | 是 | 修改无障碍节点的属性值，可修改的属性包括： <br>accessibilityText，accessibilityGroup，accessibilityLevel，checkable，checked，selected，clickable，enabled， customComponentType。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OperateVirtualNodeResult](arkts-accessibility-accessibility-operatevirtualnoderesult-e-sys.md)&gt; | Promise对象，返回执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300000](../errorcode-accessibility.md#9300000-无障碍系统服务工作异常) | System abnormality.Possible causes: <br>1.Internal operation failed. <br>2.Failed to obtain the required service or client object (null pointer). <br>3.IPC communication failed. <br>4.Failed to obtain the accessibility service proxy. <br>5.Timed out while waiting for the result of an asynchronous operation. |

**示例**

```TypeScript
import {
  AccessibilityEvent, 
  AccessibilityExtensionContext,
  AccessibilityVirtualNode,
  OperateVirtualNodeResult
} from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AccessibilityManager {
  private static instance: AccessibilityManager;
  context?: AccessibilityExtensionContext;

  static getInstance(): AccessibilityManager {
    if (!AccessibilityManager.instance) {
      AccessibilityManager.instance = new AccessibilityManager();
    }
    return AccessibilityManager.instance;
  }

  onStart(context: AccessibilityExtensionContext) {
    this.context = context;
  }

  onStop() {
    this.context = undefined;
  }

  onEvent(accessibilityEvent: AccessibilityEvent): void {
    if (!this.context) {
      console.error('context is not available!');
      return;
    }

    let elementId: number = 10; // 请使用需要修改节点属性的节点ID。
    let windowId: number = 10; // 请使用需要修改节点属性的窗口ID。
    let accessibilityVirtualNode: AccessibilityVirtualNode = {
      virtualNodeId: 1,
      accessibilityText: "accessibilityTextNew"
    }
    this.context.updateAccessibilityElementProperty(elementId, windowId, accessibilityVirtualNode).then((data: OperateVirtualNodeResult)=>{
      console.info(`updateAccessibilityElementProperty: elementId:${elementId} windowId:${windowId}, result:${data}`)
    }).catch((err: BusinessError) => {
      console.error(`failed to update accessibility element property, Code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

