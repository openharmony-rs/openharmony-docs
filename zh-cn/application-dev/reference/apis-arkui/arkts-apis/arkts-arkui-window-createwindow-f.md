# createWindow

## createWindow

```TypeScript
function createWindow(config: Configuration, callback: AsyncCallback<Window>): void
```

创建子窗口或者系统窗口，使用callback异步回调。

非[自由窗口](../../../../windowmanager/window-terminology.md#自由窗口)状态下，子窗口创建后默认是
[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)。

自由窗口状态下，子窗口参数[decorEnabled](arkts-arkui-window-configuration-i.md#Configuration)为false时，子窗口创建后为沉浸式布局；子窗口参数decorEnabled为true，子窗口
创建后为非沉浸式布局。

**起始版本：** 9

**需要权限：** ohos.permission.SYSTEM_FLOAT_WINDOW

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | Configuration | 是 | 创建窗口时的参数。 |
| callback | AsyncCallback&lt;Window&gt; | 是 | 回调函数。返回当前创建的窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.createWindow can not work correctly due to limited device<br/>capabilities.&lt;br&gt;**适用版本：** 12+ |
| [1300001](../../errorcode-universal.md#1300001-Repeated) | Repeated operation.<br/>Possible cause: The window has been created and can not be created again. |
| [1300002](../../errorcode-universal.md#1300002-This) | This window state is abnormal.<br/>Possible cause: Invalid parent window type, parent window cannot be a subWindow.&lt;br&gt;**适用版本：** 12+ |
| [1300004](../../errorcode-universal.md#1300004-Unauthorized) | Unauthorized operation. Possible cause: The window type in the configuration is<br/>invalid.&lt;br&gt;**适用版本：** 12+ |
| [1300006](../../errorcode-universal.md#1300006-This) | This window context is abnormal. |
| [1300008](../../errorcode-universal.md#1300008-The) | The display device is abnormal.&lt;br&gt;**适用版本：** 9 - 16 |
| [1300009](../../errorcode-universal.md#1300009-The) | The parent window is invalid. |

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    let windowClass: window.Window | undefined = undefined;
    let config: window.Configuration = {
      name: "test",
      windowType: window.WindowType.TYPE_DIALOG,
      ctx: this.context
    };
    try {
      window.createWindow(config, (err: BusinessError, data) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to create the window. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        windowClass = data;
        console.info('Succeeded in creating the window. Data: ' + JSON.stringify(data));
        windowClass.resize(500, 1000);
      });
    } catch (exception) {
      console.error(`Failed to create the window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}

```


## createWindow

```TypeScript
function createWindow(config: Configuration): Promise<Window>
```

创建子窗口或者系统窗口，使用Promise异步回调。

非[自由窗口](../../../../windowmanager/window-terminology.md#自由窗口)状态下，子窗口创建后默认是
[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)。

自由窗口状态下，子窗口参数[decorEnabled](arkts-arkui-window-configuration-i.md#Configuration)为false时，子窗口创建后为沉浸式布局；子窗口参数decorEnabled为true，子窗口
创建后为非沉浸式布局。

**起始版本：** 9

**需要权限：** ohos.permission.SYSTEM_FLOAT_WINDOW

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | Configuration | 是 | 创建窗口时的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Window&gt; | Promise对象。返回当前创建的窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.createWindow can not work correctly due to limited device<br/>capabilities.&lt;br&gt;**适用版本：** 12+ |
| [1300001](../../errorcode-universal.md#1300001-Repeated) | Repeated operation.<br/>Possible cause: The window has been created and can not be created again. |
| [1300002](../../errorcode-universal.md#1300002-This) | This window state is abnormal.<br/>Possible cause: Invalid parent window type, parent window cannot be a subWindow.&lt;br&gt;**适用版本：** 12+ |
| [1300004](../../errorcode-universal.md#1300004-Unauthorized) | Unauthorized operation. Possible cause: The window type in the configuration is<br/>invalid.&lt;br&gt;**适用版本：** 12+ |
| [1300006](../../errorcode-universal.md#1300006-This) | This window context is abnormal. |
| [1300008](../../errorcode-universal.md#1300008-The) | The display device is abnormal.&lt;br&gt;**适用版本：** 9 - 16 |
| [1300009](../../errorcode-universal.md#1300009-The) | The parent window is invalid. |

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    let windowClass: window.Window | undefined = undefined;
    let config: window.Configuration = {
      name: "test",
      windowType: window.WindowType.TYPE_DIALOG,
      ctx: this.context
    };
    try {
      window.createWindow(config).then((value:window.Window) => {
        console.info('Succeeded in creating the window. Data: ' + JSON.stringify(value));
        windowClass = value;
        windowClass.resize(500, 1000);
      }).catch((err:BusinessError)=> {
        console.error(`Failed to create the window. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to create the window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}

```

