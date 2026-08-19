# getAllWindowLayoutInfo

## 导入模块

```TypeScript
import { floatingBall } from '@kit.ArkUI';
import { floatView } from '@kit.ArkUI';
import { window } from '@kit.ArkUI';
```

## getAllWindowLayoutInfo

```TypeScript
function getAllWindowLayoutInfo(displayId: long): Promise<Array<WindowLayoutInfo>>
```

获取指定屏幕上可见的窗口布局信息数组，其中返回的每个Rect的宽、高是已经过缩放计算后的值，按当前窗口层级排列，层级最高的对应数组index为0，使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-window-function getAllWindowLayoutInfo(displayId: long): Promise<Array<WindowLayoutInfo>>--><!--Device-window-function getAllWindowLayoutInfo(displayId: long): Promise<Array<WindowLayoutInfo>>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | long | 是 | 需要获取窗口布局信息的displayId，该参数应为整数，且为当前实际存在屏幕的displayId，可以通过窗口属性 [WindowProperties](arkts-arkui-window-windowproperties-i.md)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[WindowLayoutInfo](arkts-arkui-window-windowlayoutinfo-i.md)&gt;&gt; | Promise对象。返回获取到的窗口布局信息对象数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause: Internal task error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function getAllWindowLayoutInfo can not work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.<br>**适用版本：** 15 - 18 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let displayId = 0;
  let promise = window.getAllWindowLayoutInfo(displayId);
  promise.then((data) => {
    console.info(`Succeeded in obtaining all window layout info. Data: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain all window layout info. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to obtain all window layout info. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let displayId = 0;
  let promise = window.getAllWindowLayoutInfo(displayId);
  promise.then((data) => {
    console.info('Succeeded in obtaining all window layout info. Data: ' + JSON.stringify(data));
  }).catch((err: Error) => {
    console.error(`Failed to obtain all window layout info. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`Failed to obtain all window layout info. Cause code: ${error.code}, message: ${error.message}`);
}
```


## getAllWindowLayoutInfo

```TypeScript
function getAllWindowLayoutInfo(displayId: long, option?: WindowInfoOptions): Promise<Array<WindowLayoutInfo>>
```

根据option指定的过滤条件获取指定屏幕上可见的窗口布局信息数组，其中返回的每个Rect的宽、高是已经过缩放计算后的值，按当前窗口层级排列，层级最高的对应数组index为0，使用Promise异步回调。当未传入option或其中 的字段都为默认值时，当前接口与[getAllWindowLayoutInfo](#getallwindowlayoutinfo)等价。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-window-function getAllWindowLayoutInfo(displayId: long, option?: WindowInfoOptions): Promise<Array<WindowLayoutInfo>>--><!--Device-window-function getAllWindowLayoutInfo(displayId: long, option?: WindowInfoOptions): Promise<Array<WindowLayoutInfo>>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | long | 是 | 需要获取窗口布局信息的displayId，该参数应为整数，且为当前实际存在屏幕的displayId，可以通过窗口属性 [WindowProperties](arkts-arkui-window-windowproperties-i.md)获取。 |
| option | [WindowInfoOptions](arkts-arkui-window-windowinfooptions-i.md) | 否 | 过滤选项。用于指定返回信息是否排除系统窗、比指定窗口层级更低或更高的窗口的信息。默认不过滤。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[WindowLayoutInfo](arkts-arkui-window-windowlayoutinfo-i.md)&gt;&gt; | Promise对象。返回获取到的窗口布局信息对象数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. Possible cause: Internal task error. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function getAllWindowLayoutInfo can not work correctly due to limited device capabilities. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible cause: 1. Invalid parameter range. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let displayId = 0;
  let option: window.WindowInfoOptions = {
    excludeSystemWindows: false,
    foregroundAboveWindow: 0,
    foregroundBelowWindow: 0,
  };
  window.getAllWindowLayoutInfo(displayId, option).then((data) => {
    console.info('Succeeded in obtaining all window layout info. Data: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain all window layout info. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to obtain all window layout info. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let displayId = 0;
  let option: window.WindowInfoOptions = {
    excludeSystemWindows: false,
    foregroundAboveWindow: 0,
    foregroundBelowWindow: 0,
  };
  window.getAllWindowLayoutInfo(displayId, option).then((data) => {
    console.info('Succeeded in obtaining all window layout info. Data: ' + JSON.stringify(data));
  }).catch((err: Error) => {
    let error = err as BusinessError;
    console.error(`Failed to obtain all window layout info. Cause code: ${error.code}, message: ${error.message}`);
  });
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`Failed to obtain all window layout info. Cause code: ${error.code}, message: ${error.message}`);
}
```

