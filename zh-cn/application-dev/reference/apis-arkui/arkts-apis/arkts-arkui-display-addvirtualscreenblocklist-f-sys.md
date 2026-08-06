# addVirtualScreenBlocklist（系统接口）

## addVirtualScreenBlocklist

```TypeScript
function addVirtualScreenBlocklist(windowIds: Array<int>): Promise<void>
```

将窗口添加到禁止投屏显示的名单中，被添加的窗口无法在投屏时显示。仅对应用主窗或系统窗口生效。使用Promise异步回调。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-display-function addVirtualScreenBlocklist(windowIds: Array<int>): Promise<void>--><!--Device-display-function addVirtualScreenBlocklist(windowIds: Array<int>): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowIds | ArkTS-Dyn: Array&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;int&gt; | 是 | 窗口id列表，传入子窗窗口id时不生效。窗口id为大于0的整数。推荐使用\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_方法获取窗口id属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function addVirtualScreenBlocklist can not work correctly due to limited device capabilities. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { display, window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    // ...
    let windowId = windowStage.getMainWindowSync().getWindowProperties().id; // 获取窗口ID
    let windowIds = [windowId];

    // 将窗口添加到禁止投屏显示的名单
    let promise = display.addVirtualScreenBlocklist(windowIds);
    promise.then(() => {
      console.info('Succeeded in adding virtual screen blocklist.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to add virtual screen blocklist. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { display, window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    // ...
    let windowId = windowStage.getMainWindowSync().getWindowProperties().id; // 获取窗口ID
    let windowIds = [windowId];

    // 将窗口添加到禁止投屏显示的名单
    let promise = display.addVirtualScreenBlocklist(windowIds);
    promise.then(() => {
      console.info('Succeeded in adding virtual screen blocklist.');
    }).catch((err: Error) => {
      console.error(`Failed to add virtual screen blocklist. Code: ${err?.code} , message: ${err?.message}`);
    })
  }
}
```

