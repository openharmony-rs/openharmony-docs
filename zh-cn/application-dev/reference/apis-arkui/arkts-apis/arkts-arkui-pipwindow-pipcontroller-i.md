# PiPController

画中画控制器实例。用于启动、停止画中画以及更新回调注册等。

下列API示例中都需先使用[PiPWindow.create()](arkts-arkui-pipwindow-create-f.md#create-1)方法获取到PiPController实例，再通过此实例调用对应方
法。

**起始版本：** 11

**系统能力：** SystemCapability.Window.SessionManager

## getPiPSettingSwitch

```TypeScript
getPiPSettingSwitch(): Promise<boolean>
```

获取设置中自动启动画中画开关的状态，使用Promise异步回调。

**起始版本：** 20

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回当前自动启动画中画开关状态，true表示开启，false表示关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |
| [1300014](../../errorcode-universal.md#1300014-PiP) | PiP internal error. |

**示例：**

```TypeScript
let pipSwitchStatus: boolean | undefined = undefined;
try {
  let promise : Promise<boolean> = this.pipController.getPiPSettingSwitch();
  promise.then((data) => {
    pipSwitchStatus = data;
    console.info('Succeeded in getting pip switch status. switchStatus: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`Failed to get pip switch status. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to get pip switch status. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## getPiPWindowInfo

```TypeScript
getPiPWindowInfo(): Promise<PiPWindowInfo>
```

获取画中画窗口信息，使用Promise异步回调。

**起始版本：** 15

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PiPWindowInfo&gt; | Promise对象，返回当前画中画窗口信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |
| [1300014](../../errorcode-universal.md#1300014-PiP) | PiP internal error. |

**示例：**

```TypeScript
let pipWindowInfo: PiPWindow.PiPWindowInfo | undefined = undefined;
try {
  let promise : Promise<PiPWindow.PiPWindowInfo> = this.pipController.getPiPWindowInfo();
  promise.then((data) => {
    pipWindowInfo = data;
    console.info('Success in get pip window info. Info: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`Failed to get pip window info. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to get pip window info. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## isPiPActive

```TypeScript
isPiPActive(): Promise<boolean>
```

获取画中画的隐藏状态。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回当前画中画的隐藏状态。true表示前台可见，false表示前台不可见（收入侧边栏）。画中画生命周期不为<br/>[STARTED](arkts-arkui-pipwindow-pipstate-e.md#PiPState)时调用本接口总是返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300014](../../errorcode-universal.md#1300014-PiP) | PiP internal error. |

**示例：**

```TypeScript
let pipActiveStatus: boolean | undefined = undefined;
try {
  let promise : Promise<boolean> | undefined = this.pipController?.isPiPActive();
  promise?.then((data) => {
    pipActiveStatus = data;
    console.info('Succeeded in getting pip active status. activeStatus: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`Failed to get pip active status. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to get pip active status. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## off

```TypeScript
off(type: 'stateChange'): void
```

关闭画中画生命周期状态变化的监听。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 事件类型，固定为'stateChange'，即画中画生命周期状态变化事件。 |

**示例：**

```TypeScript
this.pipController.off('stateChange');

```

## off

```TypeScript
off(type: 'controlPanelActionEvent'): void
```

关闭画中画控制面板控件动作事件的监听。推荐使用
[off('controlEvent')](arkts-arkui-pipwindow-pipcontroller-i.md#off-3)
来关闭画中画控制面板控件动作事件的监听。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'controlPanelActionEvent' | 是 | 事件类型，固定为'controlPanelActionEvent'，即画中画控制面板控件动作事件。 |

**示例：**

```TypeScript
this.pipController.off('controlPanelActionEvent');

```

## off('controlEvent')

```TypeScript
off(type: 'controlEvent', callback?: Callback<ControlEventParam>): void
```

关闭画中画控制面板控件动作事件的监听。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'controlEvent' | 是 | 事件类型，固定为'controlEvent'，即画中画控制面板控件动作事件。 |
| callback | Callback&lt;ControlEventParam&gt; | 否 | 描述画中画控制面板控件动作事件回调。如果未传入参数，解除type为'controlEvent'的所有回调。 |

**示例：**

```TypeScript
let callbackFunc = (event: PiPWindow.ControlEventParam) => {
  console.info(`receive control event: ${event.controlType}, ${event.status}`);
}
this.pipController.off('controlEvent', callbackFunc);

```

## off('pipWindowSizeChange')

```TypeScript
off(type: 'pipWindowSizeChange', callback?: Callback<PiPWindowSize>): void
```

关闭画中画窗口尺寸变化事件的监听。

**起始版本：** 15

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'pipWindowSizeChange' | 是 | 事件类型，固定为'pipWindowSizeChange'，即画中画窗口尺寸变化事件。 |
| callback | Callback&lt;PiPWindowSize&gt; | 否 | 回调函数。返回当前画中画窗口的尺寸。如果传入参数，则关闭该监听。如果未传入参数，解除type为'pipWindowSizeChange<br/>'的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |

**示例：**

```TypeScript
const callback = (size: PiPWindow.PiPWindowSize) => {
  // ...
}
try {
  // 通过on接口开启监听
  this.pipController.on('pipWindowSizeChange', callback);
} catch (exception) {
  console.error(`Failed to enable the listener for pip window size changes. Cause code: ${exception.code}, message: ${exception.message}`);
}

try {
  // 关闭指定callback的监听
  this.pipController.off('pipWindowSizeChange', callback);
  // 如果通过on开启多个callback进行监听，同时关闭所有监听：
  this.pipController.off('pipWindowSizeChange');
} catch (exception) {
  console.error(`Failed to disable the listener for pip window size changes. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## off('activeStatusChange')

```TypeScript
off(type: 'activeStatusChange', callback?: Callback<boolean>): void
```

关闭画中画窗口隐藏状态变化事件的监听。

**起始版本：** 22

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'activeStatusChange' | 是 | 事件类型，固定为'activeStatusChange'，即画中画隐藏状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 否 | 返回当前画中画的隐藏状态。true表示前台可见，false表示前台不可见（收入侧边栏）。如果未传入参数，解除type为'<br/>activeStatusChange'的所有回调。 |

**示例：**

```TypeScript
let callback = (activeStatus: boolean) => {
  console.info(`pip window is visible: ${activeStatus}`);
}
this.pipController.off('activeStatusChange', callback);

```

## on('stateChange')

```TypeScript
on(type: 'stateChange', callback: (state: PiPState, reason: string) => void): void
```

开启画中画生命周期状态变化的监听，建议在不需要使用时关闭监听，否则可能存在内存泄漏。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 事件类型，固定为'stateChange'，即画中画生命周期状态变化事件。 |
| callback | (state: PiPState, reason: string) =&gt; void | 是 | 回调生命周期状态变化事件以及原因。<br/>state：[PiPState](arkts-arkui-pipwindow-pipstate-e.md#PiPState)，表示当前画中画生命周期状态。<br/><br/>reason：string，表示当前生命周期的切换原因。<br/><br/>在OpenHarmony 6.1之前，reason始终为“0”，无需关注。<br/><br/>从OpenHarmony 6.1开始，reason为当前生命周期的切换原因：<br/><br/>"requestStart"：应用调用startPip接口；<br/><br/>"autoStart"：应用退后台触发画中画自动启动；<br/><br/>"requestDelete"：应用调用stopPip接口；<br/><br/>"panelActionDelete"：用户点击画中画窗口的关闭按钮；<br/><br/>"dragDelete"：用户将画中画窗口拖入垃圾桶；<br/><br/>"panelActionRestore"：用户点击画中画窗口的还原按钮（无还原按钮时可点击画中画窗口）触发还原；<br/><br/>"other"：其他原因，如新的画中画窗口拉起导致当前窗口被关闭、应用主窗口被关闭等场景。 |

**示例：**

```TypeScript
this.pipController.on('stateChange', (state: PiPWindow.PiPState, reason: string) => {
  let curState: string = '';
  switch (state) {
    case PiPWindow.PiPState.ABOUT_TO_START:
      curState = 'ABOUT_TO_START';
      break;
    case PiPWindow.PiPState.STARTED:
      curState = 'STARTED';
      break;
    case PiPWindow.PiPState.ABOUT_TO_STOP:
      curState = 'ABOUT_TO_STOP';
      break;
    case PiPWindow.PiPState.STOPPED:
      curState = 'STOPPED';
      break;
    case PiPWindow.PiPState.ABOUT_TO_RESTORE:
      curState = 'ABOUT_TO_RESTORE';
      break;
    case PiPWindow.PiPState.ERROR:
      curState = 'ERROR';
      break;
    default:
      break;
  }
  console.info('stateChange:' + curState + ' reason:' + reason);
});

```

## on('controlPanelActionEvent')

```TypeScript
on(type: 'controlPanelActionEvent', callback: ControlPanelActionEventCallback): void
```

开启画中画控制面板控件动作事件的监听，建议在不需要使用时关闭监听，否则可能存在内存泄漏。推荐使用
[on('controlEvent')](arkts-arkui-pipwindow-pipcontroller-i.md#on-3)
来开启画中画控制面板控件动作事件的监听。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'controlPanelActionEvent' | 是 | 事件类型，固定为'controlPanelActionEvent'，即画中画控制面板控件动作事件。 |
| callback | ControlPanelActionEventCallback | 是 | 描述画中画控制面板控件动作事件回调。 [since 12] |

**示例：**

```TypeScript
this.pipController.on('controlPanelActionEvent', (event: PiPWindow.PiPActionEventType, status?: number) => {
  switch (event) {
    case 'playbackStateChanged':
      if (status === 0) {
        // 停止视频
      } else if (status === 1) {
        // 播放视频
      }
      break;
    case 'nextVideo':
      // 切换到下一个视频
      break;
    case 'previousVideo':
      // 切换到上一个视频
      break;
    case 'fastForward':
      // 视频进度快进
      break;
    case 'fastBackward':
      // 视频进度后退
      break;
    default:
      break;
  }
  console.info('registerActionEventCallback, event:' + event);
});

```

## on('controlEvent')

```TypeScript
on(type: 'controlEvent', callback: Callback<ControlEventParam>): void
```

开启画中画控制面板控件动作事件的监听，建议在不需要使用时关闭监听，否则可能存在内存泄漏。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'controlEvent' | 是 | 事件类型，固定为'controlEvent'，即画中画控制面板控件动作事件。 |
| callback | Callback&lt;ControlEventParam&gt; | 是 | 描述画中画控制面板控件动作事件回调。 |

**示例：**

```TypeScript
this.pipController.on('controlEvent', (control) => {
  switch (control.controlType) {
    case PiPWindow.PiPControlType.VIDEO_PLAY_PAUSE:
      if (control.status === PiPWindow.PiPControlStatus.PAUSE) {
        // 停止视频
      } else if (control.status === PiPWindow.PiPControlStatus.PLAY) {
        // 播放视频
      }
      break;
    case PiPWindow.PiPControlType.VIDEO_NEXT:
      // 切换到下一个视频
      break;
    case PiPWindow.PiPControlType.VIDEO_PREVIOUS:
      // 切换到上一个视频
      break;
    case PiPWindow.PiPControlType.FAST_FORWARD:
      // 视频进度快进
      break;
    case PiPWindow.PiPControlType.FAST_BACKWARD:
      // 视频进度后退
      break;
    default:
      break;
  }
  console.info('registerControlEventCallback, controlType:' + control.controlType + ', status' + control.status);
});

```

## on('pipWindowSizeChange')

```TypeScript
on(type: 'pipWindowSizeChange', callback: Callback<PiPWindowSize>): void
```

开启画中画窗口尺寸变化事件的监听，建议在不需要使用时关闭监听，否则可能存在内存泄漏。

**起始版本：** 15

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'pipWindowSizeChange' | 是 | 事件类型，固定为'pipWindowSizeChange'，即画中画窗口尺寸变化事件。 |
| callback | Callback&lt;PiPWindowSize&gt; | 是 | 回调函数。返回当前画中画窗口的尺寸。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |
| [1300014](../../errorcode-universal.md#1300014-PiP) | PiP internal error. |

**示例：**

```TypeScript
try {
  this.pipController.on('pipWindowSizeChange', (size: PiPWindow.PiPWindowSize) => {
    console.info('Succeeded in enabling the listener for pip window size changes. size: ' + JSON.stringify(size));
  });
} catch (exception) {
  console.error(`Failed to enable the listener for pip window size changes. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

## on('activeStatusChange')

```TypeScript
on(type: 'activeStatusChange', callback: Callback<boolean>): void
```

开启画中画窗口隐藏状态变化事件的监听，建议在不需要使用时关闭监听，否则可能存在内存泄漏。

**起始版本：** 22

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'activeStatusChange' | 是 | 事件类型，固定为'activeStatusChange'，即画中画隐藏状态变化事件。 |
| callback | Callback&lt;boolean&gt; | 是 | 返回当前画中画的隐藏状态。true表示前台可见，false表示前台不可见（收入侧边栏）。 |

**示例：**

```TypeScript
let callback = (activeStatus: boolean) => {
  console.info(`pip window is visible: ${activeStatus}`);
}
this.pipController.on('activeStatusChange', callback);

```

## setAutoStartEnabled

```TypeScript
setAutoStartEnabled(enable: boolean): void
```

设置是否在返回桌面时自动启动画中画，默认不自动拉起。

在使用XComponent方案实现画中画功能并结合Navigation进行路由管理时，首次调用setAutoStartEnabled(true)方法，系统会缓存当前应用传入的NavigationId的栈顶信息。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 如返回桌面时需自动启动画中画，则该参数配置为true，否则为false。若设置-系统-智慧多窗-自动启动画中画开关为关闭状态，就算该参数配置为true，应用返回桌面时也不<br/>会自动启动画中画窗口。 |

**示例：**

```TypeScript
let enable: boolean = true;
this.pipController.setAutoStartEnabled(enable);

```

## setPiPControlEnabled

```TypeScript
setPiPControlEnabled(controlType: PiPControlType, enabled: boolean): void
```

更新控制面板控件使能状态。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controlType | PiPControlType | 是 | 表示画中画控制面板控件类型。 |
| enabled | boolean | 是 | 表示画中画控制面板控件使能状态。true表示控件为可使用状态，false则为禁用状态。 |

**示例：**

```TypeScript
let controlType: PiPWindow.PiPControlType = PiPWindow.PiPControlType.VIDEO_PLAY_PAUSE; // 视频播放控制面板中播放/暂停控件。
let enabled: boolean = false; // 视频播放控制面板中播放/暂停控件为禁用状态。
this.pipController.setPiPControlEnabled(controlType, enabled);

```

## startPiP

```TypeScript
startPiP(): Promise<void>
```

启动画中画，使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300012](../../errorcode-universal.md#1300012-The) | The PiP window state is abnormal. |
| [1300013](../../errorcode-universal.md#1300013-Failed) | Failed to create the PiP window. |
| [1300014](../../errorcode-universal.md#1300014-PiP) | PiP internal error. |
| [1300015](../../errorcode-universal.md#1300015-Repeated) | Repeated PiP operation. |
| [1300034](../../errorcode-universal.md#1300034-This) | This operation conflicts with other floating windows. Possible cause:<br/>App has already started float view.&lt;br&gt;**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
// 开发者可根据pipController的定义方式自行实现pipController的调用
let promise : Promise<void> = this.pipController.startPiP();
promise.then(() => {
  console.info(`Succeeded in starting pip.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to start pip. Cause:${err.code}, message:${err.message}`);
});

```

## stopPiP

```TypeScript
stopPiP(): Promise<void>
```

停止画中画，使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300011](../../errorcode-universal.md#1300011-Failed) | Failed to destroy the PiP window. |
| [1300012](../../errorcode-universal.md#1300012-The) | The PiP window state is abnormal. |
| [1300015](../../errorcode-universal.md#1300015-Repeated) | Repeated PiP operation. |

**示例：**

```TypeScript
let promise : Promise<void> = this.pipController.stopPiP();
promise.then(() => {
  console.info(`Succeeded in stopping pip.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to stop pip. Cause:${err.code}, message:${err.message}`);
});

```

## updateContentNode

```TypeScript
updateContentNode(contentNode: typeNode.XComponent): Promise<void>
```

更新画中画节点内容，使用Promise异步回调。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contentNode | typeNode.XComponent | 是 | 用于渲染画中画窗口中的内容。该参数不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |
| [1300014](../../errorcode-universal.md#1300014-PiP) | PiP internal error. |

**示例：**

```TypeScript
import { typeNode, UIContext } from '@kit.ArkUI';

let context: UIContext | undefined = undefined; // 可传入UIContext或在布局中通过this.getUIContext()为context赋有效值

try {
  let contentNode = typeNode.createNode(context, "XComponent");
  this.pipController.updateContentNode(contentNode);
} catch (exception) {
  console.error(`Failed to update content node. Cause: ${exception.code}, message: ${exception.message}`);
}

```

## updateContentSize

```TypeScript
updateContentSize(width: number, height: number): void
```

当媒体源切换时，向画中画控制器更新媒体源尺寸信息。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 表示媒体内容宽度，必须为大于0的整数，单位为px。用于更新画中画窗口比例。 |
| height | number | 是 | 表示媒体内容高度，必须为大于0的整数，单位为px。用于更新画中画窗口比例。 |

**示例：**

```TypeScript
let width: number = 540; // 假设当前内容宽度变为540px。
let height: number = 960; // 假设当前内容高度变为960px。
this.pipController.updateContentSize(width, height);

```

## updatePiPControlStatus

```TypeScript
updatePiPControlStatus(controlType: PiPControlType, status: PiPControlStatus): void
```

更新画中画控制面板控件功能状态。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controlType | PiPControlType | 是 | 表示画中画控制面板控件类型。目前仅支持VIDEO_PLAY_PAUSE、MICROPHONE_SWITCH、CAMERA_SWITCH和<br/>MUTE_SWITCH这几种控件类型，传入其他控件类型不生效也不报错。 |
| status | PiPControlStatus | 是 | 表示画中画控制面板控件状态。 |

**示例：**

```TypeScript
let controlType: PiPWindow.PiPControlType = PiPWindow.PiPControlType.VIDEO_PLAY_PAUSE; // 视频播放控制面板中播放/暂停控件。
let status: PiPWindow.PiPControlStatus = PiPWindow.PiPControlStatus.PLAY; // 视频播放控制面板中播放/暂停控件为播放状态。
this.pipController.updatePiPControlStatus(controlType, status);

```

