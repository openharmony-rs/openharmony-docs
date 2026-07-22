# FloatViewController

标准悬浮窗控制器实例。用于启动、停止标准悬浮窗以及注册回调等操作。

下列API示例中都需先使用[floatView.create()](arkts-arkui-floatview-create-f.md#create)方法获取到标准悬浮窗控制器实例（即floatViewController），再通过此实例调用对应方法。

**起始版本：** 26.0.0

<!--Device-floatView-interface FloatViewController--><!--Device-floatView-interface FloatViewController-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## getWindowProperties

```TypeScript
getWindowProperties(): FloatViewProperties
```

获取标准悬浮窗窗口的属性。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-getWindowProperties(): FloatViewProperties--><!--Device-FloatViewController-getWindowProperties(): FloatViewProperties-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FloatViewProperties](arkts-arkui-floatview-floatviewproperties-i.md) | 返回标准悬浮窗窗口的属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300031](../errorcode-window.md#1300031-闪控窗状态不支持该操作) | This operation is not supported on the float view in the current state.Possible cause: The float view window has not started, has stopped, or is in an error state. |

**示例：**

```TypeScript
try {
  // 获取闪控窗窗口属性
  let properties: floatView.FloatViewProperties | undefined = this.floatViewController?.getWindowProperties();
  console.info('Float view properties: ' + JSON.stringify(properties));
} catch (e) {
  console.error(`Failed to get window properties. Cause:${e.code}, message:${e.message}`);
}

```

## offLimitsChange

```TypeScript
offLimitsChange(callback?: Callback<FloatViewLimits>): void
```

取消标准悬浮窗限制变化的监听事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-offLimitsChange(callback?: Callback<FloatViewLimits>): void--><!--Device-FloatViewController-offLimitsChange(callback?: Callback<FloatViewLimits>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;FloatViewLimits&gt; | 否 | 回调函数。返回当前的标准悬浮窗限制变化信息。若传入参数，则停止该监听。若未传入参数，则停止所有标准悬浮窗限制变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |

**示例：**

```TypeScript
// 定义限制变化回调函数
let onLimitsChange = (limits: floatView.FloatViewLimits) => {
  console.info('Float view limitsChange: ' + JSON.stringify(limits));
};
try {
  // 取消闪控窗限制变化监听
  this.floatViewController?.offLimitsChange(onLimitsChange);
} catch (e) {
  console.error(`Failed to off limitsChange float view. Cause:${e.code}, message:${e.message}`);
}

```

## offRectChange

```TypeScript
offRectChange(callback?: Callback<FloatViewRectChangeInfo>): void
```

取消标准悬浮窗矩形区域变化的监听事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-offRectChange(callback?: Callback<FloatViewRectChangeInfo>): void--><!--Device-FloatViewController-offRectChange(callback?: Callback<FloatViewRectChangeInfo>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;FloatViewRectChangeInfo&gt; | 否 | 回调函数。返回当前的标准悬浮窗矩形区域变化信息。若传入参数，则停止该监听。若未传入参数，则停止所有标准悬浮窗矩形区域变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |

**示例：**

```TypeScript
// 定义矩形区域变化回调函数
let onRectChange = (info: floatView.FloatViewRectChangeInfo) => {
  console.info('Float view rectChange: ' + JSON.stringify(info));
};
try {
  // 取消闪控窗矩形区域变化监听
  this.floatViewController?.offRectChange(onRectChange);
} catch (e) {
  console.error(`Failed to off rectChange float view. Cause:${e.code}, message:${e.message}`);
}

```

## offStateChange

```TypeScript
offStateChange(callback?: Callback<FloatViewStateChangeInfo>): void
```

取消标准悬浮窗状态变化的监听事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-offStateChange(callback?: Callback<FloatViewStateChangeInfo>): void--><!--Device-FloatViewController-offStateChange(callback?: Callback<FloatViewStateChangeInfo>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;FloatViewStateChangeInfo&gt; | 否 | 回调函数。返回当前的标准悬浮窗状态变化信息。若传入参数，则停止该监听。若未传入参数，则停止所有标准悬浮窗状态变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |

**示例：**

```TypeScript
// 定义状态变化回调函数
let onStateChange = (info: floatView.FloatViewStateChangeInfo) => {
  console.info('Float view stateChange: ' + JSON.stringify(info));
};
try {
  // 取消闪控窗状态变化监听
  this.floatViewController?.offStateChange(onStateChange);
} catch (e) {
  console.error(`Failed to off stateChange float view. Cause:${e.code}, message:${e.message}`);
}

```

## onLimitsChange

```TypeScript
onLimitsChange(callback: Callback<FloatViewLimits>): void
```

注册标准悬浮窗限制变化的监听事件，当限制规格变化时触发回调，例如设备折叠或者展开。不再使用时，取消监听以避免内存泄漏。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-onLimitsChange(callback: Callback<FloatViewLimits>): void--><!--Device-FloatViewController-onLimitsChange(callback: Callback<FloatViewLimits>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;FloatViewLimits&gt; | 是 | 回调函数。返回当前的标准悬浮窗限制变化信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300030](../errorcode-window.md#1300030-重复操作闪控窗) | Repeated operations on the float view. Possible cause:The callback has already registered. |

**示例：**

```TypeScript
// 定义限制变化回调函数
let onLimitsChange = (limits: floatView.FloatViewLimits) => {
  console.info('Float view limitsChange: ' + JSON.stringify(limits));
};
try {
  // 注册闪控窗限制变化监听
  this.floatViewController?.onLimitsChange(onLimitsChange);
} catch (e) {
  console.error(`Failed to on limitsChange float view. Cause:${e.code}, message:${e.message}`);
}

```

## onRectChange

```TypeScript
onRectChange(callback: Callback<FloatViewRectChangeInfo>): void
```

注册标准悬浮窗矩形区域（位置和大小）变化的监听事件。不再使用时，取消监听以避免内存泄漏。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-onRectChange(callback: Callback<FloatViewRectChangeInfo>): void--><!--Device-FloatViewController-onRectChange(callback: Callback<FloatViewRectChangeInfo>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;FloatViewRectChangeInfo&gt; | 是 | 回调函数。返回当前的标准悬浮窗矩形区域变化信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300030](../errorcode-window.md#1300030-重复操作闪控窗) | Repeated operations on the float view. Possible cause:The callback has already registered. |

**示例：**

```TypeScript
// 定义矩形区域变化回调函数
let onRectChange = (info: floatView.FloatViewRectChangeInfo) => {
  console.info('Float view rectChange: ' + JSON.stringify(info));
};
try {
  // 注册闪控窗矩形区域变化监听
  this.floatViewController?.onRectChange(onRectChange);
} catch (e) {
  console.error(`Failed to on rectChange float view. Cause:${e.code}, message:${e.message}`);
}

```

## onStateChange

```TypeScript
onStateChange(callback: Callback<FloatViewStateChangeInfo>): void
```

注册标准悬浮窗状态变化的监听事件。不再使用时，取消监听以避免内存泄漏。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-onStateChange(callback: Callback<FloatViewStateChangeInfo>): void--><!--Device-FloatViewController-onStateChange(callback: Callback<FloatViewStateChangeInfo>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;FloatViewStateChangeInfo&gt; | 是 | 回调函数。返回当前的标准悬浮窗状态变化信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300030](../errorcode-window.md#1300030-重复操作闪控窗) | Repeated operations on the float view. Possible cause:The callback has already registered. |

**示例：**

```TypeScript
// 定义状态变化回调函数
let onStateChange = (info: floatView.FloatViewStateChangeInfo) => {
  console.info('Float view stateChange: ' + JSON.stringify(info));
};
try {
  // 注册闪控窗状态变化监听
  this.floatViewController?.onStateChange(onStateChange);
} catch (e) {
  console.error(`Failed to on stateChange float view. Cause:${e.code}, message:${e.message}`);
}

```

## restoreMainWindow

```TypeScript
restoreMainWindow(wantParameters?: Record<string, Object>): Promise<void>
```

恢复标准悬浮窗的主窗口到前台显示。如果主窗口已处于前台时调用，将抬升主窗口层级。此接口只能在标准悬浮窗窗口被点击后使用。当主窗口处于PAUSED生命周期或处于多任务状态时，调用接口将抛出错误码1300032。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-restoreMainWindow(wantParameters?: Record<string, Object>): Promise<void>--><!--Device-FloatViewController-restoreMainWindow(wantParameters?: Record<string, Object>): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wantParameters | Record&lt;string, Object&gt; | 否 | 恢复标准悬浮窗的主窗口时会给主窗口传递的自定义参数，主窗口会在触发[onNewWant](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-abilitylifecyclecallback-abilitylifecyclecallback-c.md#onabilitycreate)回调时收到。默认值为空，代表不向主窗传入任何自定义参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause:Internal IPC error. |
| [1300031](../errorcode-window.md#1300031-闪控窗状态不支持该操作) | This operation is not supported on the float view in the current state.Possible cause: The float view window is not started when restoring. |
| [1300032](../errorcode-window.md#1300032-恢复主窗口失败) | Failed to restore the main window. Possible cause:1. User has never clicked the float view window before restore.2. The float view window is not in the foreground.3. The main window is in PAUSED lifecycle state.4. The main window is in background during recent. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView } from '@kit.ArkUI';

// 创建恢复主窗口的参数
let param: Record<string, Object> = {
  'info': 'helloworld',
};
// 闪控窗状态需是STARTED
try {
  // 恢复闪控窗的主窗口到前台显示
  this.floatViewController?.restoreMainWindow(param).then(() => {
    console.info('Succeeded in restoring main window.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to restore main window. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to restore main window. Cause:${e.code}, message:${e.message}`);
}

```

## setFloatViewVisibilityInApp

```TypeScript
setFloatViewVisibilityInApp(isVisible: boolean): Promise<void>
```

设置应用在前台时标准悬浮窗窗口是否可见。使用Promise异步回调。

创建标准悬浮窗后未调用此接口前，默认其在应用处于前台时为可见状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-setFloatViewVisibilityInApp(isVisible: boolean): Promise<void>--><!--Device-FloatViewController-setFloatViewVisibilityInApp(isVisible: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isVisible | boolean | 是 | 应用在前台时标准悬浮窗是否可见，true表示可见，false表示不可见。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause:Internal IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView } from '@kit.ArkUI';

try {
  // 设置应用在前台时闪控窗可见
  this.floatViewController?.setFloatViewVisibilityInApp(true).then(() => {
    console.info('Succeeded in setting float view visibility in app.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to set float view visibility in app. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to set float view visibility in app. Cause:${e.code}, message:${e.message}`);
}

```

## setUIContext

```TypeScript
setUIContext(path: string, storage?: LocalStorage): Promise<void>
```

根据当前工程中指定的页面路径为标准悬浮窗加载具体页面内容，通过LocalStorage传递状态属性至加载页面。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-setUIContext(path: string, storage?: LocalStorage): Promise<void>--><!--Device-FloatViewController-setUIContext(path: string, storage?: LocalStorage): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 要加载到窗口中的页面内容的路径，该路径需添加到工程的main_pages.json文件中。不支持相对路径写法，需与main_pages.json中的src取值保持一致。 |
| storage | [LocalStorage](arkts-arkui-localstorage-c.md) | 否 | 页面级UI状态存储单元，用于为加载到窗口的页面内容传递状态属性。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible causes: Invalid path. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView } from '@kit.ArkUI';

try {
  // floatViewController需通过floatView.create()获取，详见floatView.create()示例
  // 设置闪控窗的页面内容路径
  this.floatViewController?.setUIContext('pages/Index').then(() => {
    console.info('Succeeded in setting UI context.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to set UI context. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to set UI context. Cause:${e.code}, message:${e.message}`);
}

```

## setUIContextByName

```TypeScript
setUIContextByName(name: string, storage?: LocalStorage): Promise<void>
```

根据指定路由页面名称为当前窗口加载[命名路由](../../../ui/arkts-routing.md#命名路由)页面，通过LocalStorage传递状态属性至加载页面，使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-setUIContextByName(name: string, storage?: LocalStorage): Promise<void>--><!--Device-FloatViewController-setUIContextByName(name: string, storage?: LocalStorage): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 命名路由页面的名称。 |
| storage | [LocalStorage](arkts-arkui-localstorage-c.md) | 否 | 页面级UI状态存储单元，用于为加载到窗口的页面内容传递状态属性。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible causes: Invalid name. |

**示例：**

```TypeScript
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { entryName } from './Hello'; // 导入命名路由页面
import { floatView } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private floatViewController: floatView.FloatViewController | undefined = undefined;
  // 创建控制器
  // ...
  public setUIContextByName(): void {
    try {
      // 根据命名路由名称设置闪控窗的页面内容
      this.floatViewController?.setUIContextByName(entryName).then(() => {
        console.info('Succeeded in loading the content.');
      }).catch((err: BusinessError): void => {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (e) {
      console.error(`Failed to load the content. Cause code: ${e.code}, message: ${e.message}`);
    }
  }
}

```

```TypeScript
// Hello.ets
export const entryName : string = 'Hello';
@Entry({routeName: entryName, useSharedStorage: true})
@Component
export struct Hello {
  @State message: string = 'Hello World'
  build() {
    Row() {
      Column() {
        Text(this.message)
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

## setWindowSize

```TypeScript
setWindowSize(size: window.Size): Promise<void>
```

设置标准悬浮窗窗口大小。建议先调用[getFloatViewLimits](arkts-arkui-floatview-getfloatviewlimits-f.md#getfloatviewlimits)接口获取推荐的宽高范围和宽高比范围，再根据推荐值调用本接口。窗口实际大小变化可通过[onRectChange](floatView.FloatViewController.onRectChange(callback: Callback<FloatViewRectChangeInfo>))接口监听。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-setWindowSize(size: window.Size): Promise<void>--><!--Device-FloatViewController-setWindowSize(size: window.Size): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | window.Size | 是 | 表示窗口的大小。建议大小满足[getFloatViewLimits](arkts-arkui-floatview-getfloatviewlimits-f.md#getfloatviewlimits)接口返回的限制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause:Internal IPC error. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error.Possible cause: The value of the size is less than or equal to 0. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView, window } from '@kit.ArkUI';

// 设置窗口大小
let size: window.Size = {
  width: 400,
  height: 600
};
try {
  // 设置闪控窗窗口大小
  this.floatViewController?.setWindowSize(size).then(() => {
    console.info('Succeeded in setting window size.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to set window size. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to set window size. Cause:${e.code}, message:${e.message}`);
}

```

## start

```TypeScript
start(): Promise<void>
```

启动标准悬浮窗窗口。接口返回不表示start流程结束，需要通过[onStateChange](floatView.FloatViewController.onStateChange(callback: Callback<FloatViewStateChangeInfo>))接口监听到STARTED回调时判断启动成功。建议在调用[setUIContext()](arkts-arkui-floatview-floatviewcontroller-i.md#setuicontext)或[setUIContextByName()](arkts-arkui-floatview-floatviewcontroller-i.md#setuicontextbyname)后调用start()。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.FLOAT_VIEW

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-start(): Promise<void>--><!--Device-FloatViewController-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. Possible cause:The application does not have the permission required to call the API. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause:Internal IPC error. |
| [1300030](../errorcode-window.md#1300030-重复操作闪控窗) | Repeated operations on the float view. Possible cause:The float view is starting or has already started. |
| [1300031](../errorcode-window.md#1300031-闪控窗状态不支持该操作) | The float view state does not support this operation. Possible cause:The float view is stopping. |
| [1300033](../errorcode-window.md#1300033-启动闪控窗失败) | Failed to start float view. Possible causes:1. Start multiple float views.2. The main window of context is not foreground. |
| [1300034](../errorcode-window.md#1300034-闪控窗与其他悬浮窗口操作冲突) | This operation conflicts with other floating windows. Possible cause:App has already started floating ball or pip window. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView } from '@kit.ArkUI';

try {
  // 启动闪控窗
  this.floatViewController?.start().then(() => {
    console.info('Succeeded in starting float view.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to start float view. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to start float view. Cause:${e.code}, message:${e.message}`);
}

```

## stop

```TypeScript
stop(): Promise<void>
```

停止标准悬浮窗窗口。接口返回不表示stop流程结束，需要通过[onStateChange](floatView.FloatViewController.onStateChange(callback: Callback<FloatViewStateChangeInfo>))接口监听到STOPPED回调时判断停止成功。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-stop(): Promise<void>--><!--Device-FloatViewController-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause:Internal IPC error. |
| [1300030](../errorcode-window.md#1300030-重复操作闪控窗) | Repeated operations on the float view. Possible cause:The float view is stopping or has already stopped. |
| [1300031](../errorcode-window.md#1300031-闪控窗状态不支持该操作) | This operation is not supported on the float view in the current state.Possible cause: The float view window is not started. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView } from '@kit.ArkUI';

try {
  // 停止闪控窗
  this.floatViewController?.stop().then(() => {
    console.info('Succeeded in stopping float view.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to stop float view. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to stop float view. Cause:${e.code}, message:${e.message}`);
}

```

## switchTemplate

```TypeScript
switchTemplate(templateProperty: TemplateProperty): Promise<void>
```

切换标准悬浮窗的模板并改变其窗口尺寸。建议先调用[getFloatViewLimits](arkts-arkui-floatview-getfloatviewlimits-f.md#getfloatviewlimits)接口获取目标模板类型推荐的宽高范围和宽高比范围，再根据推荐值调用本接口。窗口实际大小变化可通过[onRectChange](floatView.FloatViewController.onRectChange(callback: Callback<FloatViewRectChangeInfo>))接口监听。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewController-switchTemplate(templateProperty: TemplateProperty): Promise<void>--><!--Device-FloatViewController-switchTemplate(templateProperty: TemplateProperty): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| templateProperty | [TemplateProperty](arkts-arkui-floatview-templateproperty-i.md) | 是 | 表示需要切换的窗口模板类型及大小。建议大小满足[getFloatViewLimits](arkts-arkui-floatview-getfloatviewlimits-f.md#getfloatviewlimits)接口返回的限制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:The float view controller object is null. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause:Internal IPC error. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible cause:1. Invalid template type.2. The value of the size is less than or equal to 0. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { floatView, window } from '@kit.ArkUI';

// 设置新窗口大小
let newSize: window.Size = {
  width: 800,
  height: 100
};
// 设置模板属性
let templateProperty: floatView.TemplateProperty = {
  templateType: floatView.FloatViewTemplateType.HORIZONTAL_BAR,
  size: newSize
}
try {
  // 切换闪控窗模板并改变窗口尺寸
  this.floatViewController?.switchTemplate(templateProperty).then(() => {
    console.info('Succeeded in switching window type and size.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to switch window type and size. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to switch window type and size. Cause:${e.code}, message:${e.message}`);
}

```

