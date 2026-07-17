# Window

当前窗口实例，窗口管理器管理的基本单元。

下列API示例中都需先使用[getLastWindow()](arkts-arkui-window-getlastwindow-f.md#getlastwindow-1)、[createWindow()](arkts-arkui-window-createwindow-f.md#createwindow-1)、[findWindow()](arkts-arkui-window-findwindow-f.md#findwindow-1)中的任一方法获取到Window实例（windowClass），再通过此实例调用对应方法。

**起始版本：** 6

<!--Device-window-interface Window--><!--Device-window-interface Window-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## attachLayoutToParentWindow

```TypeScript
attachLayoutToParentWindow(anchorInfo?: WindowAnchorInfo, attachOptions?: SubWindowAttachOptions): Promise<void>
```

设置一级子窗与主窗保持相对位置不变。使用Promise异步回调。

该相对位置通过子窗与主窗之间的锚点偏移量表示，子窗和主窗使用的窗口锚点相同。

> **说明：**  
>  
> - 只支持一级子窗调用该接口，子窗需处于自由悬浮窗口模式（即窗口模式为window.WindowStatusType.FLOATING）。  
>  
> - 当子窗调用该接口后，立即使其显示位置跟随主窗并保持相对位置不变，并且可以监听主窗大小及模式切换。除非调用  
> [detachLayoutToParentWindow()](arkts-arkui-window-window-i-sys.md#detachlayouttoparentwindow-1)接口解绑，否则效果将持续。  
>  
> - 当子窗调用该接口后，再调用  
> [moveWindowTo()](arkts-arkui-window-window-i.md#movewindowto-2)、  
> [maximize()](arkts-arkui-window-window-i.md#maximize-1)、  
> [setFollowParentWindowLayoutEnabled()](arkts-arkui-window-window-i.md#setfollowparentwindowlayoutenabled-1)等修改窗  
> 口位置的接口，或通过鼠标/触摸操作对子窗进行拖拽移动、拖拽缩放时将不生效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Window-attachLayoutToParentWindow(anchorInfo?: WindowAnchorInfo, attachOptions?: SubWindowAttachOptions): Promise<void>--><!--Device-Window-attachLayoutToParentWindow(anchorInfo?: WindowAnchorInfo, attachOptions?: SubWindowAttachOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| anchorInfo | [WindowAnchorInfo](arkts-arkui-window-windowanchorinfo-i-sys.md) | 否 | 一级子窗与主窗保持相对位置不变时的锚点参数。若不传，默认逻辑参考[WindowAnchorInfo](arkts-arkui-window-windowanchorinfo-i-sys.md)。 |
| attachOptions | [SubWindowAttachOptions](arkts-arkui-window-subwindowattachoptions-i-sys.md) | 否 | 设置子窗布局的附加参数。若不传，默认逻辑参考[SubWindowAttachOptions](arkts-arkui-window-subwindowattachoptions-i-sys.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Function attachLayoutToParentWindow can not work correctly due to limited device capabilities. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation.Possible cause: 1. Invalid window type. Only subwindows are supported;2. The current window's parent window is not a main window;3. Only level-1 subwindows are supported. |
| [1300010](../errorcode-window.md#1300010-当前窗口模式不支持该操作) | The operation in the current window status is invalid.Possible cause: 1. The subwindow is following its parent window's layout.2. The subwindow is not in the floating mode. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', (loadError: BusinessError) => {
      if (loadError.code) {
        console.error(`Failed to load the content. Cause code: ${loadError.code}, message: ${loadError.message}`);
        return;
      }
      console.info("Succeeded in loading the content.");
      windowStage.createSubWindow("subWindow").then((subWindow: window.Window) => {
        if (subWindow == null) {
          console.error("Failed to create the subWindow. Cause: The data is empty");
          return;
        }
        let anchorInfo : window.WindowAnchorInfo = {
          anchorType: window.WindowAnchor.TOP_START,
          offsetX: 0,
          offsetY: 0
        };
        let attachOptions: window.SubWindowAttachOptions = {
          parentWindowSizeChangeCallback:(data: window.Size) => {
            console.info(`Successfully accepted parentWindow size change, width: ${data.width}, height: ${data.height}`);
          },
          parentWindowStatusChangeCallback:(type: window.WindowStatusType) => {
            console.info(`Successfully accepted parentWindow status change, statusType: ${type}`);
          },
          isIntersectedWidthLimit: true,
          isIntersectedHeightLimit: true
        }
        subWindow.attachLayoutToParentWindow(anchorInfo, attachOptions).then(() => {
          console.info("Succeeded in attaching to the main window");
        }).catch((error: BusinessError) => {
          console.error(`attachLayoutToParentWindow failed. ${error.code} ${error.message}`);
        })
      }).catch((error: BusinessError) => {
        console.error(`createSubWindow failed. ${error.code} ${error.message}`);
      })
    });
  }
}

```

## bindDialogTarget

```TypeScript
bindDialogTarget(token: rpc.RemoteObject, deathCallback: Callback<void>): Promise<void>
```

绑定模态窗口与目标窗口，成功绑定后，目标窗口不能响应用户操作。同时添加目标窗口销毁监听，使用Promise异步回调。

**起始版本：** 9

<!--Device-Window-bindDialogTarget(token: rpc.RemoteObject, deathCallback: Callback<void>): Promise<void>--><!--Device-Window-bindDialogTarget(token: rpc.RemoteObject, deathCallback: Callback<void>): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | rpc.RemoteObject | 是 | 目标窗口token值。 |
| deathCallback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<void> | 是 | 目标窗口销毁监听。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { dialogRequest, Want, ServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export class Property {
  public value: Object

  constructor(value: Object) {
    this.value = value
  }
}

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info('onRequest');
    let config: window.Configuration = {
      name: "test",
      windowType: window.WindowType.TYPE_DIALOG,
      ctx: this.context
    };
    try {
      window.createWindow(config, (err: BusinessError, data) => {
        const errCode: number = err?.code;
        if (errCode) {
          console.error(`Failed to create the window. Cause code: ${err?.code}, message: ${err?.message}`);
          return;
        }
        if (!data) {
          console.error('data is null');
          return;
        }
        let token = want.parameters?.['ohos.ability.params.request.token'] as Property;
        let value = token.value as rpc.RemoteObject;
        let promise = data.bindDialogTarget(value, () => {
          console.info('Dialog Window Need Destroy.');
        });
        promise.then(() => {
          console.info('Succeeded in binding dialog target.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`);
        });
      });
    } catch (err) {
      console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`)
    }
  }
}

```

## bindDialogTarget

```TypeScript
bindDialogTarget(token: rpc.RemoteObject, deathCallback: Callback<void>, callback: AsyncCallback<void>): void
```

绑定模态窗口与目标窗口，成功绑定后，目标窗口不能响应用户操作。同时添加目标窗口销毁监听，使用callback异步回调。

**起始版本：** 9

<!--Device-Window-bindDialogTarget(token: rpc.RemoteObject, deathCallback: Callback<void>, callback: AsyncCallback<void>): void--><!--Device-Window-bindDialogTarget(token: rpc.RemoteObject, deathCallback: Callback<void>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | rpc.RemoteObject | 是 | 目标窗口token值。 |
| deathCallback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<void> | 是 | 目标窗口销毁监听。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { dialogRequest, Want, ServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export class Property {
  public value: Object

  constructor(value: Object) {
    this.value = value
  }
}

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info('onRequest');
    let config: window.Configuration = {
      name: "test",
      windowType: window.WindowType.TYPE_DIALOG,
      ctx: this.context
    };
    try {
      window.createWindow(config, (err: BusinessError, data) => {
        let errCode: number = err?.code;
        if (errCode) {
          console.error(`Failed to create the window. Cause code: ${err?.code}, message: ${err?.message}`);
          return;
        }
        if (!data) {
          console.error('data is null');
          return;
        }
        let token = want.parameters?.['ohos.ability.params.request.token'] as Property;
        let value = token.value as rpc.RemoteObject;
        data.bindDialogTarget(value, () => {
          console.info('Dialog Window Need Destroy.');
          }, (err: BusinessError) => {
          let errCode: number = err?.code;
          if (errCode) {
            console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`);
            return;
          }
          console.info('Succeeded in binding dialog target.');
        });
      });
    } catch (err) {
      console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`)
    }
  }
}

```

## bindDialogTarget

```TypeScript
bindDialogTarget(requestInfo: dialogRequest.RequestInfo, deathCallback: Callback<void>): Promise<void>
```

绑定模态窗口与目标窗口，成功绑定后，目标窗口不能响应用户操作。同时添加目标窗口销毁监听，使用Promise异步回调。

**起始版本：** 9

<!--Device-Window-bindDialogTarget(requestInfo: dialogRequest.RequestInfo, deathCallback: Callback<void>): Promise<void>--><!--Device-Window-bindDialogTarget(requestInfo: dialogRequest.RequestInfo, deathCallback: Callback<void>): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestInfo | dialogRequest.RequestInfo | 是 | 目标窗口RequestInfo值。 |
| deathCallback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<void> | 是 | 目标窗口销毁监听。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
import { dialogRequest, Want, ServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info('onRequest');
    let config: window.Configuration = {
      name: "test", windowType: window.WindowType.TYPE_DIALOG, ctx: this.context
    };
    try {
      window.createWindow(config, (err: BusinessError, data) => {
        const errCode: number = err?.code;
        if (errCode) {
          console.error(`Failed to create the window. Cause code: ${err?.code}, message: ${err?.message}`);
          return;
        }
        if (!data) {
          console.error('data is null');
          return;
        }
        let requestInfo = dialogRequest.getRequestInfo(want);
        let promise = data.bindDialogTarget(requestInfo, () => {
          console.info('Dialog Window Need Destroy.');
        });
        promise.then(() => {
          console.info('Succeeded in binding dialog target.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`);
        });
      });
    } catch (err) {
      console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`)
    }
  }
}

```

## bindDialogTarget

```TypeScript
bindDialogTarget(requestInfo: dialogRequest.RequestInfo, deathCallback: Callback<void>, callback: AsyncCallback<void>): void
```

绑定模态窗口与目标窗口，成功绑定后，目标窗口不能响应用户操作。同时添加目标窗口销毁监听，使用callback异步回调。

**起始版本：** 9

<!--Device-Window-bindDialogTarget(requestInfo: dialogRequest.RequestInfo, deathCallback: Callback<void>, callback: AsyncCallback<void>): void--><!--Device-Window-bindDialogTarget(requestInfo: dialogRequest.RequestInfo, deathCallback: Callback<void>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestInfo | dialogRequest.RequestInfo | 是 | 目标窗口RequestInfo值。 |
| deathCallback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<void> | 是 | 目标窗口销毁监听。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
import { dialogRequest, Want, ServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info('onRequest');
    let config: window.Configuration = {
      name: "test", windowType: window.WindowType.TYPE_DIALOG, ctx: this.context
    };
    try {
      window.createWindow(config, (err: BusinessError, data) => {
        let errCode: number = err?.code;
        if (errCode) {
          console.error(`Failed to create the window. Cause code: ${err?.code}, message: ${err?.message}`);
          return;
        }
        if (!data) {
          console.error('data is null');
          return;
        }
        let requestInfo = dialogRequest.getRequestInfo(want);
        data.bindDialogTarget(requestInfo, () => {
          console.info('Dialog Window Need Destroy.');
          }, (err: BusinessError) => {
          let errCode: number = err?.code;
          if (errCode) {
            console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`);
            return;
          }
          console.info('Succeeded in binding dialog target.');
        });
      });
    } catch (err) {
      console.error(`Failed to bind dialog target. Cause code: ${err?.code}, message: ${err?.message}`)
    }
  }
}

```

## detachLayoutToParentWindow

```TypeScript
detachLayoutToParentWindow(): Promise<void>
```

解除一级子窗与主窗保持相对位置不变的协同关系。使用Promise异步回调。

> **说明：**  
>  
> - 子窗调用接口时需保持子窗处于协同状态。  
>  
> - 调用接口解除协同后，子窗将保持协同时的位置，可对子窗进行拖拽以修改子窗大小和位置。  
>  
> - 解除协同后，调用  
> [moveWindowTo()](arkts-arkui-window-window-i.md#movewindowto-2)、  
> [maximize()](arkts-arkui-window-window-i.md#maximize-1)、  
> [setFollowParentWindowLayoutEnabled()](arkts-arkui-window-window-i.md#setfollowparentwindowlayoutenabled-1)修改窗口  
> 位置的接口，或通过鼠标/触摸操作对子窗进行拖拽移动、拖拽缩放时将生效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Window-detachLayoutToParentWindow(): Promise<void>--><!--Device-Window-detachLayoutToParentWindow(): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Function detachLayoutToParentWindow cannot work correctly due to limited device capabilities. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation.Possible cause: 1. Invalid window type. Only subwindows are supported;2. Only level-1 subwindows are supported. |
| [1300010](../errorcode-window.md#1300010-当前窗口模式不支持该操作) | The operation in the current window status is invalid.Possible cause: The subwindow is not attached to the main window. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', (loadError: BusinessError) => {
      if (loadError.code) {
        console.error(`Failed to load the content. Cause code: ${loadError.code}, message: ${loadError.message}`);
        return;
      }
      console.info("Succeeded in loading the content.");
      windowStage.createSubWindow("subWindow").then((subWindow: window.Window) => {
        if (subWindow == null) {
          console.error("Failed to create the subWindow. Cause: The data is empty");
          return;
        }
        subWindow.detachLayoutToParentWindow().then(() => {
          console.info("Succeeded in detaching to the main window");
        }).catch((error: BusinessError) => {
          console.error(`detachLayoutToParentWindow failed. ${error.code} ${error.message}`);
        })
      }).catch((error: BusinessError) => {
        console.error(`createSubWindow failed. ${error.code} ${error.message}`);
      })
    });
  }
}

```

## enableDrag

```TypeScript
enableDrag(enable: boolean): Promise<void>
```

使能/禁止拖拽窗口，仅对系统窗口、应用子窗口、全局悬浮窗和模态窗口生效。使用Promise异步回调。

使能后，将允许通过鼠标操作或触摸对窗口进行拉伸操作。

**起始版本：** 20

<!--Device-Window-enableDrag(enable: boolean): Promise<void>--><!--Device-Window-enableDrag(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否允许拖拽。<br>true表示允许，false表示不允许。&lt;/br&gt; |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 14 - 19 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

## getRotationLocked

```TypeScript
getRotationLocked(): boolean
```

仅支持[系统窗口](../../../../windowmanager/window-terminology.md#系统窗口)获取当前旋转锁定状态。非系统窗口调用返回1300029错误码。

**起始版本：** 22

<!--Device-Window-getRotationLocked(): boolean--><!--Device-Window-getRotationLocked(): boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前系统窗是否设置旋转锁定。true表示当前系统窗已锁定旋转；false表示当前系统窗未锁定旋转。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function setRotationLocked can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| 1300029 | This window type is invalid. |

**示例：**

```TypeScript
try {
  let locked = windowClass.getRotationLocked();
  console.info('Succeeded in getting rotation locked.');
} catch (exception) {
  console.error(`Failed to get rotation locked. Cause code: ${exception.code}, message: ${exception.message}`);
};

```

## getTransitionController

```TypeScript
getTransitionController(): TransitionController
```

获取窗口属性转换控制器。

**起始版本：** 9

<!--Device-Window-getTransitionController(): TransitionController--><!--Device-Window-getTransitionController(): TransitionController-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TransitionController](arkts-arkui-window-transitioncontroller-i-sys.md) | 属性转换控制器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
let controller = windowClass.getTransitionController(); // 获取属性转换控制器

```

## hide

```TypeScript
hide (callback: AsyncCallback<void>): void
```

隐藏当前窗口，使用callback异步回调，仅支持系统窗口与应用子窗口。

**起始版本：** 7

<!--Device-Window-hide (callback: AsyncCallback<void>): void--><!--Device-Window-hide (callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.hide((err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to hide the window. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding the window.');
});

```

## hide

```TypeScript
hide(): Promise<void>
```

隐藏当前窗口，使用Promise异步回调，仅支持系统窗口与应用子窗口。

**起始版本：** 7

<!--Device-Window-hide(): Promise<void>--><!--Device-Window-hide(): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.hide();
promise.then(() => {
  console.info('Succeeded in hiding the window.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide the window. Cause code: ${err.code}, message: ${err.message}`);
});

```

## hideNonSystemFloatingWindows

```TypeScript
hideNonSystemFloatingWindows(shouldHide: boolean, callback: AsyncCallback<void>): void
```

设置是否隐藏非系统级悬浮窗口（[windowType](arkts-arkui-window-windowtype-e.md)类型为TYPE_FLOAT），使用callback异步回调。

非系统级悬浮窗口是指非系统应用创建的悬浮窗口。默认情况下，一个系统应用主窗口可以与非系统级悬浮窗口共同显示，即该主窗口可以被上层的非系统级悬浮窗口遮挡，如果设置为true，则所有的非系统级悬浮窗口都会被隐藏，此时该主窗口就不会被上层的非系统级悬浮窗口遮挡。

**起始版本：** 11

<!--Device-Window-hideNonSystemFloatingWindows(shouldHide: boolean, callback: AsyncCallback<void>): void--><!--Device-Window-hideNonSystemFloatingWindows(shouldHide: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shouldHide | boolean | 是 | 指示是否隐藏非系统级的悬浮窗口，true表示隐藏，false表示不隐藏。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // 加载主窗口对应的页面
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('Succeeded in loading the content.');
    });

    // 获取应用主窗口。
    let mainWindow: window.Window | undefined = undefined;
    windowStage.getMainWindow((err, data) => {
      if (err.code) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      mainWindow = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));

      let shouldHide = true;
      try {
        // 调用带callback参数的hideNonSystemFloatingWindows接口
        mainWindow.hideNonSystemFloatingWindows(shouldHide, (err) => {
          if (err.code) {
            console.error(`Failed to hide the non-system floating windows. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in hiding the non-system floating windows.');
        });
      } catch (exception) {
        console.error(`Failed to hide the non-system floating windows. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}

```

## hideNonSystemFloatingWindows

```TypeScript
hideNonSystemFloatingWindows(shouldHide: boolean): Promise<void>
```

设置是否隐藏非系统级悬浮窗口（[windowType](arkts-arkui-window-windowtype-e.md)类型为TYPE_FLOAT），使用Promise异步回调。

非系统级悬浮窗口是指非系统应用创建的悬浮窗口。默认情况下，一个系统应用主窗口可以与非系统级悬浮窗口共同显示，即该主窗口可以被上层的非系统级悬浮窗口遮挡，如果设置为true，则所有的非系统级悬浮窗口都会被隐藏，此时该主窗口就不会被上层的非系统级悬浮窗口遮挡。

**起始版本：** 11

<!--Device-Window-hideNonSystemFloatingWindows(shouldHide: boolean): Promise<void>--><!--Device-Window-hideNonSystemFloatingWindows(shouldHide: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shouldHide | boolean | 是 | 指示是否隐藏非系统级的悬浮窗口，true表示隐藏，false表示不隐藏。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // 加载主窗口对应的页面
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('Succeeded in loading the content.');
    });

    // 获取应用主窗口。
    let mainWindow: window.Window | undefined = undefined;
    windowStage.getMainWindow((err, data) => {
      if (err.code) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      mainWindow = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));

      let shouldHide = true;
      try {
        // 调用hideNonSystemFloatingWindows接口，获取promise对象
        let promise = mainWindow.hideNonSystemFloatingWindows(shouldHide);
        promise.then(()=> {
          console.info('Succeeded in hiding the non-system floating windows.');
        }).catch((err: BusinessError)=>{
          console.error(`Failed to hide the non-system floating windows. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to hide the non-system floating windows. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}

```

## hideWithAnimation

```TypeScript
hideWithAnimation(callback: AsyncCallback<void>): void
```

隐藏当前窗口，过程中播放动画，使用callback异步回调，仅支持系统窗口。

**起始版本：** 9

<!--Device-Window-hideWithAnimation(callback: AsyncCallback<void>): void--><!--Device-Window-hideWithAnimation(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation.Possible cause: Invalid window type. Only system windows are supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.hideWithAnimation((err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to hide the window with animation. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding the window with animation.');
});

```

## hideWithAnimation

```TypeScript
hideWithAnimation(): Promise<void>
```

隐藏当前窗口，过程中播放动画，使用Promise异步回调，仅支持系统窗口。

**起始版本：** 9

<!--Device-Window-hideWithAnimation(): Promise<void>--><!--Device-Window-hideWithAnimation(): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation.Possible cause: Invalid window type. Only system windows are supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.hideWithAnimation();
promise.then(() => {
  console.info('Succeeded in hiding the window with animation.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide the window with animation. Cause code: ${err.code}, message: ${err.message}`);
});

```

## isMainWindowFullScreenAcrossDisplays

```TypeScript
isMainWindowFullScreenAcrossDisplays(): Promise<boolean>
```

判断当前窗口的主窗口是否是跨多块屏幕使用全屏模式显示，使用Promise异步回调，仅支持主窗口与应用子窗口。

**起始版本：** 20

<!--Device-Window-isMainWindowFullScreenAcrossDisplays(): Promise<boolean>--><!--Device-Window-isMainWindowFullScreenAcrossDisplays(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回true表示当前窗口的主窗口跨多块屏幕使用全屏模式显示，返回false表示当前窗口的主窗口未跨多块屏幕使用全屏模式显示。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = windowClass.isMainWindowFullScreenAcrossDisplays();
  promise.then((data: boolean)=> {
      console.info(`Succeeded in using isMainWindowFullScreenAcrossDisplays function. Data: ${data}`);
  }).catch((err: BusinessError)=>{
      console.error(`Failed to use isMainWindowFullScreenAcrossDisplays function. code:${err.code}, message:${err.message}.`);
  });
} catch (exception) {
  console.error(`Failed to use isMainWindowFullScreenAcrossDisplays function. Cause code: ${exception.code}, message: ${exception.message}.`);
}

```

## off('mainWindowFullScreenAcrossDisplaysChanged')

```TypeScript
off(type: 'mainWindowFullScreenAcrossDisplaysChanged', callback?: Callback<boolean>): void
```

取消监听本窗口的主窗口跨多块屏幕使用全屏模式显示的状态变化事件。

**起始版本：** 20

<!--Device-Window-off(type: 'mainWindowFullScreenAcrossDisplaysChanged', callback?: Callback<boolean>): void--><!--Device-Window-off(type: 'mainWindowFullScreenAcrossDisplaysChanged', callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'mainWindowFullScreenAcrossDisplaysChanged' | 是 | 监听事件，固定为'mainWindowFullScreenAcrossDisplaysChanged'，即本窗口的主窗口跨多块屏幕使用全屏模式显示的状态变化。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<boolean> | 否 | 回调函数。即本窗口的主窗口跨多块屏幕使用全屏模式显示的状态变化回调。如果传入参数，则关闭该监听。如果未传入参数，则关闭所有本窗口的主窗口跨多块屏幕使用全屏模式显示的状态变化回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation.Possible cause: Invalid window type. Only main windows and subwindows are supported. |

**示例：**

```TypeScript
const callback = (mainWindowFullScreenAcrossDisplaysChanged: boolean) => {
  // ...
}
try {
  // 通过on接口开启监听
  windowClass.on('mainWindowFullScreenAcrossDisplaysChanged', callback);
  // 关闭指定callback的监听
  windowClass.off('mainWindowFullScreenAcrossDisplaysChanged', callback);
  // 如果通过on开启多个callback进行监听，同时关闭所有监听：
  windowClass.off('mainWindowFullScreenAcrossDisplaysChanged');
} catch (exception) {
  console.error(`Failed to unregister callback. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## on('mainWindowFullScreenAcrossDisplaysChanged')

```TypeScript
on(type: 'mainWindowFullScreenAcrossDisplaysChanged', callback: Callback<boolean>): void
```

监听本窗口的主窗口跨多块屏幕使用全屏模式显示的状态变化事件。

**起始版本：** 20

<!--Device-Window-on(type: 'mainWindowFullScreenAcrossDisplaysChanged', callback: Callback<boolean>): void--><!--Device-Window-on(type: 'mainWindowFullScreenAcrossDisplaysChanged', callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'mainWindowFullScreenAcrossDisplaysChanged' | 是 | 监听事件，固定为'mainWindowFullScreenAcrossDisplaysChanged'，即本窗口的主窗口跨多块屏幕使用全屏模式显示的状态变化。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<boolean> | 是 | 回调函数。即本窗口的主窗口跨多块屏幕使用全屏模式显示的状态变化回调。true表示主窗口进入跨多块屏幕使用全屏模式显示状态，false表示主窗口退出跨多块屏幕使用全屏模式显示状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation.Possible cause: Invalid window type. Only main windows and subwindows are supported. |

**示例：**

```TypeScript
const callback = (mainWindowFullScreenAcrossDisplaysChanged: boolean) => {
  console.info(`main window across displays changed. Data: ${mainWindowFullScreenAcrossDisplaysChanged}`);
}
try {
  windowClass.on('mainWindowFullScreenAcrossDisplaysChanged', callback);
} catch (exception) {
  console.error(`Failed to register callback. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## opacity

```TypeScript
opacity(opacity: number): void
```

设置窗口不透明度。仅支持在[自定义系统窗口的显示与隐藏动画](../../../../windowmanager/system-window-stage-sys.md#自定义系统窗口的显示与隐藏动画)中使用。

**起始版本：** 9

<!--Device-Window-opacity(opacity: double): void--><!--Device-Window-opacity(opacity: double): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| opacity | number | 是 | 不透明度。该参数为浮点数，取值范围为[0.0, 1.0]。0.0表示完全透明，1.0表示完全不透明。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
try {
  windowClass.opacity(0.5);
} catch (exception) {
  console.error(`Failed to opacity. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## raiseAboveTarget

```TypeScript
raiseAboveTarget(windowId: number, callback: AsyncCallback<void>): void
```

将同一个主窗口下的子窗口抬升到目标子窗口之上。使用callback异步回调。

使用该接口需要确保要抬升的子窗口和目标子窗口都已创建完成，分别调用[showWindow()](arkts-arkui-window-window-i.md#showwindow-1)并执行完毕。

**起始版本：** 10

<!--Device-Window-raiseAboveTarget(windowId: int, callback: AsyncCallback<void>): void--><!--Device-Window-raiseAboveTarget(windowId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | number | 是 | 目标子窗口的id，通过[getWindowProperties](arkts-arkui-window-window-i.md#getwindowproperties-1)接口获取到[properties](arkts-arkui-window-windowproperties-i.md)后，再通过properties.id获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: Mandatory parameters are left unspecified. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |
| [1300009](../errorcode-window.md#1300009-父窗口无效) | The parent window is invalid. |

**示例：**

```TypeScript
// EntryAbility.ets
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window;
    // 创建子窗
    try {
      windowStage.createSubWindow("testSubWindow").then((data) => {
        if (data == null) {
          console.error("Failed to create the subWindow. Cause: The data is empty");
          return;
        }
        windowClass = data;
        windowClass.showWindow().then(() => {
          // windowClass的获取需放在targetWindow之上
          let targetWindow: window.Window = windowClass;
          let properties = targetWindow.getWindowProperties();
          let targetId = properties.id;
          windowClass.raiseAboveTarget(targetId, (err: BusinessError) => {
            if (err.code) {
              console.error(`Failed to raise the subWindow to target subWindow top. Cause code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('Succeeded in raising the subWindow to target subWindow top.');
          });
        });
      });
    } catch (exception) {
      console.error(`Failed to create the subWindow. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}

```

## raiseAboveTarget

```TypeScript
raiseAboveTarget(windowId: number): Promise<void>
```

将同一个主窗下的子窗口提升到目标子窗口之上。使用Promise异步回调。

使用该接口需要确保要抬升的子窗口和目标子窗口都已创建完成，分别调用[showWindow()](arkts-arkui-window-window-i.md#showwindow-1)并执行完毕。

**起始版本：** 10

<!--Device-Window-raiseAboveTarget(windowId: int): Promise<void>--><!--Device-Window-raiseAboveTarget(windowId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | number | 是 | 目标子窗口的id，通过[getWindowProperties](arkts-arkui-window-window-i.md#getwindowproperties-1)接口获取到[properties](arkts-arkui-window-windowproperties-i.md)后，再通过properties.id获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: Mandatory parameters are left unspecified. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |
| [1300009](../errorcode-window.md#1300009-父窗口无效) | The parent window is invalid. |

**示例：**

```TypeScript
// EntryAbility.ets
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window;
    // 创建子窗
    try {
      windowStage.createSubWindow("testSubWindow").then((data) => {
        if (data == null) {
          console.error("Failed to create the subWindow. Cause: The data is empty");
          return;
        }
        windowClass = data;
        windowClass.showWindow().then(() => {
          // windowClass的获取需放在targetWindow之上
          let targetWindow: window.Window = windowClass;
          let properties = targetWindow.getWindowProperties();
          let targetId = properties.id;
          windowClass.raiseAboveTarget(targetId).then(()=> {
            console.info('Succeeded in raising the subWindow to target subWindow top.');
          }).catch((err: BusinessError)=>{
            console.error(`Failed to raise the subWindow to target subWindow top. Cause code: ${err.code}, message: ${err.message}`);
          });
        });
      });
    } catch (exception) {
      console.error(`Failed to create the subWindow. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}

```

## raiseMainWindowAboveTarget

```TypeScript
raiseMainWindowAboveTarget(windowId: number): Promise<void>
```

将主窗口的层级调整至同应用下的另一个主窗口之上，子窗口的层级会跟随所属主窗口变动。使用Promise异步回调。

仅支持系统应用主窗口调用。

传入目标主窗口的id，调用窗口和目标窗口需满足：同应用进程、显示在同一物理屏、层级低于锁屏、非置顶主窗、非模态主窗且无模应用子窗。

- 应用主窗口或者它的子窗口如果是焦点窗口，此主窗口调用该接口降低层级后则自动失焦，由当前层级最高的应用窗口获焦。  
- 应用主窗口调用该接口调整层级后超过当前焦点窗口，则被抬升主窗口及其子窗口中，层级最高的窗口自动获焦；应用主窗口调用该接口调整层级后未超过当前焦点窗口，则焦点不做转移。

**起始版本：** 20

<!--Device-Window-raiseMainWindowAboveTarget(windowId: int): Promise<void>--><!--Device-Window-raiseMainWindowAboveTarget(windowId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | number | 是 | 目标主窗口的id，该参数为整数，通过[getWindowProperties](arkts-arkui-window-window-i.md#getwindowproperties-1)接口获取到[properties](arkts-arkui-window-windowproperties-i.md)后，再通过properties.id获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible cause:1. Invalid parameter range. 2. Invalid parameter length. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility, Want, StartOptions, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}.`);
        return;
      }
      console.info('Succeeded in loading the content.');
      try {
        let want: Want = {
          abilityName: "RaiseMainWindowAbility",
          bundleName: "com.example.myapplication"
        };
        let options: StartOptions = {
          windowMode: AbilityConstant.WindowMode.WINDOW_MODE_FLOATING
        };
        this.context.startAbility(want, options);
      } catch (err) {
        console.error(`Failed to start the ability. Cause code: ${err.code}, message: ${err.message}.`);
      }
      setTimeout(async () => {
        let mainWindow: window.Window | null | undefined = windowStage.getMainWindowSync();
        let targetId: number | null | undefined = AppStorage.get('higher_window_id');
        mainWindow.raiseMainWindowAboveTarget(targetId).then(() => {
          console.info('Succeeded in raising main window above target.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to raise main window above target. Cause code: ${err.code}, message: ${err.message}.`)
        });
      }, 3000)
    });
  }
}

```

```TypeScript
// 新建文件src/main/ets/raisemainwindowability/RaiseMainWindowAbility.ets
import { UIAbility } from '@kit.AbilityKit';

export default class RaiseMainWindowAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    AppStorage.setOrCreate('higher_window_id', windowStage.getMainWindowSync().getWindowProperties().id);
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}.`);
        return;
      }
      console.info('Succeeded in loading the content.');
    });
  }
}

```

```TypeScript
// module.json5
{
  "module": {
    "name": "entry",
    "type": "entry",
    "description": "$string:module_desc",
    "mainElement": "EntryAbility",
    "deviceTypes": [
      "phone",
      "tablet",
      "2in1"
    ],
    "deliveryWithInstall": true,
    "installationFree": false,
    "pages": "$profile:main_pages",
    "abilities": [
      {
        "name": "EntryAbility",
        "srcEntry": "./ets/entryability/EntryAbility.ets",
        "description": "$string:EntryAbility_desc",
        "icon": "$media:layered_image",
        "label": "$string:EntryAbility_label",
        "startWindowIcon": "$media:startIcon",
        "startWindowBackground": "$color:start_window_background",
        "exported": true,
        "skills": [
          {
            "entities": [
              "entity.system.home"
            ],
            "actions": [
              "action.system.home"
            ]
          }
        ]
      },
      {
        "name": "RaiseMainWindowAbility",
        "launchType": "multiton",
        "srcEntry": "./ets/entryability/EntryAbility.ets",
        "description": "$string:EntryAbility_desc",
        "icon": "$media:layered_image",
        "label": "$string:EntryAbility_label",
        "startWindowIcon": "$media:startIcon",
        "startWindowBackground": "$color:start_window_background",
        "exported": true,
        "skills": [
          {
            "entities": [
              "entity.system.home"
            ],
            "actions": [
              "action.system.home"
            ]
          }
        ]
      }
    ]
  }
}

```

## raiseToAppTop

```TypeScript
raiseToAppTop(callback: AsyncCallback<void>): void
```

提升应用子窗口到应用顶层。使用callback异步回调。

使用该接口需要先创建子窗口，并确保该子窗口调用[showWindow()](arkts-arkui-window-window-i.md#showwindow-1)并执行完毕。

**起始版本：** 10

<!--Device-Window-raiseToAppTop(callback: AsyncCallback<void>): void--><!--Device-Window-raiseToAppTop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |
| [1300009](../errorcode-window.md#1300009-父窗口无效) | The parent window is invalid. |

**示例：**

```TypeScript
// EntryAbility.ets
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    // 创建子窗
    windowStage.createSubWindow('testSubWindow').then((subWindow) => {
      if (subWindow == null) {
        console.error('Failed to create the subWindow. Cause: The data is empty');
        return;
      }
      subWindow.showWindow().then(() => {
        subWindow.raiseToAppTop((err: BusinessError) => {
          const errCode: number = err.code;
          if (errCode) {
            console.error(`Failed to raise the window to app top. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in raising the window to app top.');
        });
      });
    });
  }
}

```

## requestFocus

```TypeScript
requestFocus(isFocused: boolean): Promise<void>
```

支持当前窗口主动请求获焦/失焦，使用Promise异步回调。调用成功即返回，该接口返回值不代表最终获焦/失焦生效结果。可使用[on('windowEvent')](arkts-arkui-window-window-i.md#on-22)监听窗口获焦/失焦状态。

获焦请求发送后，窗口获焦结果受到窗口可获焦属性及窗口可见状态的限制。获焦成功的窗口需满足以下约束：1.窗口支持获焦；2.窗口可见（窗口已显示，未销毁且未退至后台）。

失焦请求发送后，窗口无条件失焦。

**起始版本：** 13

<!--Device-Window-requestFocus(isFocused: boolean): Promise<void>--><!--Device-Window-requestFocus(isFocused: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isFocused | boolean | 是 | 是否获取焦点，true表示请求获焦，false表示请求失焦。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, non-system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isFocused: boolean = true;
let promise = windowClass.requestFocus(isFocused);
promise.then(() => {
  console.info('Succeeded in requesting focus.');
}).catch((err: BusinessError) => {
  console.error(`Failed to request focus. Cause code: ${err.code}, message: ${err.message}`);
});

```

## rotate

```TypeScript
rotate(rotateOptions: RotateOptions): void
```

设置窗口旋转参数。仅支持在[自定义系统窗口的显示与隐藏动画](../../../../windowmanager/system-window-stage-sys.md#自定义系统窗口的显示与隐藏动画)中使用。

**起始版本：** 9

<!--Device-Window-rotate(rotateOptions: RotateOptions): void--><!--Device-Window-rotate(rotateOptions: RotateOptions): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotateOptions | [RotateOptions](../arkts-components/arkts-arkui-common-rotateoptions-i.md) | 是 | 旋转参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
let obj: window.RotateOptions = {
  x: 1.0,
  y: 1.0,
  z: 45.0,
  pivotX: 0.5,
  pivotY: 0.5
};
try {
  windowClass.rotate(obj);
} catch (exception) {
  console.error(`Failed to rotate. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## scale

```TypeScript
scale(scaleOptions: ScaleOptions): void
```

设置窗口缩放参数。仅支持在[自定义系统窗口的显示与隐藏动画](../../../../windowmanager/system-window-stage-sys.md#自定义系统窗口的显示与隐藏动画)中使用。

**起始版本：** 9

<!--Device-Window-scale(scaleOptions: ScaleOptions): void--><!--Device-Window-scale(scaleOptions: ScaleOptions): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scaleOptions | [ScaleOptions](../arkts-components/arkts-arkui-common-scaleoptions-i.md) | 是 | 缩放参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
let obj: window.ScaleOptions = {
  x: 2.0,
  y: 1.0,
  pivotX: 0.5,
  pivotY: 0.5
};
try {
  windowClass.scale(obj);
} catch (exception) {
  console.error(`Failed to scale. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setBackdropBlur

```TypeScript
setBackdropBlur(radius: number): void
```

设置窗口背景模糊。

窗口背景是指窗口覆盖的下层区域，与窗口大小相同。

需要通过[setWindowBackgroundColor](arkts-arkui-window-window-i.md#setwindowbackgroundcolor-1)将窗口内容背景设置成透明，否则无法看到模糊效果。

**起始版本：** 9

<!--Device-Window-setBackdropBlur(radius: double): void--><!--Device-Window-setBackdropBlur(radius: double): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | number | 是 | 表示窗口背景模糊的半径值。该参数为浮点数，单位为px，取值范围为[0.0, +∞)，取值为0.0表示关闭窗口背景模糊。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
try {
  windowClass.setWindowBackgroundColor('#00FFFFFF');
  windowClass.setBackdropBlur(4.0);
} catch (exception) {
  console.error(`Failed to set backdrop blur. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setBackdropBlurStyle

```TypeScript
setBackdropBlurStyle(blurStyle: BlurStyle): void
```

设置窗口背景模糊类型。

**起始版本：** 9

<!--Device-Window-setBackdropBlurStyle(blurStyle: BlurStyle): void--><!--Device-Window-setBackdropBlurStyle(blurStyle: BlurStyle): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurStyle | [BlurStyle](../arkts-components/arkts-arkui-common-blurstyle-e.md) | 是 | 表示窗口背景模糊类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
try {
  windowClass.setBackdropBlurStyle(window.BlurStyle.THIN);
} catch (exception) {
  console.error(`Failed to set backdrop blur style. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setBlur

```TypeScript
setBlur(radius: number): void
```

设置窗口模糊。

**起始版本：** 9

<!--Device-Window-setBlur(radius: double): void--><!--Device-Window-setBlur(radius: double): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | number | 是 | 表示窗口模糊的半径值。该参数为浮点数，单位为px，取值范围为[0, +∞)，取值为0.0时表示关闭窗口模糊。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
try {
  windowClass.setBlur(4.0);
} catch (exception) {
  console.error(`Failed to set blur. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setCornerRadius

```TypeScript
setCornerRadius(cornerRadius: number): void
```

设置窗口圆角半径。

**起始版本：** 9

<!--Device-Window-setCornerRadius(cornerRadius: double): void--><!--Device-Window-setCornerRadius(cornerRadius: double): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cornerRadius | number | 是 | 表示窗口圆角的半径值。该参数为浮点数，单位为px，取值范围为[0.0, +∞)，取值为0.0时表示没有窗口圆角。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
try {
  windowClass.setCornerRadius(4.0);
} catch (exception) {
  console.error(`Failed to set corner radius. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setDefaultDensityEnabled

```TypeScript
setDefaultDensityEnabled(enabled: boolean): void
```

设置窗口是否使用所在屏幕的系统默认Density。Stage模型下，该接口需要在[loadContent()](arkts-arkui-window-window-i.md#loadcontent-1)或[setUIContent()](arkts-arkui-window-window-i.md#setuicontent-1)调用生效后使用。

不调用此接口进行设置，则表示不使用系统默认Density。

当存在同时使用该接口、[setDefaultDensityEnabled(true)](../../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#setdefaultdensityenabled12)和[setCustomDensity](../../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#setcustomdensity15)时，以最后调用的设置效果为准。

**起始版本：** 20

<!--Device-Window-setDefaultDensityEnabled(enabled: boolean): void--><!--Device-Window-setDefaultDensityEnabled(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置是否使用系统默认Density。true表示使用系统默认Density，窗口不跟随系统显示大小变化重新布局；false表示不使用系统默认Density，窗口跟随系统显示大小变化重新布局。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The window is not created or destroyed. |

**示例：**

```TypeScript
try {
  windowClass.setDefaultDensityEnabled(true);
  console.info(`Succeeded in setting default density enabled`);
} catch (exception) {
  console.error(`Failed to set default density enabled. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setForbidSplitMove

```TypeScript
setForbidSplitMove(isForbidSplitMove: boolean, callback: AsyncCallback<void>): void
```

设置主窗口在分屏模式下是否被禁止移动，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 26.0.0

<!--Device-Window-setForbidSplitMove(isForbidSplitMove: boolean, callback: AsyncCallback<void>): void--><!--Device-Window-setForbidSplitMove(isForbidSplitMove: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isForbidSplitMove | boolean | 是 | 窗口在分屏模式下是否被禁止移动。true表示禁止；false表示不禁止。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let isForbidSplitMove: boolean = true;
      try {
        windowClass.setForbidSplitMove(isForbidSplitMove, (err: BusinessError) => {
          const errCode: number = err.code;
          if (errCode) {
            console.error(`Failed to forbid window moving in split screen mode. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in forbidding window moving in split screen mode.');
        });
      } catch (exception) {
        console.error(`Failed to forbid window moving in split screen mode. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}

```

## setForbidSplitMove

```TypeScript
setForbidSplitMove(isForbidSplitMove: boolean): Promise<void>
```

设置主窗口在分屏模式下是否被禁止移动，使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 26.0.0

<!--Device-Window-setForbidSplitMove(isForbidSplitMove: boolean): Promise<void>--><!--Device-Window-setForbidSplitMove(isForbidSplitMove: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isForbidSplitMove | boolean | 是 | 窗口在分屏模式下是否被禁止移动。true表示禁止；false表示不禁止。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let isForbidSplitMove: boolean = true;
      try {
        let promise = windowClass.setForbidSplitMove(isForbidSplitMove);
        promise.then(() => {
          console.info('Succeeded in forbidding window moving in split screen mode.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to forbid window moving in split screen mode. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to forbid window moving in split screen mode. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}

```

## setHandwritingFlag

```TypeScript
setHandwritingFlag(enable: boolean): Promise<void>
```

为当前窗口添加或移除手写标志，添加该标志后窗口只响应手写笔事件，不响应触屏事件。使用Promise异步回调。

**起始版本：** 12

<!--Device-Window-setHandwritingFlag(enable: boolean): Promise<void>--><!--Device-Window-setHandwritingFlag(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否对窗口添加标志位。true表示添加，false表示移除。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let enable = true;
  let promise = windowClass.setHandwritingFlag(enable);
  promise.then(() => {
    console.info('Succeeded in setting handwriting flag of window.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set handwriting flag of window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set handwriting flag of window. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setMainWindowRaiseByClickEnabled

```TypeScript
setMainWindowRaiseByClickEnabled(enable: boolean): Promise<void>
```

禁止/使能主窗口点击抬升功能。使用Promise异步回调。

点击主窗口时，默认会抬升主窗口及其子窗口。调用此接口禁止主窗口点击抬升后（即传入false），点击主窗口时不会将其及子窗口进行抬升，保持原有状态不变；点击子窗口时，主窗口会连同子窗口一起被抬升。

**起始版本：** 23

<!--Device-Window-setMainWindowRaiseByClickEnabled(enable: boolean): Promise<void>--><!--Device-Window-setMainWindowRaiseByClickEnabled(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 设置主窗口点击抬升功能是否使能，true表示使能，false表示禁止。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.getMainWindow().then((window: window.Window) => {
      // 加载主窗口对应的页面
      windowStage.loadContent('pages/Index', (err) => {
        if (err.code) {
          console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in loading the content.');
        try {
          let raiseEnabled: boolean = false;
          let promise = window.setMainWindowRaiseByClickEnabled(raiseEnabled);
          promise.then(() => {
            console.info('Succeeded in disabling the raise-by-click function.');
          })
        } catch(err) {
          console.error(`Failed to disable the raise-by-click function. Cause code: ${err.code}, message: ${err.message}`);
        };
      });
    });
  }
}

```

## setRaiseByClickEnabled

```TypeScript
setRaiseByClickEnabled(enable: boolean, callback: AsyncCallback<void>): void
```

禁止/使能子窗口点击抬升功能。使用callback异步回调。

通常来说，点击一个子窗口，会将该子窗口显示到最上方，如果设置为false，那么点击子窗口的时候，不会将该子窗口显示到最上方，而是保持不变。

使用该接口需要先创建子窗口，并确保该子窗口调用[showWindow()](arkts-arkui-window-window-i.md#showwindow-1)并执行完毕。

**起始版本：** 10

<!--Device-Window-setRaiseByClickEnabled(enable: boolean, callback: AsyncCallback<void>): void--><!--Device-Window-setRaiseByClickEnabled(enable: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 设置子窗口点击抬升功能是否使能，true表示使能，false表示禁止。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |
| [1300009](../errorcode-window.md#1300009-父窗口无效) | The parent window is invalid. |

**示例：**

```TypeScript
// EntryAbility.ets
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    // 创建子窗
    windowStage.createSubWindow("testSubWindow").then((subWindow) => {
      if (subWindow == null) {
        console.error('Failed to create the subWindow. Cause: The data is empty');
        return;
      }
      subWindow.showWindow().then(() => {
        try {
          let enabled = false;
          subWindow.setRaiseByClickEnabled(enabled, (err) => {
          if (err.code) {
            console.error(`Failed to disable the raise-by-click function. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in disabling the raise-by-click function.');
          });
        } catch (err) {
          console.error(`Failed to disable the raise-by-click function. Cause code: ${err.code}, message: ${err.message}`);
        }
      });
    });
  }
}

```

## setRotationLocked

```TypeScript
setRotationLocked(locked: boolean): Promise<void>
```

仅支持[系统窗口](../../../../windowmanager/window-terminology.md#系统窗口)设置旋转锁定，锁定后系统窗口显示方向不变，未锁定时系统窗口显示方向受主窗口显示方向、旋转锁定按钮、sensor旋转影响。非系统窗口调用返回1300029错误码。使用Promise异步回调。

> **说明：**  
>  
> - 如果在锁定期间主窗口通过  
> [setPreferredOrientation()](arkts-arkui-window-window-i.md#setpreferredorientation-2)  
> 设置显示方向属性，则解除旋转锁定后该窗口在前台还原最后一次的方向请求。  
>  
> - 如果在锁定期间系统窗口通过  
> [setPreferredOrientation()](arkts-arkui-window-window-i.md#setpreferredorientation-2)  
> 设置显示方向属性，则解除旋转锁定后该窗口在前台且层级最高时还原最后一次的方向请求。低层级窗口通过setRotationLocked设置旋转锁定不会影响高层级系统窗口调用  
> [setPreferredOrientation()](arkts-arkui-window-window-i.md#setpreferredorientation-2)  
> 设置显示方向。  
>  
> - 如果在锁定期间sensor方向发生了变化，则解除旋转锁定后还原到最后一次的sensor方向。  
>  
> - 如果在锁定期间应用调用  
> [setOrientation()](arkts-arkui-screen-screen-i-sys.md#setorientation-1)  
> 设置屏幕方向，忽略该次屏幕方向设置。  
>  
> - 解除锁定时，根据主窗口的显示方向属性  
> [setPreferredOrientation()](arkts-arkui-window-window-i.md#setpreferredorientation-2)  
> 、sensor方向等决定应用显示方向，具体见[窗口旋转简介](../../../../windowmanager/window-rotation.md#窗口旋转简介)。  
>  
> - 不影响应用[module.json5配置文件中的abilities标签](../../../../quick-start/module-configuration-file.md#abilities标签)  
> orientation属性设置的启动方向。

**起始版本：** 22

<!--Device-Window-setRotationLocked(locked: boolean): Promise<void>--><!--Device-Window-setRotationLocked(locked: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locked | boolean | 是 | 设置是否锁定旋转，true表示锁定旋转，false表示解除锁定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function setRotationLocked can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| 1300029 | This window type is invalid. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let locked: boolean = true;
let promise = windowClass.setRotationLocked(locked);
promise.then(() => {
  console.info('set rotation locked success.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set rotation locked. Cause code: ${err.code}, message: ${err.message}`);
});

```

## setShadow

```TypeScript
setShadow(radius: number, color?: string, offsetX?: number, offsetY?: number): void
```

设置窗口边缘阴影。

**起始版本：** 9

<!--Device-Window-setShadow(radius: double, color?: string, offsetX?: double, offsetY?: double): void--><!--Device-Window-setShadow(radius: double, color?: string, offsetX?: double, offsetY?: double): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | number | 是 | 表示窗口边缘阴影的模糊半径。该参数为浮点数，单位为px，取值范围为[0.0, +∞)，取值为0.0时表示关闭窗口边缘阴影。 |
| color | string | 否 | 表示窗口边缘阴影的颜色，为十六进制RGB或ARGB颜色，不区分大小写，例如`#00FF00`或`#FF00FF00`，默认值为'#000000'。 |
| offsetX | number | 否 | 表示窗口边缘阴影的X轴的偏移量。该参数为浮点数，单位为px，默认值为0.0。 |
| offsetY | number | 否 | 表示窗口边缘阴影的Y轴的偏移量。该参数为浮点数，单位为px，默认值为0.0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
try {
  windowClass.setShadow(4.0, '#FF00FF00', 2, 3);
} catch (exception) {
  console.error(`Failed to set shadow. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setSingleFrameComposerEnabled

```TypeScript
setSingleFrameComposerEnabled(enable: boolean): Promise<void>
```

禁止/使能单帧合成渲染节点的功能。使用Promise异步回调。

单帧合成渲染节点的功能主要用于跟手性要求较高的场景，使能该功能之后可以降低渲染节点的上屏延时。通过setSingleFrameComposerEnabled接口，如果enable设置为true，则使能单帧合成渲染节点的功能，否则禁止单帧合成渲染节点的功能。

**起始版本：** 11

<!--Device-Window-setSingleFrameComposerEnabled(enable: boolean): Promise<void>--><!--Device-Window-setSingleFrameComposerEnabled(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 设置单帧合成渲染节点的功能是否使能，true表示使能，false表示禁止。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let enable = true;
try {
  let promise = windowClass.setSingleFrameComposerEnabled(enable);
  promise.then(()=> {
      console.info('Succeeded in enabling the single-frame-composer function.');
  }).catch((err: BusinessError)=>{
      console.error(`Failed to enable the single-frame-composer function. code:${err.code}, message:${err.message}.`);
  });
} catch (exception) {
  console.error(`Failed to enable the single-frame-composer function. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setSnapshotSkip

```TypeScript
setSnapshotSkip(isSkip: boolean): void
```

截屏、录屏或投屏是否忽略当前窗口。此接口一般用于禁止截屏、录屏或投屏的场景。

若要实现窗口始终在前台忽略截屏、录屏或投屏，在窗口从后台回到前台时，需要通过[on('windowEvent')](arkts-arkui-window-window-i.md#on-22)监听窗口生命周期变化，在后台状态时设置为false，而在前台状态时设置为true。

**起始版本：** 9

<!--Device-Window-setSnapshotSkip(isSkip: boolean): void--><!--Device-Window-setSnapshotSkip(isSkip: boolean): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSkip | boolean | 是 | 截屏、录屏或投屏是否忽略当前窗口，默认为false。<br>true表示忽略当前窗口，false表示不忽略当前窗口。&lt;/br&gt; |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |

**示例：**

```TypeScript
let isSkip: boolean = true;
try {
  windowClass.setSnapshotSkip(isSkip);
} catch (exception) {
  console.error(`Failed to Skip. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setTitleButtonVisible

```TypeScript
setTitleButtonVisible(isMaximizeVisible: boolean, isMinimizeVisible: boolean, isSplitVisible: boolean): void
```

设置主窗标题栏上的最大化、最小化、分屏按钮是否可见。

仅对在当前场景下可见的标题栏按钮（最大化、最小化、分屏）生效。

**起始版本：** 12

<!--Device-Window-setTitleButtonVisible(isMaximizeVisible: boolean, isMinimizeVisible: boolean, isSplitVisible: boolean): void--><!--Device-Window-setTitleButtonVisible(isMaximizeVisible: boolean, isMinimizeVisible: boolean, isSplitVisible: boolean): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isMaximizeVisible | boolean | 是 | 设置最大化按钮是否可见，true为可见，false为隐藏。 |
| isMinimizeVisible | boolean | 是 | 设置最小化按钮是否可见，true为可见，false为隐藏。 |
| isSplitVisible | boolean | 是 | 设置分屏按钮是否可见，true为可见，false为隐藏。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // 加载主窗口对应的页面
    windowStage.loadContent('pages/Index', (err) => {
      if (err?.code) {
        console.error(`Failed to load content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      let mainWindow: window.Window | undefined = undefined;
      // 获取应用主窗口。
      windowStage.getMainWindow().then(
        data => {
          if (!data) {
            console.error('Failed to get main window.');
            return;
          }
          mainWindow = data;
          console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
          // 调用setTitleButtonVisible接口，隐藏主窗标题栏最大化、最小化、分屏按钮。
          mainWindow.setTitleButtonVisible(false, false, false);
        }
      ).catch((err: BusinessError) => {
          if(err.code){
            console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
          }
      });
    });
  }
}

```

## setTopmost

```TypeScript
setTopmost(isTopmost: boolean): Promise<void>
```

系统应用主窗口调用，实现将窗口置于所有应用窗口之上不被遮挡，使用Promise异步回调。

**起始版本：** 12

<!--Device-Window-setTopmost(isTopmost: boolean): Promise<void>--><!--Device-Window-setTopmost(isTopmost: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isTopmost | boolean | 是 | 是否将系统应用主窗口置顶，true表示置顶，false表示取消置顶。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // ...
    windowStage.getMainWindow().then((mainWindow) => {
      let isTopmost: boolean = true;
      mainWindow.setTopmost(isTopmost).then(() => {
        console.info('Succeeded in setting the main window to be topmost.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to set the main window to be topmost. Cause code: ${err.code}, message: ${err.message}`);
      });
    });
  }
}

```

## setTouchableAreas

```TypeScript
setTouchableAreas(rects: Array<Rect>): Promise<void>
```

实现设置窗口可触摸区域；不设置时默认整个窗口区域可触摸；设置窗口可触摸区域后，区域外触摸事件将被透传；如果窗口区域发生变化需要重新设置。

**起始版本：** 26.0.0

**需要权限：** 
- API版本26.0.0+：ohos.permission.SET_WINDOW_TOUCH_AREAS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Window-setTouchableAreas(rects: Array<Rect>): Promise<void>--><!--Device-Window-setTouchableAreas(rects: Array<Rect>): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rects | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<Rect> | 是 | 窗口可触摸区域。可触摸区域最大个数不能超过10个，且范围不能超出窗口区域。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required or a non-system application calls the API.<br>**适用版本：** 26.0.0+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12 - 24 |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible cause: Invalid parameter range. |

## setWakeUpScreen

```TypeScript
setWakeUpScreen(wakeUp: boolean): void
```

唤醒屏幕。

**起始版本：** 9

<!--Device-Window-setWakeUpScreen(wakeUp: boolean): void--><!--Device-Window-setWakeUpScreen(wakeUp: boolean): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wakeUp | boolean | 是 | 是否设置唤醒屏幕。true表示唤醒；false表示不唤醒。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
let wakeUp: boolean = true;
try {
  windowClass.setWakeUpScreen(wakeUp);
} catch (exception) {
  console.error(`Failed to wake up the screen. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setWaterMarkFlag

```TypeScript
setWaterMarkFlag(enable: boolean, callback: AsyncCallback<void>): void
```

为当前窗口添加或删除安全水印标志，使用callback异步回调。

**起始版本：** 10

<!--Device-Window-setWaterMarkFlag(enable: boolean, callback: AsyncCallback<void>): void--><!--Device-Window-setWaterMarkFlag(enable: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否对窗口添加标志位。true表示添加，false表示删除。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300008](../errorcode-window.md#1300008-显示设备异常) | The display device is abnormal. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let enable: boolean = true;
  windowClass.setWaterMarkFlag(enable, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set water mark flag of window. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting water mark flag of window.');
  });
} catch (exception) {
  console.error(`Failed to set water mark flag of window. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setWaterMarkFlag

```TypeScript
setWaterMarkFlag(enable: boolean): Promise<void>
```

为当前窗口添加或删除安全水印标志，使用Promise异步回调。

**起始版本：** 10

<!--Device-Window-setWaterMarkFlag(enable: boolean): Promise<void>--><!--Device-Window-setWaterMarkFlag(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否对窗口添加标志位。true表示添加，false表示删除。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300008](../errorcode-window.md#1300008-显示设备异常) | The display device is abnormal. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let enable = true;
  let promise = windowClass.setWaterMarkFlag(enable);
  promise.then(() => {
    console.info('Succeeded in setting water mark flag of window.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set water mark flag of window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set water mark flag of window. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## setWindowContainerModalColor

```TypeScript
setWindowContainerModalColor(activeColor: string, inactiveColor: string): void
```

设置主窗口容器在焦点态和非焦点态时的背景色。该接口需在调用[loadContent()](arkts-arkui-window-window-i.md#loadcontent-1)或[setUIContent()](arkts-arkui-window-window-i.md#setuicontent-1)后使用。

窗口容器背景色覆盖整个窗口区域，包括标题栏和内容区域。内容区域背景色默认跟随系统深浅色，当同时使用该接口和[setWindowBackgroundColor()](arkts-arkui-window-window-i.md#setwindowbackgroundcolor-1)设置背景色时，内容区域显示窗口背景色，标题栏显示窗口容器背景色。

**起始版本：** 26.0.0

**需要权限：** 
- API版本26.0.0+：ohos.permission.SET_WINDOW_ALPHA

<!--Device-Window-setWindowContainerModalColor(activeColor: string, inactiveColor: string): void--><!--Device-Window-setWindowContainerModalColor(activeColor: string, inactiveColor: string): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| activeColor | string | 是 | 窗口容器处于焦点态时的背景色，为十六进制RGB或ARGB颜色，不区分大小写，例如'#00FF00'或'#FF00FF00'。 |
| inactiveColor | string | 是 | 窗口容器处于非焦点态时的背景色，为十六进制RGB颜色或ARGB颜色，不区分大小写，例如'#00FF00'或'#FF00FF00'。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required or a non-system application calls the API.<br>**适用版本：** 26.0.0+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 20 - 24 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

## setWindowMode

```TypeScript
setWindowMode(mode: WindowMode): Promise<void>
```

设置主窗口模式，使用Promise异步回调。

**起始版本：** 9

<!--Device-Window-setWindowMode(mode: WindowMode): Promise<void>--><!--Device-Window-setWindowMode(mode: WindowMode): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WindowMode](../../apis-test-kit/arkts-apis/arkts-test-uitest-windowmode-e.md) | 是 | 窗口模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let mode = window.WindowMode.FULLSCREEN;
      try {
        let promise = windowClass.setWindowMode(mode);
        promise.then(() => {
          console.info('Succeeded in setting the window mode.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to set the window mode. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to set the window mode. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}

```

## setWindowMode

```TypeScript
setWindowMode(mode: WindowMode, callback: AsyncCallback<void>): void
```

设置主窗口模式，使用callback异步回调。

**起始版本：** 9

<!--Device-Window-setWindowMode(mode: WindowMode, callback: AsyncCallback<void>): void--><!--Device-Window-setWindowMode(mode: WindowMode, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WindowMode](../../apis-test-kit/arkts-apis/arkts-test-uitest-windowmode-e.md) | 是 | 窗口模式。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      const errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      let mode = window.WindowMode.FULLSCREEN;
      try {
        windowClass.setWindowMode(mode, (err: BusinessError) => {
          const errCode: number = err.code;
          if (errCode) {
            console.error(`Failed to set the window mode. Cause code: ${err.code}, message: ${err.message}`);
            return;
          }
          console.info('Succeeded in setting the window mode.');
        });
      } catch (exception) {
        console.error(`Failed to set the window mode. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}

```

## setWindowType

```TypeScript
setWindowType(type: WindowType): Promise<void>
```

设置窗口类型，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

<!--Device-Window-setWindowType(type: WindowType): Promise<void>--><!--Device-Window-setWindowType(type: WindowType): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [WindowType](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-windowtype-t.md) | 是 | 窗口类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let type = window.WindowType.TYPE_SYSTEM_ALERT;
let promise = windowClass.setWindowType(type);
promise.then(() => {
  console.info('Succeeded in setting the window type.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the window type. Cause code: ${err.code}, message: ${err.message}`);
});

```

## setWindowType

```TypeScript
setWindowType(type: WindowType, callback: AsyncCallback<void>): void
```

设置窗口类型，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

<!--Device-Window-setWindowType(type: WindowType, callback: AsyncCallback<void>): void--><!--Device-Window-setWindowType(type: WindowType, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [WindowType](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-windowtype-t.md) | 是 | 窗口类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let type = window.WindowType.TYPE_SYSTEM_ALERT;
windowClass.setWindowType(type, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to set the window type. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the window type.');
});

```

## showWithAnimation

```TypeScript
showWithAnimation(callback: AsyncCallback<void>): void
```

显示当前窗口，过程中播放动画，使用callback异步回调，仅支持系统窗口。

**起始版本：** 9

<!--Device-Window-showWithAnimation(callback: AsyncCallback<void>): void--><!--Device-Window-showWithAnimation(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation.Possible cause: Invalid window type. Only system windows are supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

windowClass.showWithAnimation((err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to show the window with animation. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in showing the window with animation.');
});

```

## showWithAnimation

```TypeScript
showWithAnimation(): Promise<void>
```

显示当前窗口，过程中播放动画，使用Promise异步回调，仅支持系统窗口。

**起始版本：** 9

<!--Device-Window-showWithAnimation(): Promise<void>--><!--Device-Window-showWithAnimation(): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. The window is not created or destroyed;2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation.Possible cause: Invalid window type. Only system windows are supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = windowClass.showWithAnimation();
promise.then(() => {
  console.info('Succeeded in showing the window with animation.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show the window with animation. Cause code: ${err.code}, message: ${err.message}`);
});

```

## translate

```TypeScript
translate(translateOptions: TranslateOptions): void
```

设置窗口平移参数。仅支持在[自定义系统窗口的显示与隐藏动画](../../../../windowmanager/system-window-stage-sys.md#自定义系统窗口的显示与隐藏动画)中使用。

**起始版本：** 9

<!--Device-Window-translate(translateOptions: TranslateOptions): void--><!--Device-Window-translate(translateOptions: TranslateOptions): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| translateOptions | [TranslateOptions](../arkts-components/arkts-arkui-common-translateoptions-i.md) | 是 | 平移参数，单位为px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. |

**示例：**

```TypeScript
let obj: window.TranslateOptions = {
  x: 100.0,
  y: 0.0,
  z: 0.0
};
try {
  windowClass.translate(obj);
} catch (exception) {
  console.error(`Failed to translate. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

