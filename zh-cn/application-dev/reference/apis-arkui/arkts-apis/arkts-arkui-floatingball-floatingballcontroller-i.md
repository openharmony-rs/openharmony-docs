# FloatingBallController

闪控球控制器实例，用于启动、更新、停止闪控球以及注册回调等操作。 下列API示例中都需先使用[floatingBall.create()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法获取到闪控球控制器实例（即floatingBallController），再通过此实例调用对应方法。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-floatingBall-interface FloatingBallController--><!--Device-floatingBall-interface FloatingBallController-End-->

**系统能力：** SystemCapability.Window.SessionManager

## getFloatingBallWindowInfo

```TypeScript
getFloatingBallWindowInfo(): Promise<FloatingBallWindowInfo>
```

获得闪控球窗口信息，使用Promise异步回调。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-FloatingBallController-getFloatingBallWindowInfo(): Promise<FloatingBallWindowInfo>--><!--Device-FloatingBallController-getFloatingBallWindowInfo(): Promise<FloatingBallWindowInfo>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FloatingBallWindowInfo&gt; | Promise对象，返回闪控球窗口信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:Internal error, the window type is not a floating ball. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally.Possible cause: Internal IPC error. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. Possible cause: The process ID calling the API does not match the process ID of the session that created the floating ball. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1. The floating ball controller has been destroyed.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. The floating ball window is not created or has been destroyed. |
| [1300025](../errorcode-window.md#1300025-闪控球状态不支持该操作) | The floating ball state does not support this operation. Possible cause:The floating ball is not started. |

**示例：**

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

floatingBallController.getFloatingBallWindowInfo().then((data: floatingBall.FloatingBallWindowInfo) => {
  console.info('Succeeded in getting floating ball window info. Info: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`Failed to get floating ball window info. Cause code: ${err.code}, message: ${err.message}`);
});
```

## off('stateChange')

```TypeScript
off(type: 'stateChange', callback?: Callback<FloatingBallState>): void
```

取消闪控球生命周期状态变化的监听事件。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-FloatingBallController-off(type: 'stateChange', callback?: Callback<FloatingBallState>): void--><!--Device-FloatingBallController-off(type: 'stateChange', callback?: Callback<FloatingBallState>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 监听事件，固定为'stateChange'，即闪控球生命周期状态变化事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FloatingBallState&gt; | 否 | 回调函数。返回当前的闪控球生命周期状态。若传入参数，则停止该监听。若未传入参数，则停止所有闪控球生命周期状态变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1.Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Callback is null or not callable. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball controller has been destroyed. |

**示例：**

```TypeScript
// xxx.ets

let onStateChange = (state: floatingBall.FloatingBallState) => {
  console.info('Floating ball stateChange: ' + state);
};
try {
  floatingBallController.off('stateChange', onStateChange);
} catch (e) {
  console.error(`Failed to off stateChange floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## off('click')

```TypeScript
off(type: 'click', callback?: Callback<void>): void
```

取消闪控球点击的监听事件。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-FloatingBallController-off(type: 'click', callback?: Callback<void>): void--><!--Device-FloatingBallController-off(type: 'click', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'click' | 是 | 监听事件，固定为'click'，即闪控球点击事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 回调函数。当点击闪控球事件发生时的回调。该回调函数不返回任何参数。若传入参数，则关闭特定的监听。若未传入参数，则关闭所有闪控球点击的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1.Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Callback is null or not callable. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball controller has been destroyed. |

**示例：**

```TypeScript
// xxx.ets

let onClick = () => {
  console.info('Floating ball onClick');
};
try {
  floatingBallController.off('click', onClick);
} catch (e) {
  console.error(`Failed to off click floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## offClick

```TypeScript
offClick(callback?: Callback<void>): void
```

Unregister floating ball click event listener.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-FloatingBallController-offClick(callback?: Callback<void>): void--><!--Device-FloatingBallController-offClick(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | Indicates the callback function. If not provided,all callbacks for the given event type will be removed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1.Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Callback is null or not callable. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball controller has been destroyed. |

**示例：**

```TypeScript
// xxx.ets

let onClickEvent = () => {
  console.info('Floating ball onClick');
};
try {
  floatingBallController.offClick(onClickEvent);
} catch(e: Error) {
  console.error(`Failed to off click floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## offDestroy

```TypeScript
offDestroy(callback?: Callback<string>): void
```

取消闪控球销毁事件的监听。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatingBallController-offDestroy(callback?: Callback<string>): void--><!--Device-FloatingBallController-offDestroy(callback?: Callback<string>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;string&gt; | 否 | 回调函数。若传入参数，则取消该监听；若未传入参数，则取消所有闪控球销毁事件的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible cause:Callback is null or not callable. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball controller has been destroyed. |

**示例：**

```TypeScript
let onDestroy = (reason: string) => {
  console.info('Floating ball has destroyed, reason: ' + reason);
};
try {
  floatingBallController?.offDestroy(onDestroy);
} catch(e) {
  console.error(`Failed to offDestroy floating ball. Cause:${e.code}, message:${e.message}`);
}
// 取消所有监听
try {
  floatingBallController?.offDestroy();
} catch(e) {
  console.error(`Failed to offDestroy all listeners. Cause:${e.code}, message:${e.message}`);
}
```

## offStateChange

```TypeScript
offStateChange(callback?: Callback<FloatingBallState>): void
```

Unregister floating ball stateChange event listener.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-FloatingBallController-offStateChange(callback?: Callback<FloatingBallState>): void--><!--Device-FloatingBallController-offStateChange(callback?: Callback<FloatingBallState>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FloatingBallState&gt; | 否 | Indicates the callback function. If not provided,all callbacks for the given event type will be removed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1.Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Callback is null or not callable. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball controller has been destroyed. |

**示例：**

```TypeScript
// xxx.ets

let onStateChangeEvent = (state: floatingBall.FloatingBallState) => {
  console.info(`Floating ball stateChange:${state}`);
};
try {
  floatingBallController.offStateChange(onStateChangeEvent);
} catch(e: Error) {
  console.error(`Failed to offStateChange floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## on('stateChange')

```TypeScript
on(type: 'stateChange', callback: Callback<FloatingBallState>): void
```

注册闪控球生命周期状态变化的监听事件。不再使用时，取消监听以避免内存泄漏。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-FloatingBallController-on(type: 'stateChange', callback: Callback<FloatingBallState>): void--><!--Device-FloatingBallController-on(type: 'stateChange', callback: Callback<FloatingBallState>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 监听事件，固定为'stateChange'，即闪控球生命周期状态变化事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FloatingBallState&gt; | 是 | 回调函数。返回当前的闪控球生命周期状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1.Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Callback is null or not callable. |
| [1300022](../errorcode-window.md#1300022-重复操作闪控球) | Repeated floating ball operation. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball controller has been destroyed. |

**示例：**

```TypeScript
// xxx.ets

let onStateChange = (state: floatingBall.FloatingBallState) => {
  console.info('Floating ball stateChange: ' + state);
};
try {
  floatingBallController.on('stateChange', onStateChange);
} catch (e) {
  console.error(`Failed to on stateChange floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## on('click')

```TypeScript
on(type: 'click', callback: Callback<void>): void
```

注册闪控球的点击监听事件，不使用时，取消监听以避免内存泄漏。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-FloatingBallController-on(type: 'click', callback: Callback<void>): void--><!--Device-FloatingBallController-on(type: 'click', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'click' | 是 | 监听事件，固定为'click'，即闪控球点击事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当点击闪控球事件发生时的回调。该回调函数不返回任何参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1.Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Callback is null or not callable. |
| [1300022](../errorcode-window.md#1300022-重复操作闪控球) | Repeated floating ball operation. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball controller has been destroyed. |

**示例：**

```TypeScript
// xxx.ets

let onClick = () => {
  console.info('Floating ball onClick');
};
try {
  floatingBallController.on('click', onClick);
} catch (e) {
  console.error(`Failed to on click floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## onClick

```TypeScript
onClick(callback: Callback<void>): void
```

Register floating ball click event listener.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-FloatingBallController-onClick(callback: Callback<void>): void--><!--Device-FloatingBallController-onClick(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | Used to handle {'click'} command. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1.Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Callback is null or not callable. |
| [1300022](../errorcode-window.md#1300022-重复操作闪控球) | Repeated floating ball operation. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball controller has been destroyed. |

**示例：**

```TypeScript
// xxx.ets

let onClickEvent = () => {
  console.info('Floating ball onClick');
};
try {
  floatingBallController.onClick(onClickEvent);
} catch(e: Error) {
  console.error(`Failed to on click floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## onDestroy

```TypeScript
onDestroy(callback: Callback<string>): void
```

注册闪控球销毁事件的监听。当闪控球销毁时，回调函数会接收到销毁原因的字符串。不再使用时，调用\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_接口取消监听以避免内存泄漏。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatingBallController-onDestroy(callback: Callback<string>): void--><!--Device-FloatingBallController-onDestroy(callback: Callback<string>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;string&gt; | 是 | 回调函数。返回闪控球停止的原因。停止原因包括：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- "APP\_\_\_ESCAPED\_UNDERSCORE\_\_\_STOP"：应用主动停止。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- "DUMPSTER\_\_\_ESCAPED\_UNDERSCORE\_\_\_STOP"：拖动到垃圾桶触发停止。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- "LONG\_\_\_ESCAPED\_UNDERSCORE\_\_\_PRESS\_\_\_ESCAPED\_UNDERSCORE\_\_\_SINGLE\_\_\_ESCAPED\_UNDERSCORE\_\_\_STOP"：长按单个闪控球触发停止。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- "LONG\_\_\_ESCAPED\_UNDERSCORE\_\_\_PRESS\_\_\_ESCAPED\_UNDERSCORE\_\_\_ALL\_\_\_ESCAPED\_UNDERSCORE\_\_\_STOP"：长按全部闪控球触发停止。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- "MAIN\_\_\_ESCAPED\_UNDERSCORE\_\_\_WINDOW\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESTROY\_\_\_ESCAPED\_UNDERSCORE\_\_\_STOP"：context关联的主窗口被销毁后触发停止。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- "SQUEEZE"：超出设备闪控球数量上限，被其他闪控球挤占停止。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- "FLOAT\_\_\_ESCAPED\_UNDERSCORE\_\_\_VIEW\_\_\_ESCAPED\_UNDERSCORE\_\_\_STOP"：与标准悬浮窗绑定后，绑定状态下跟随标准悬浮窗停止。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_7\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- "STOP\_\_\_ESCAPED\_UNDERSCORE\_\_\_IN\_\_\_ESCAPED\_UNDERSCORE\_\_\_SIDEBAR"：在侧边栏中被停止。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible cause:Callback is null or not callable. |
| [1300022](../errorcode-window.md#1300022-重复操作闪控球) | Repeated floating ball operation. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball controller has been destroyed. |

**示例：**

```TypeScript
let onDestroy = (reason: string) => {
  console.info('Floating ball has destroyed, reason: ' + reason);
};
try {
  floatingBallController?.onDestroy(onDestroy);
} catch(e) {
  console.error(`Failed to onDestroy floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## onStateChange

```TypeScript
onStateChange(callback: Callback<FloatingBallState>): void
```

Register floating ball stateChange event listener.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-FloatingBallController-onStateChange(callback: Callback<FloatingBallState>): void--><!--Device-FloatingBallController-onStateChange(callback: Callback<FloatingBallState>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FloatingBallState&gt; | 是 | Used to handle {'stateChange'} command. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1.Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Callback is null or not callable. |
| [1300022](../errorcode-window.md#1300022-重复操作闪控球) | Repeated floating ball operation. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball controller has been destroyed. |

**示例：**

```TypeScript
// xxx.ets

let onStateChangeEvent = (state: floatingBall.FloatingBallState) => {
  console.info(`Floating ball stateChange:${state}`);
};
try {
  floatingBallController.onStateChange(onStateChangeEvent);
} catch(e: Error) {
  console.error(`Failed to onStateChange floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## restoreMainWindow

```TypeScript
restoreMainWindow(want: Want): Promise<void>
```

恢复应用主窗口并加载指定页面。使用Promise异步回调。仅支持在点击闪控球后调用；若应用拥有\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_权限，可以无需点击直接调用该接口。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.USE_FLOAT_BALL

<!--Device-FloatingBallController-restoreMainWindow(want: Want): Promise<void>--><!--Device-FloatingBallController-restoreMainWindow(want: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 加载指定页面的Want。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually returned by VerifyAccessToken. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:Internal error, the window type is not a floating ball. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally.Possible cause: Internal IPC error. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. Possible cause: The process ID calling the API does not match the process ID of the session that created the floating ball. |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible cause:Want parameter is null or invalid. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1.The floating ball controller has been destroyed.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.The floating ball window is not created or has been destroyed. |
| [1300025](../errorcode-window.md#1300025-闪控球状态不支持该操作) | The floating ball state does not support this operation. Possible cause:The floating ball is not started. |
| [1300026](../errorcode-window.md#1300026-闪控球拉起应用窗口失败) | Failed to restore the main window. Possible causes:1. Invalid parameter. The provided bundleName does not match the caller's application bundleName.2. The application lacks the ohos.permission.AUTO\_\_\_ESCAPED\_UNDERSCORE\_\_\_RESTORE\_\_\_ESCAPED\_UNDERSCORE\_\_\_MAIN\_\_\_ESCAPED\_UNDERSCORE\_\_\_WINDOW permission,and no user interaction (click) on the floating ball has occurred. |

**示例：**

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let want: Want = {
  bundleName: 'xxx.xxx.xxx',
  abilityName: 'EntryAbility'
};
try {
  floatingBallController.restoreMainWindow(want).then(() => {
    console.info('Succeeded in restoring floating ball main window.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to restore floating ball main window. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error(`Failed to restore floating ball main window. Cause:${e.code}, message:${e.message}`);
}
```

## setFloatingBallVisibilityInApp

```TypeScript
setFloatingBallVisibilityInApp(isVisible: boolean): Promise<void>
```

设置闪控球在应用内是否可见。使用Promise异步回调。 - 当应用处于多任务界面时（\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_为PAUSED），闪控球不可见。 - 默认情况（即未调用此接口设置时）和调用此接口传入true时：除多任务界面外，闪控球均可见。 - 调用此接口传入false时：当应用处于前台（\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_为SHOWN或者RESUMED）时，闪控球不可见；当应用处于 后台（\_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_为HIDDEN）时，闪控球可见。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatingBallController-setFloatingBallVisibilityInApp(isVisible: boolean): Promise<void>--><!--Device-FloatingBallController-setFloatingBallVisibilityInApp(isVisible: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isVisible | boolean | 是 | true表示闪控球在应用内可见；false表示闪控球在应用内不可见。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally.Possible cause: Internal IPC error. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:The floating ball controller is null. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible causes:The floating ball window has not been created or has been destroyed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

floatingBallController?.setFloatingBallVisibilityInApp(false).then(() => {
  console.info('Succeeded in setting floating ball visibility.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set floating ball visibility. Cause code: ${err.code}, message: ${err.message}`);
});
```

## startFloatingBall

```TypeScript
startFloatingBall(params: FloatingBallParams): Promise<void>
```

启动闪控球，使用Promise异步回调。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.USE_FLOAT_BALL

<!--Device-FloatingBallController-startFloatingBall(params: FloatingBallParams): Promise<void>--><!--Device-FloatingBallController-startFloatingBall(params: FloatingBallParams): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 启动闪控球的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually returned by VerifyAccessToken. |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1. FloatingBallParams parameter is null.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Parameter is invalid, such as invalid icon object, template type,or title (empty or exceeds 64 bytes). |
| [1300020](../errorcode-window.md#1300020-创建闪控球窗口失败) | Failed to create the floating ball window. Possible cause:The main window is not shown. |
| [1300021](../errorcode-window.md#1300021-启动多个闪控球失败) | Failed to start multiple floating ball windows. |
| [1300022](../errorcode-window.md#1300022-重复操作闪控球) | Repeated floating ball operation. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1.The floating ball controller has been destroyed.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Internal error, failed to show the floating ball window.Such as insufficient resources or abnormal window service. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball window is not created or has been destroyed. |
| [1300025](../errorcode-window.md#1300025-闪控球状态不支持该操作) | The floating ball state does not support this operation. Possible cause:The floating ball state is stopping. |
| [1300034](../errorcode-window.md#1300034-闪控窗与其他悬浮窗口操作冲突) | This operation conflicts with other floating windows. Possible cause:App has already started float view.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

let startParams: floatingBall.FloatingBallParams = {
  template: floatingBall.FloatingBallTemplate.EMPHATIC,
  title: 'title',
  content: 'content'
};
try {
  floatingBallController.startFloatingBall(startParams).then(() => {
    console.info('Succeeded in starting floating ball.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to start floating ball. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to start floating ball. Cause:${e.code}, message:${e.message}`);
}
```

## stopFloatingBall

```TypeScript
stopFloatingBall(): Promise<void>
```

停止闪控球，使用Promise异步回调。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-FloatingBallController-stopFloatingBall(): Promise<void>--><!--Device-FloatingBallController-stopFloatingBall(): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300022](../errorcode-window.md#1300022-重复操作闪控球) | Repeated floating ball operation. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball window is not created or has been destroyed. |

**示例：**

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

floatingBallController.stopFloatingBall().then(() => {
  console.info('Succeeded in stopping floating ball.');
}).catch((err: BusinessError): void => {
  console.error(`Failed to stop floating ball. Cause:${err.code}, message:${err.message}`);
});
```

## updateFloatingBall

```TypeScript
updateFloatingBall(params: FloatingBallParams): Promise<void>
```

更新闪控球，使用Promise异步回调。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-FloatingBallController-updateFloatingBall(params: FloatingBallParams): Promise<void>--><!--Device-FloatingBallController-updateFloatingBall(params: FloatingBallParams): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 更新闪控球的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:Internal error, the window type is not a floating ball. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally.Possible cause: Internal IPC error. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. Possible cause: The process ID calling the API does not match the process ID of the session that created the floating ball. |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1.FloatingBallParams parameter is null.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Parameter is invalid, such as invalid icon object, template type,or title (empty or exceeds 64 bytes). |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. Possible cause:System error, such as a null pointer, insufficient memory. |
| [1300024](../errorcode-window.md#1300024-闪控球窗口状态异常) | The floating ball window state is abnormal. Possible cause:The floating ball window is not created or has been destroyed. |
| [1300025](../errorcode-window.md#1300025-闪控球状态不支持该操作) | The floating ball state does not support this operation. Possible cause:The floating ball is not started. |
| [1300027](../errorcode-window.md#1300027-更新闪控球时不能改变模板类型) | When updating the floating ball, the template type cannot be changed. |
| [1300028](../errorcode-window.md#1300028-不支持更新静态模板类型闪控球) | Updating static template-based floating balls is not supported. |

**示例：**

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

let updateParams: floatingBall.FloatingBallParams = {
  template: floatingBall.FloatingBallTemplate.EMPHATIC,
  title: 'title2',
  content: 'content2'
};
try {
  floatingBallController.updateFloatingBall(updateParams).then(() => {
    console.info('Succeeded in updating floating ball.');
  }).catch((err: BusinessError): void => {
    console.error(`Failed to update floating ball. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to update floating ball. Cause:${e.code}, message:${e.message}`);
}
```

