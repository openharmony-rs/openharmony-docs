# getVisibleWindowInfo（系统接口）

## getVisibleWindowInfo

```TypeScript
function getVisibleWindowInfo(): Promise<Array<WindowInfo>>
```

获取当前屏幕的可见主窗口（未退至后台的主窗口）信息。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.VISIBLE_WINDOW_INFO

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;WindowInfo&gt;&gt; | Promise对象，返回当前可见窗口的相关信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API.<br/>Possible cause: Need ohos.permission.VISIBLE_WINDOW_INFO permission.&lt;br&gt;**适用版本：** 18+ |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, non-system application uses system<br/>API.&lt;br&gt;**适用版本：** 12 - 17 |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Function getVisibleWindowInfo can not work correctly due to limited device capabilities. |
| [1300003](../../errorcode-universal.md#1300003-This) | This window manager service works abnormally.<br/>Possible cause: Internal task error. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = window.getVisibleWindowInfo();
  promise.then((data) => {
    data.forEach(windowInfo=>{
      console.info(`left:${windowInfo.rect.left}`);
      console.info(`top:${windowInfo.rect.top}`);
      console.info(`width:${windowInfo.rect.width}`);
      console.info(`height:${windowInfo.rect.height}`);
      console.info(`windowId:${windowInfo.windowId}`);
      console.info(`windowStatusType:${windowInfo.windowStatusType}`);
      console.info(`abilityName:${windowInfo.abilityName}`);
      console.info(`bundleName:${windowInfo.bundleName}`);
      console.info(`isFocused:${windowInfo.isFocused}`);
      console.info(`displayId:${windowInfo.displayId}`);
      console.info(`globalDisplayRect:${JSON.stringify(windowInfo.globalDisplayRect)}`);
      console.info(`globalRect:${JSON.stringify(windowInfo.globalRect)}`);
    })
  }).catch((err: BusinessError) => {
    console.error('Failed to getWindowInfo. Cause: ' + JSON.stringify(err));
  });
} catch (exception) {
  console.error(`Failed to get visible window info. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

