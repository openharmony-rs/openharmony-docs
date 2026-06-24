# getAllWindowLayoutInfo

## getAllWindowLayoutInfo

```TypeScript
function getAllWindowLayoutInfo(displayId: number): Promise<Array<WindowLayoutInfo>>
```

获取指定屏幕上可见的窗口布局信息数组，其中返回的每个Rect的宽、高是已经过缩放计算后的值，按当前窗口层级排列，层级最高的对应数组index为0，使用Promise异步回调。

**起始版本：** 15

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 需要获取窗口布局信息的displayId，该参数应为整数，且为当前实际存在屏幕的displayId，可以通过窗口属性<br/>[WindowProperties](arkts-arkui-window-windowproperties-i.md#WindowProperties)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;WindowLayoutInfo&gt;&gt; | Promise对象。返回获取到的窗口布局信息对象数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible cause:<br/>1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Function getAllWindowLayoutInfo can not work correctly due to limited device capabilities. |
| [1300002](../../errorcode-universal.md#1300002-This) | This window state is abnormal.&lt;br&gt;**适用版本：** 15 - 18 |
| [1300003](../../errorcode-universal.md#1300003-This) | This window manager service works abnormally.<br/>Possible cause: Internal task error. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let displayId = 0;
  let promise = window.getAllWindowLayoutInfo(displayId);
  promise.then((data) => {
    console.info('Succeeded in obtaining all window layout info. Data: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain all window layout info. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to obtain all window layout info. Cause code: ${exception.code}, message: ${exception.message}`);
}

```


## getAllWindowLayoutInfo

```TypeScript
function getAllWindowLayoutInfo(displayId: number, option?: WindowInfoOptions): Promise<Array<WindowLayoutInfo>>
```

根据option指定的过滤条件获取指定屏幕上可见的窗口布局信息数组，其中返回的每个Rect的宽、高是已经过缩放计算后的值，按当前窗口层级排列，层级最高的对应数组index为0，使用Promise异步回调。当未传入option或其中
的字段都为默认值时，当前接口与[getAllWindowLayoutInfo](arkts-arkui-window-getallwindowlayoutinfo-f.md#getAllWindowLayoutInfo-1)等价。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 需要获取窗口布局信息的displayId，该参数应为整数，且为当前实际存在屏幕的displayId，可以通过窗口属性<br/>[WindowProperties](arkts-arkui-window-windowproperties-i.md#WindowProperties)获取。 |
| option | WindowInfoOptions | 否 | 过滤选项。用于指定返回信息是否排除系统窗、比指定窗口层级更低或更高的窗口的信息。默认不过滤。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;WindowLayoutInfo&gt;&gt; | Promise对象。返回获取到的窗口布局信息对象数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Function getAllWindowLayoutInfo can not work correctly due to limited device capabilities. |
| [1300003](../../errorcode-universal.md#1300003-This) | This window manager service works abnormally.<br/>Possible cause: Internal task error. |
| [1300016](../../errorcode-universal.md#1300016-Parameter) | Parameter error. Possible cause: 1. Invalid parameter range. |

