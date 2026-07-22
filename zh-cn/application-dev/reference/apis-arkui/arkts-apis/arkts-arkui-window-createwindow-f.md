# createWindow

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## createWindow

```TypeScript
function createWindow(config: Configuration, callback: AsyncCallback<Window>): void
```

创建子窗口或者系统窗口，使用callback异步回调。

非[自由窗口](../../../windowmanager/window-terminology.md#自由窗口)状态下，子窗口创建后默认是[沉浸式布局](../../../windowmanager/window-terminology.md#沉浸式布局)。

自由窗口状态下，子窗口参数[decorEnabled](arkts-arkui-window-configuration-i.md)为false时，子窗口创建后为沉浸式布局；子窗口参数decorEnabled为true，子窗口创建后为非沉浸式布局。

**起始版本：** 9

**需要权限：** 
- API版本12+：ohos.permission.SYSTEM_FLOAT_WINDOW

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-window-function createWindow(config: Configuration, callback: AsyncCallback<Window>): void--><!--Device-window-function createWindow(config: Configuration, callback: AsyncCallback<Window>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [Configuration](arkts-arkui-window-configuration-i.md) | 是 | 创建窗口时的参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Window&gt; | 是 | 回调函数。返回当前创建的窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.createWindow can not work correctly due to limited device capabilities.<br>**适用版本：** 12+ |
| [1300001](../errorcode-window.md#1300001-重复操作) | Repeated operation.Possible cause: The window has been created and can not be created again. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: Invalid parent window type, parent window cannot be a subWindow.<br>**适用版本：** 12+ |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. Possible cause: The window type in the configuration is invalid.<br>**适用版本：** 12+ |
| [1300006](../errorcode-window.md#1300006-窗口上下文异常) | This window context is abnormal. |
| [1300008](../errorcode-window.md#1300008-显示设备异常) | The display device is abnormal.<br>**适用版本：** 9 - 16 |
| [1300009](../errorcode-window.md#1300009-父窗口无效) | The parent window is invalid. |

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

非[自由窗口](../../../windowmanager/window-terminology.md#自由窗口)状态下，子窗口创建后默认是[沉浸式布局](../../../windowmanager/window-terminology.md#沉浸式布局)。

自由窗口状态下，子窗口参数[decorEnabled](arkts-arkui-window-configuration-i.md)为false时，子窗口创建后为沉浸式布局；子窗口参数decorEnabled为true，子窗口创建后为非沉浸式布局。

**起始版本：** 9

**需要权限：** 
- API版本12+：ohos.permission.SYSTEM_FLOAT_WINDOW

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-window-function createWindow(config: Configuration): Promise<Window>--><!--Device-window-function createWindow(config: Configuration): Promise<Window>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [Configuration](arkts-arkui-window-configuration-i.md) | 是 | 创建窗口时的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Window&gt; | Promise对象。返回当前创建的窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.createWindow can not work correctly due to limited device capabilities.<br>**适用版本：** 12+ |
| [1300001](../errorcode-window.md#1300001-重复操作) | Repeated operation.Possible cause: The window has been created and can not be created again. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: Invalid parent window type, parent window cannot be a subWindow.<br>**适用版本：** 12+ |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. Possible cause: The window type in the configuration is invalid.<br>**适用版本：** 12+ |
| [1300006](../errorcode-window.md#1300006-窗口上下文异常) | This window context is abnormal. |
| [1300008](../errorcode-window.md#1300008-显示设备异常) | The display device is abnormal.<br>**适用版本：** 9 - 16 |
| [1300009](../errorcode-window.md#1300009-父窗口无效) | The parent window is invalid. |

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

