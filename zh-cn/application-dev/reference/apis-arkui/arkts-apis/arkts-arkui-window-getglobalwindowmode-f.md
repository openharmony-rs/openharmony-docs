# getGlobalWindowMode

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

<a id="getglobalwindowmode"></a>
## getGlobalWindowMode

```TypeScript
function getGlobalWindowMode(displayId?: number): Promise<number>
```

获取指定屏幕上生命周期位于前台的窗口对应的窗口模式，使用Promise异步回调。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-window-function getGlobalWindowMode(displayId?: long): Promise<int>--><!--Device-window-function getGlobalWindowMode(displayId?: long): Promise<int>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 否 | 可选的屏幕ID，用于获取对应屏幕上的窗口模式信息。该参数应为大于等于0的整数，小于0时会返回错误码1300016，不传或传值为null以及undefined则代表查询所有屏幕，传入非整数会忽略掉小数部分。如果指定的屏幕不存在，返回值为0，推荐使用[getWindowProperties()](arkts-arkui-window-window-i.md#getwindowproperties-1)方法获取窗口所在屏幕ID属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回获取到的窗口模式。每一个二进制位代表一种窗口模式，当前支持的窗口模式见[GlobalWindowMode](arkts-arkui-window-globalwindowmode-e.md)，返回值为对应窗口模式值按位进行或运算的结果。比如，当前屏幕上存在全屏窗口、悬浮窗和画中画三种窗口，则返回值为`0b1\|0b100\|0b1000 = 13`。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function getGlobalWindowMode can not work correctly due to limited device capabilities. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally.Possible cause: Internal task error. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible cause: 1. Invalid parameter range;2. The parameter format is incorrect. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let displayId = 0;
  let promise = window.getGlobalWindowMode(displayId);
  promise.then((data) => {
    console.info(`Succeeded in obtaining global window mode. Data: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain global window mode. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to obtain global window mode. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

