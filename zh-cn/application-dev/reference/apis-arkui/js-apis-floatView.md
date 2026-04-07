# @ohos.window.floatView (应用浮窗)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @betafringe007-->
<!--Designer: @zhoulin_-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

应用浮窗是悬浮在桌面/应用界面上的小型窗口，提供灵活的窗口管理能力。

本模块提供应用浮窗能力，包括判断设备是否支持应用浮窗功能、创建应用浮窗控制器以启动、更新或停止应用浮窗等。

当需要在小窗口中展示应用内容或提供快捷操作时，可使用本模块接口。

本模块接口可与闪控球联合使用，在绑定了的情况下用户点击可相互切换。

> **说明：**
>
> - 本模块首批接口从API version 26开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 针对系统能力SystemCapability.Window.SessionManager，请先使用[canIUse()](../common/js-apis-syscap.md#caniuse)接口判断当前设备是否支持此syscap及对应接口。
>
> - 本模块仅支持Stage模型。

## 导入模块

```ts
import { floatView } from '@kit.ArkUI';
```

## floatView.isFloatViewEnabled

isFloatViewEnabled(): boolean

判断当前设备是否支持应用浮窗功能。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型 | 说明 |
|------------|------------|
| boolean  | 当前设备是否支持应用浮窗功能。true表示支持，false则表示不支持。 |

**示例：**

```ts
let enable: boolean = floatView.isFloatViewEnabled();
console.info('Float view enabled is: ' + enable);
```

## floatView.create

create(config: FloatViewConfiguration): Promise&lt;FloatViewController&gt;

创建应用浮窗控制器，使用Promise异步回调。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| config | [FloatViewConfiguration](#floatviewconfiguration) | 是 | 创建应用浮窗控制器的参数。该参数不能为null或者undefined，并且构造该参数的context不能为null或者undefined，否则抛出401。其他参数异常情况抛出1300016，具体原因参考错误码详细介绍。 |

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;[FloatViewController](#floatviewcontroller)&gt; | Promise对象。返回当前创建的应用浮窗控制器。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 801 | Capability not supported. Possible cause: Call the API on unsupported device. |
| 1300002 | This window state is abnormal. Possible cause: 1. This window context is abnormal. 2. System error, such as a null pointer, insufficient memory or a JS engine exception. |
| 1300016 | Parameter error. Possible cause: Invalid template type. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

let floatViewController: floatView.FloatViewController | undefined = undefined;
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回的结果为UIAbilityContext
let ctx = this.getUIContext().getHostContext() as common.UIAbilityContext;
let config: floatView.FloatViewConfiguration = {
  context: ctx,
  templateType: floatView.FloatViewTemplateType.ROUNDED_RECTANGLE
};
try {
  floatView.create(config).then((data: floatView.FloatViewController) => {
    floatViewController = data;
    console.info(`Succeeded in creating float view controller. Data: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create float view controller. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to create float view controller. Cause:${e.code}, message:${e.message}`);
}
```

## floatView.bind

bind(floatViewController: FloatViewController, floatingBallController: FloatingBallController, floatingBallParams: FloatingBallParams): Promise&lt;void&gt;

绑定应用浮窗和闪控球。需要先创建[应用浮窗控制器](#floatviewcreate)和[闪控球控制器](js-apis-floatingball#floatingballcreate)，且均未启动。

> **说明：**
> - 绑定成功后，调用[floatViewController.start()](#start)或[floatingBallController.startFloatingBall](js-apis-floatingball#startfloatingball)均会同时创建应用浮窗窗口和闪控球窗口。但同一时刻仅展示其中一个窗口，展示顺序取决于先调用哪个控制器的启动接口。
> - 绑定成功后，应用浮窗窗口与闪控球窗口支持用户点击触发的互相切换。
> - 绑定成功后，调用任一控制器的停止接口会同时销毁应用浮窗窗口和闪控球窗口。

**需要权限：** ohos.permission.USE_FLOAT_BALL 和 ohos.permission.FLOAT_VIEW

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| floatViewController | [FloatViewController](#floatviewcontroller) | 是 | 应用浮窗控制器。 |
| floatingBallController | [FloatingBallController](js-apis-floatingBall.md#floatingballcontroller) | 是 | 闪控球控制器。 |
| floatingBallParams | [FloatingBallParams](js-apis-floatingBall.md#floatingballparams) | 是 | 闪控球参数。 |

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 201 | Permission verification failed. Possible cause: The application does not have the permission required to call the API. |
| 801 | Capability not supported on this device. Possible cause: Call api on unsupported device. |
| 1300019 | Wrong parameters for operating the floating ball. Possible cause: Invalid floating ball params. |
| 1300025 | The floatingBall state does not support this operation. Possible cause: 1.The floating ball has started but not stopped yet. 2.The floating ball controller has been bound. |
| 1300031 | The floatView state does not support this operation. Possible cause: 1.The float view has started but not stopped yet. 2.The float view controller has been bound. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { floatingBall } from '@kit.ArkUI';

let floatingBallController: floatingBall.FloatingBallController | undefined = undefined;
let floatViewController: floatView.FloatViewController | undefined = undefined;

// 创建应用浮窗控制器和闪控球控制器
// ...

let floatingBallParams: floatingBall.FloatingBallParams = {
  template: floatingBall.FloatingBallTemplate.EMPHATIC,
  title: 'title',
  content: 'content'
};

try {
  if (floatViewController && floatingBallController) {
    floatView.bind(floatViewController, floatingBallController, floatingBallParams).then(() => {
      console.info('Succeeded in binding float view and floating ball.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to bind float view and floating ball. Cause:${err.code}, message:${err.message}`);
    });
  }
} catch(e) {
  console.error(`Failed to bind float view and floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## floatView.unbind

unbind(floatViewController: FloatViewController, floatingBallController: FloatingBallController): Promise&lt;void&gt;

解绑应用浮窗和闪控球，需要在[应用浮窗控制器](#floatviewcreate)和[闪控球控制器](js-apis-floatingball#floatingballcreate)均停止后才可解绑。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| floatViewController | [FloatViewController](#floatviewcontroller) | 是 | 应用浮窗控制器。 |
| floatingBallController | [FloatingBallController](js-apis-floatingBall.md#floatingballcontroller) | 是 | 闪控球控制器。 |

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 801 | Capability not supported on this device. Possible cause: Call api on unsupported device. |
| 1300025 | The floating ball state does not support this operation. Possible cause: 1.The floating ball has started but not stopped yet. 2.The floatingBallController has not been bound. |
| 1300031 | The floatView state does not support this operation. Possible cause: 1.The float view has started but not stopped yet. 2.The floatViewController has not been bound. 3.The floatViewController and the floatingBallController are not bound together. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 使用绑定时传入的应用浮窗和闪控球控制器
  if (floatViewController && floatingBallController) {
    floatView.unbind(floatViewController, floatingBallController).then(() => {
      console.info('Succeeded in unbinding float view and floating ball.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to unbind float view and floating ball. Cause:${err.code}, message:${err.message}`);
    });
  }
} catch(e) {
  console.error(`Failed to unbind float view and floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## floatView.getFloatViewLimits

getFloatViewLimits(): FloatViewLimits

获取当前应用浮窗窗口的限制，单位为px。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型 | 说明 |
|------------|------------|
| [FloatViewLimits](#floatviewlimits) | 返回应用浮窗窗口的限制，包括最大尺寸、最小尺寸和宽高比限制范围。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 801 | Capability not supported. Possible cause: Call the API on unsupported device. |
| 1300002 | This window state is abnormal. Possible cause: System error, such as a null pointer, insufficient memory or a JS engine exception. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |

**示例：**

```ts
let limits: floatView.FloatViewLimits = floatView.getFloatViewLimits();
console.info('Float view limits: ' + JSON.stringify(limits));
```

## FloatViewConfiguration

创建应用浮窗控制器时需要提供的参数配置。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
|------------|------------|------------|------------|------------|
| context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | 否 | 否 | 表示上下文环境。|
| templateType | [FloatViewTemplateType](#floatviewtemplatetype) | 否 | 否 | 应用浮窗的模板类型。|

## FloatViewController

应用浮窗控制器实例，用于启动、停止应用浮窗以及注册回调等操作。

下列API示例中都需先使用[floatView.create()](#floatviewcreate)方法获取到应用浮窗控制器实例（即floatViewController），再通过此实例调用对应方法。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

### setUIContext

setUIContext(path: string, storage?: LocalStorage): Promise&lt;void&gt;

设置应用浮窗的UI内容。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| path | string | 是 | 要加载到窗口中的页面内容的路径，该路径需添加到工程的main_pages.json文件中。不支持相对路径写法，需与main_pages.json中的src取值保持一致。 |
| storage | [LocalStorage](../../ui/state-management/arkts-localstorage.md) | 否 | 窗口加载的内容实例内共享的数据对象。 |

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300016 | Parameter error. Possible causes: Invalid path. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  floatViewController.setUIContext('pages/Index').then(() => {
    console.info('Succeeded in setting UI context.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set UI context. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to set UI context. Cause:${e.code}, message:${e.message}`);
}
```

### setWindowSize

setWindowSize(size: Size): Promise&lt;void&gt;

设置应用浮窗窗口大小。建议先调用[getFloatViewLimits](#floatviewgetfloatviewlimits)接口获取推荐的宽高范围和宽高比范围，再根据推荐值调用本接口。窗口实际大小变化可通过[onRectChange](#onrectchange)接口监听。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| size | [Size](arkts-apis-window-i.md#size7) | 是 | 表示窗口的大小。建议大小满足[getFloatViewLimits](#floatviewgetfloatviewlimits)接口返回的限制。 |

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |
| 1300016 | Parameter error. Possible cause: The value of the size is less than or equal to 0. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import window from '@ohos.window';

let size: window.Size = {
  width: 400,
  height: 600
};

try {
  floatViewController.setWindowSize(size).then(() => {
    console.info('Succeeded in setting window size.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set window size. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to set window size. Cause:${e.code}, message:${e.message}`);
}
```

### start

start(): Promise&lt;void&gt;

启动应用浮窗窗口。接口返回不表示start流程结束，需要通过[onStateChange](#onstatechange)接口监听到STARTED回调时判断启动成功。

**需要权限：** ohos.permission.FLOAT_VIEW

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 201 | Permission verification failed, usually returned by VerifyAccessToken. |
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |
| 1300030 | Repeated operations on the float view. Possible cause: The float view is starting or has already started. |
| 1300031 | The float view state does not support this operation. Possible cause: The float view is stopping. |
| 1300033 | Failed to start float view. Possible causes: 1. Start multiple float views. 2. The application does not have any foreground windows. |
| 1300034 | This operation conflicts with other floating windows. Possible cause: App has already started floating ball or pip window. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  floatViewController.start().then(() => {
    console.info('Succeeded in starting float view.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to start float view. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to start float view. Cause:${e.code}, message:${e.message}`);
}
```

### stop

stop(): Promise&lt;void&gt;

停止应用浮窗窗口。接口返回不表示stop流程结束，需要通过[onStateChange](#onstatechange)接口监听到STOPPED回调时判断停止成功。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |
| 1300030 | Repeated operations on the float view. Possible cause: The float view is stopping or has already stopped. |
| 1300031 | This operation is not supported on the float view in the current state. Possible cause: The float view window is not started. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  floatViewController.stop().then(() => {
    console.info('Succeeded in stopping float view.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to stop float view. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to stop float view. Cause:${e.code}, message:${e.message}`);
}
```

### setFloatViewVisibilityInApp

setFloatViewVisibilityInApp(isVisible: boolean): Promise&lt;void&gt;

设置应用在前台时应用浮窗窗口是否可见。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| isVisible | boolean | 是 | 应用在前台时应用浮窗是否可见，true表示可见，false表示不可见。 |

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  floatViewController.setFloatViewVisibilityInApp(true).then(() => {
    console.info('Succeeded in setting float view visibility in app.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set float view visibility in app. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to set float view visibility in app. Cause:${e.code}, message:${e.message}`);
}
```

### restoreMainWindow

restoreMainWindow(wantParameters?: Record&lt;string, Object&gt;): Promise&lt;void&gt;

恢复应用浮窗的主窗口到前台。此接口只能在应用浮窗窗口被点击后使用。当主窗口处于PAUSED生命周期或当前系统处于多任务中心时，调用接口将抛出错误码1300032。如果主窗口已处于前台时调用，将抬升主窗口层级。

**系统能力：** SystemCapability.Window.SessionManager

**只支持Stage模型。**

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| wantParameters | Record&lt;string, Object&gt; | 否 | 恢复应用浮窗的主窗口时会给主窗口传递的自定义参数，主窗口会在触发[onNewWant](../apis-ability-kit/js-apis-app-ability-abilityLifecycleCallback.md#onnewwant12)回调时收到。默认值为空，代表不向主窗传入任何自定义参数。 |

**返回值：**

| 类型 | 说明 |
|------------|------------|
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300003 | This window manager service works abnormally. Possible cause: Internal IPC error. |
| 1300031 | This operation is not supported on the float view in the current state. Possible cause: The float view window is not started when restoring. |
| 1300032 | Failed to restore the main window. Possible cause: 1. User has never clicked the float view window before restore. 2. The float view window is not in the foreground. 3. The main window is in PAUSED lifecycle state. 4. The main window is in background during recent. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 应用浮窗状态需是STARTED
try {
  floatViewController.restoreMainWindow().then(() => {
    console.info('Succeeded in restoring main window.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to restore main window. Cause:${err.code}, message:${err.message}`);
  });
} catch(e) {
  console.error(`Failed to restore main window. Cause:${e.code}, message:${e.message}`);
}
```

### getWindowProperties

getWindowProperties(): FloatViewProperties

获取应用浮窗窗口的属性。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型 | 说明 |
|------------|------------|
| [FloatViewProperties](#floatviewproperties) | 返回应用浮窗窗口的属性。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300031 | This operation is not supported on the float view in the current state. Possible cause: The float view window has not started, has stopped, or is in an error state. |

**示例：**

```ts
try {
  let properties: floatView.FloatViewProperties = floatViewController.getWindowProperties();
  console.info('Float view properties: ' + JSON.stringify(properties));
} catch(e) {
  console.error(`Failed to get window properties. Cause:${e.code}, message:${e.message}`);
}
```

### onStateChange

onStateChange(callback: Callback&lt;FloatViewStateChangeInfo&gt;): void

注册应用浮窗状态变化的监听事件。不再使用时，取消监听以避免内存泄漏。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| callback | Callback&lt;[FloatViewStateChangeInfo](#floatviewstatechangeinfo)&gt; | 是 | 回调函数。返回当前的应用浮窗状态变化信息。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300030 | Repeated operations on the float view. Possible cause: The callback has already registered. |

**示例：**

```ts
let onStateChange = (info: floatView.FloatViewStateChangeInfo) => {
  console.info('Float view stateChange: ' + JSON.stringify(info));
};
try {
  floatViewController.onStateChange(onStateChange);
} catch(e) {
  console.error(`Failed to on stateChange float view. Cause:${e.code}, message:${e.message}`);
}
```

### offStateChange

offStateChange(callback?: Callback&lt;FloatViewStateChangeInfo&gt;): void

取消应用浮窗状态变化的监听事件。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| callback | Callback&lt;[FloatViewStateChangeInfo](#floatviewstatechangeinfo)&gt; | 否 | 回调函数。返回当前的应用浮窗状态变化信息。若传入参数，则停止该监听。若未传入参数，则停止所有应用浮窗状态变化的监听。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |

**示例：**

```ts
let onStateChange = (info: floatView.FloatViewStateChangeInfo) => {
  console.info('Float view stateChange: ' + JSON.stringify(info));
};
try {
  floatViewController.offStateChange(onStateChange);
} catch(e) {
  console.error(`Failed to off stateChange float view. Cause:${e.code}, message:${e.message}`);
}
```

### onRectChange

onRectChange(callback: Callback&lt;FloatViewRectChangeInfo&gt;): void

注册应用浮窗矩形区域（位置和大小）变化的监听事件。不再使用时，取消监听以避免内存泄漏。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| callback | Callback&lt;[FloatViewRectChangeInfo](#floatviewrectchangeinfo)&gt; | 是 | 回调函数。返回当前的应用浮窗矩形区域变化信息。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300030 | Repeated operations on the float view. Possible cause: The callback has already registered. |

**示例：**

```ts
let onRectChange = (info: floatView.FloatViewRectChangeInfo) => {
  console.info('Float view rectChange: ' + JSON.stringify(info));
};
try {
  floatViewController.onRectChange(onRectChange);
} catch(e) {
  console.error(`Failed to on rectChange float view. Cause:${e.code}, message:${e.message}`);
}
```

### offRectChange

offRectChange(callback?: Callback&lt;FloatViewRectChangeInfo&gt;): void

取消应用浮窗矩形区域变化的监听事件。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| callback | Callback&lt;[FloatViewRectChangeInfo](#floatviewrectchangeinfo)&gt; | 否 | 回调函数。返回当前的应用浮窗矩形区域变化信息。若传入参数，则停止该监听。若未传入参数，则停止所有应用浮窗矩形区域变化的监听。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |

**示例：**

```ts
let onRectChange = (info: floatView.FloatViewRectChangeInfo) => {
  console.info('Float view rectChange: ' + JSON.stringify(info));
};
try {
  floatViewController.offRectChange(onRectChange);
} catch(e) {
  console.error(`Failed to off rectChange float view. Cause:${e.code}, message:${e.message}`);
}
```

### onLimitsChange

onLimitsChange(callback: Callback&lt;FloatViewLimits&gt;): void

注册应用浮窗限制变化的监听事件。不再使用时，取消监听以避免内存泄漏。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| callback | Callback&lt;[FloatViewLimits](#floatviewlimits)&gt; | 是 | 回调函数。返回当前的应用浮窗限制变化信息。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |
| 1300030 | Repeated operations on the float view. Possible cause: The callback has already registered. |

**示例：**

```ts
let onLimitsChange = (limits: floatView.FloatViewLimits) => {
  console.info('Float view limitsChange: ' + JSON.stringify(limits));
};
try {
  floatViewController.onLimitsChange(onLimitsChange);
} catch(e) {
  console.error(`Failed to on limitsChange float view. Cause:${e.code}, message:${e.message}`);
}
```

### offLimitsChange

offLimitsChange(callback?: Callback&lt;FloatViewLimits&gt;): void

取消应用浮窗限制变化的监听事件。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|------------|------------|------------|------------|
| callback | Callback&lt;[FloatViewLimits](#floatviewlimits)&gt; | 否 | 回调函数。返回当前的应用浮窗限制变化信息。若传入参数，则停止该监听。若未传入参数，则停止所有应用浮窗限制变化的监听。 |

**错误码：**

以下错误码的详细介绍请参见[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息 |
|------------|------------|
| 1300002 | This window state is abnormal. Possible cause: The float view controller object is null. |

**示例：**

```ts
let onLimitsChange = (limits: floatView.FloatViewLimits) => {
  console.info('Float view limitsChange: ' + JSON.stringify(limits));
};
try {
  floatViewController.offLimitsChange(onLimitsChange);
} catch(e) {
  console.error(`Failed to off limitsChange float view. Cause:${e.code}, message:${e.message}`);
}
```

## FloatViewTemplateType

应用浮窗模板类型的枚举。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 值 | 说明 |
|------------|------------|------------|
| ROUNDED_RECTANGLE | 0 | 圆角矩形。 |

## FloatViewProperties

应用浮窗窗口的属性。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
|------------|------------|------------|------------|------------|
| windowId | number | 否 | 否 | 应用浮窗窗口ID。 |
| displayId | number | 否 | 否 | 应用浮窗所在屏幕ID。 |
| windowRect | [Rect](arkts-apis-window-i.md#rect7) | 否 | 否 | 应用浮窗窗口矩形区域。 |
| windowScale | number | 否 | 否 | 应用浮窗窗口缩放比例。 |
| titleBarRect | [Rect](arkts-apis-window-i.md#rect7) | 否 | 否 | 应用浮窗标题栏矩形区域。 |
| inSidebar | boolean | 否 | 否 | 应用浮窗是否在侧边栏中。 |

## RatioLimit

应用浮窗的比例限制。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
|------------|------------|------------|------------|------------|
| minRatio | number | 否 | 否 | 应用浮窗的宽高比最小值。 |
| maxRatio | number | 否 | 否 | 应用浮窗的宽高比最大值。 |

## FloatViewLimits

应用浮窗窗口的限制。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
|------------|------------|------------|------------|------------|
| minSize | [Size](arkts-apis-window-i.md#size7) | 否 | 否 | 应用浮窗的最小尺寸。 |
| maxSize | [Size](arkts-apis-window-i.md#size7) | 否 | 否 | 应用浮窗的最大尺寸。 |
| ratioLimits | Array&lt;[RatioLimit](#ratiolimit)&gt; | 否 | 否 | 应用浮窗的宽高比限制。宽高比比值由窗口矩形区域的宽除以高获得 |

## FloatViewStateChangeInfo

应用浮窗状态变化信息。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
|------------|------------|------------|------------|------------|
| state | [FloatViewState](#floatviewstate) | 否 | 否 | 应用浮窗的状态。 |
| stopReason | string | 否 | 否 | 应用浮窗停止的原因。该参数仅在状态为FloatViewState.STOPPED时有效，在其他状态下默认为空字符串（""）。停止原因和对应含义如下：<br/>"APP_STOP"：应用主动停止<br/>"APP_KILL_STOP"：应用进程被杀死后停止<br/>"STOP_IN_SIDEBAR"：在侧边栏被关闭<br/>"TITLE_BAR_CLICK_STOP"：标题栏点击关闭按钮<br/>"DUMPSTER_STOP"：拖入垃圾桶停止<br/>"REPLACE_STOP"：被其他应用浮窗挤占<br/>"FLOATING_BALL_STOP"：绑定状态下跟随闪控球停止 |

## FloatViewState

应用浮窗状态的枚举。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 值 | 说明 |
|------------|------------|------------|
| STARTED | 1 | 应用浮窗已启动并显示。 |
| HIDDEN | 2 | 应用浮窗已隐藏。上滑进入多任务界面时触发，或设置了应用在前台时隐藏且应用处于前台时触发 |
| STOPPED | 3 | 应用浮窗已停止。 |
| IN_SIDEBAR | 4 | 应用浮窗在侧边栏中。 |
| IN_FLOATING_BALL | 5 | 应用浮窗切换为闪控球。 |
| ERROR | 6 | 应用浮窗处于错误状态。 |

## FloatViewRectChangeInfo

应用浮窗矩形区域变化信息。

**系统能力：** SystemCapability.Window.SessionManager

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
|------------|------------|------------|------------|------------|
| windowRect | [Rect](arkts-apis-window-i.md#rect7) | 否 | 否 | 应用浮窗窗口矩形区域。 |
| windowScale | number | 否 | 否 | 应用浮窗窗口缩放比例。 |
| reason | string | 否 | 否 | 应用浮窗矩形区域变化的原因。原因和对应含义如下：<br/>"POSITION_CHANGE"：位置变化<br/>"SIZE_CHANGE"：大小变化<br/>"RECT_CHANGE"：位置大小同时变化。 |
