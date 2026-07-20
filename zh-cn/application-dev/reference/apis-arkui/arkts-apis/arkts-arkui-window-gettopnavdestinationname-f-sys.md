# getTopNavDestinationName（系统接口）

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

<a id="gettopnavdestinationname"></a>
## getTopNavDestinationName

```TypeScript
function getTopNavDestinationName(windowId: number): Promise<string>
```

获取指定的前台窗口当前栈顶[Navigation](../../apis-arkui/arkts-components/arkts-arkui-navigation-i)中的[NavDestination](../../apis-arkui/arkts-components/arkts-arkui-nav_destination-i)名称，使用Promise异步回调。

**起始版本：** 20

<!--Device-window-function getTopNavDestinationName(windowId: int): Promise<string>--><!--Device-window-function getTopNavDestinationName(windowId: int): Promise<string>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | number | 是 | 窗口Id，用于指定要查询的窗口。该参数应为大于0的整数，小于等于0时会返回错误码1300016，如果指定的窗口不存在或生命周期不在前台，返回错误码为1300002。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回获取到的[NavDestination](../../apis-arkui/arkts-components/arkts-arkui-nav_destination-i)名称。<br>对于[Navigation](../../apis-arkui/arkts-components/arkts-arkui-navigation-i)嵌套以及当前页面存在多个[Navigation](../../apis-arkui/arkts-components/arkts-arkui-navigation-i)的场景，查询的是后创建的[Navigation](../../apis-arkui/arkts-components/arkts-arkui-navigation-i)的信息。<br>如果页面没有[Navigation](../../apis-arkui/arkts-components/arkts-arkui-navigation-i)或者[Navigation](../../apis-arkui/arkts-components/arkts-arkui-navigation-i)中没有[NavDestination](../../apis-arkui/arkts-components/arkts-arkui-nav_destination-i)，返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, non-system application uses system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible cause: 1. Invalid parameter range. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let windowId = 10;
  let promise = window.getTopNavDestinationName(windowId);
  promise.then((data) => {
    console.info(`Succeeded, data: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed, cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed, exception code: ${exception.code}, message: ${exception.message}`);
}

```

