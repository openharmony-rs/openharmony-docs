# off

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

<a id="off"></a>
## off('add' | 'remove' | 'change')

```TypeScript
function off(type: 'add' | 'remove' | 'change', callback?: Callback<number>): void
```

关闭显示设备变化的监听。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function off(type: 'add' | 'remove' | 'change', callback?: Callback<long>): void--><!--Device-display-function off(type: 'add' | 'remove' | 'change', callback?: Callback<long>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'add' \| 'remove' \| 'change' | 是 | 监听事件。<br/>- type为"add"，表示增加显示设备事件。例如：插入显示器。<br/>- type为"remove"，表示移除显示设备事件。例如：移除显示器。<br/>- type为"change"，表示改变显示设备事件。例如：显示器方向改变。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;number&gt; | 否 | 需要取消注册的回调函数。返回监听到的屏幕ID，该参数为整数。若无此参数，则取消注册当前type类型事件监听的所有回调函数。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

**示例：**

```TypeScript
// 如果通过on注册多个callback，同时关闭所有callback监听
display.off('remove');

let callback: Callback<number> = (data: number) => {
  console.info(`Succeeded in unregistering the callback for display remove. Data: ${data}`)
};
// 关闭传入的callback监听
display.off('remove', callback);

```


<a id="off-1"></a>
## off('add' | 'remove' | 'change')

```TypeScript
function off(type: 'add' | 'remove' | 'change', callback?: Callback<number>): void
```

关闭显示设备变化的监听。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function off(type: 'add' | 'remove' | 'change', callback?: Callback<long>): void--><!--Device-display-function off(type: 'add' | 'remove' | 'change', callback?: Callback<long>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'add' \| 'remove' \| 'change' | 是 | 监听事件。<br/>- type为"add"，表示增加显示设备事件。例如：插入显示器。<br/>- type为"remove"，表示移除显示设备事件。例如：移除显示器。<br/>- type为"change"，表示改变显示设备事件。例如：显示器方向改变。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;number&gt; | 否 | 需要取消注册的回调函数。返回监听到的屏幕ID，该参数为整数。若无此参数，则取消注册当前type类型事件监听的所有回调函数。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

**示例：**

```TypeScript
// 如果通过on注册多个callback，同时关闭所有callback监听
display.off('remove');

let callback: Callback<number> = (data: number) => {
  console.info(`Succeeded in unregistering the callback for display remove. Data: ${data}`)
};
// 关闭传入的callback监听
display.off('remove', callback);

```


<a id="off-2"></a>
## off('add' | 'remove' | 'change')

```TypeScript
function off(type: 'add' | 'remove' | 'change', callback?: Callback<number>): void
```

关闭显示设备变化的监听。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function off(type: 'add' | 'remove' | 'change', callback?: Callback<long>): void--><!--Device-display-function off(type: 'add' | 'remove' | 'change', callback?: Callback<long>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'add' \| 'remove' \| 'change' | 是 | 监听事件。<br/>- type为"add"，表示增加显示设备事件。例如：插入显示器。<br/>- type为"remove"，表示移除显示设备事件。例如：移除显示器。<br/>- type为"change"，表示改变显示设备事件。例如：显示器方向改变。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;number&gt; | 否 | 需要取消注册的回调函数。返回监听到的屏幕ID，该参数为整数。若无此参数，则取消注册当前type类型事件监听的所有回调函数。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

**示例：**

```TypeScript
// 如果通过on注册多个callback，同时关闭所有callback监听
display.off('remove');

let callback: Callback<number> = (data: number) => {
  console.info(`Succeeded in unregistering the callback for display remove. Data: ${data}`)
};
// 关闭传入的callback监听
display.off('remove', callback);

```


<a id="off-3"></a>
## off('foldStatusChange')

```TypeScript
function off(type: 'foldStatusChange', callback?: Callback<FoldStatus>): void
```

关闭折叠设备折叠状态变化的监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function off(type: 'foldStatusChange', callback?: Callback<FoldStatus>): void--><!--Device-display-function off(type: 'foldStatusChange', callback?: Callback<FoldStatus>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'foldStatusChange' | 是 | 监听事件，固定为'foldStatusChange'，表示折叠设备折叠状态发生变化。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;FoldStatus&gt; | 否 | 需要取消注册的回调函数。表示折叠设备折叠状态。若无此参数，则取消注册折叠状态变化监听的所有回调函数。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
// 如果通过on注册多个callback，同时关闭所有callback监听
display.off('foldStatusChange');

let callback: Callback<display.FoldStatus> = (data: display.FoldStatus) => {
  console.info(`unregistering FoldStatus changes callback. Data: ${data}`);
};
// 关闭传入的callback监听
display.off('foldStatusChange', callback);

```


<a id="off-4"></a>
## off('foldAngleChange')

```TypeScript
function off(type: 'foldAngleChange', callback?: Callback<Array<number>>): void
```

关闭折叠设备折叠角度变化的监听。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function off(type: 'foldAngleChange', callback?: Callback<Array<double>>): void--><!--Device-display-function off(type: 'foldAngleChange', callback?: Callback<Array<double>>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'foldAngleChange' | 是 | 监听事件，固定为'foldAngleChange'表示折叠设备折叠角度发生变化。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;Array&lt;number&gt;&gt; | 否 | 需要取消注册的回调函数。表示折叠设备屏幕折叠角度值（0度~180度）。若无此参数，则取消注册折叠角度变化监听的所有回调函数。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

// 如果通过on注册多个callback，同时关闭所有callback监听
display.off('foldAngleChange');

let callback: Callback<Array<number>> = (angles: Array<number>) => {
  console.info('Listening fold angles length: ' + angles.length);
};
// 关闭传入的callback监听
display.off('foldAngleChange', callback);

```


<a id="off-5"></a>
## off('captureStatusChange')

```TypeScript
function off(type: 'captureStatusChange', callback?: Callback<boolean>): void
```

关闭设备的屏幕显示信息是否被获取的监听。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function off(type: 'captureStatusChange', callback?: Callback<boolean>): void--><!--Device-display-function off(type: 'captureStatusChange', callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureStatusChange' | 是 | 监听事件，固定为'captureStatusChange'表示设备的屏幕显示信息被获取的状态发生变化。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;boolean&gt; | 否 | 需要取消注册的回调函数。表示设备的屏幕显示信息是否被获取。true表示设备的屏幕显示信息开始被获取，包括处于截屏、投屏、录屏状态，或创建了虚拟屏幕(虚拟屏幕可能被应用获取屏幕图像)，截屏仅返回一次true；false表示获取结束。若无此参数，则取消注册设备的屏幕显示信息是否存在被获取监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

// 如果通过on注册多个callback，同时关闭所有callback监听
display.off('captureStatusChange');

let callback: Callback<boolean> = (captureStatus: boolean) => {
  console.info('Listening capture status: ' + captureStatus);
};
// 关闭传入的callback监听
display.off('captureStatusChange', callback);

```


<a id="off-6"></a>
## off('foldDisplayModeChange')

```TypeScript
function off(type: 'foldDisplayModeChange', callback?: Callback<FoldDisplayMode>): void
```

关闭折叠设备屏幕显示模式变化的监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function off(type: 'foldDisplayModeChange', callback?: Callback<FoldDisplayMode>): void--><!--Device-display-function off(type: 'foldDisplayModeChange', callback?: Callback<FoldDisplayMode>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'foldDisplayModeChange' | 是 | 监听事件，固定为'foldDisplayModeChange'，表示折叠设备屏幕显示模式发生变化。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;FoldDisplayMode&gt; | 否 | 需要取消注册的回调函数。表示折叠设备屏幕显示模式。若无此参数，则取消注册屏幕显示模式变化监听的所有回调函数。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

// 如果通过on注册多个callback，同时关闭所有callback监听
display.off('foldDisplayModeChange');

let callback: Callback<display.FoldDisplayMode> = (data: display.FoldDisplayMode) => {
  console.info(`unregistering FoldDisplayMode changes callback. Data: ${data}`);
};
// 关闭传入的callback监听
display.off('foldDisplayModeChange', callback);

```


<a id="off-7"></a>
## off('brightnessInfoChange')

```TypeScript
function off(type: 'brightnessInfoChange', callback?: BrightnessCallback<number, BrightnessInfo>): void
```

关闭所有屏幕亮度信息状态变化的监听。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-display-function off(type: 'brightnessInfoChange', callback?: BrightnessCallback<long, BrightnessInfo>): void--><!--Device-display-function off(type: 'brightnessInfoChange', callback?: BrightnessCallback<long, BrightnessInfo>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'brightnessInfoChange' | 是 | 监听事件，固定为'brightnessInfoChange'，表示屏幕亮度信息状态发生变化。 |
| callback | [BrightnessCallback](arkts-arkui-display-brightnesscallback-t.md)&lt;number, BrightnessInfo&gt; | 否 | 需要取消注册的回调函数。表示brightnessInfo状态发生改变。若无此参数，则取消所有注册brightnessInfo状态发生改变的回调函数。参数1为displayId，参数2为屏幕亮度信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |
| [1400004](../errorcode-display.md#1400004-参数异常) | Parameter error. Possible cause: 1. Invalid parameter range. |

**示例：**

```TypeScript
let callback: display.BrightnessCallback<number, display.BrightnessInfo> = (id: number, data: display.BrightnessInfo) => {
  console.info(`Listening enabled ${id}. Data: ${JSON.stringify(data)}`);
};
try {
  display.off('brightnessInfoChange', callback);
} catch (error) {
  console.error(`Failed to unregister brightnessInfoChange listener. Code ${error.code}, message: ${error.message}`);
}

```

