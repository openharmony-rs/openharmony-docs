# WindowStage

窗口管理器。管理各个基本窗口单元，即[Window](arkts-window.md)实例。

下列API示例中都需在[onWindowStageCreate()](../../apis-ability-kit/arkts-apis/arkts-ability-uiability-c.md#onWindowStageCreate-1)函数中使用WindowStage
的实例调用对应方法。

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## disableWindowDecor

```TypeScript
disableWindowDecor(): void
```

禁止窗口装饰。

禁止窗口装饰后，当主窗口进入全屏沉浸状态时，此时鼠标Hover到上方窗口标题栏热区上会显示悬浮标题栏。若想禁用悬浮标题栏显示，请使用
[setTitleAndDockHoverShown()](arkts-arkui-window-window-i.md#setTitleAndDockHoverShown-1)接口。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system<br/>API.&lt;br&gt;**适用版本：** 12+ |
| [1300002](../../errorcode-universal.md#1300002-This) | This window state is abnormal. |
| [1300005](../../errorcode-universal.md#1300005-This) | This window stage is abnormal. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('disableWindowDecor');
    windowStage.disableWindowDecor();
  }
};

```

## setImageForRecent

```TypeScript
setImageForRecent(imgResourceId: number, value: ImageFit): Promise<void>
```

设置应用在多任务中和Dock栏悬停时显示的图片，使用Promise异步回调。
> **说明：**
>
> 调用该接口前，建议先通过[loadContent](#loadcontent9)方法或者[setUIContent](arkts-apis-window-Window.md#setuicontent9-1)
> 方法完成页面加载。如果应用窗口未完成页面加载就直接调用该接口，功能将不会生效。此时多任务中只显示应用启动页。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imgResourceId | number | 是 | 应用自定义图片的资源id，图片资源需放在resources/base/media目录下，通过`$r`资源访问方式获取对应图片的资源id，这里以获取<br/>startIcon图片的资源id为例给出示意：`$r("app.media.startIcon").id`。 |
| value | ImageFit | 是 | 应用自定义图片的填充方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |
| [1300002](../../errorcode-universal.md#1300002-This) | This window state is abnormal. |
| [1300003](../../errorcode-universal.md#1300003-This) | This window manager service works abnormally. |
| [1300016](../../errorcode-universal.md#1300016-Parameter) | Parameter error. Possible cause:<br/>1. Invalid parameter range. 2. Invalid parameter length. 3. Incorrect parameter format. |

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    let imgResourceId = $r("app.media.startIcon").id
    try {
      let promise = windowStage.setImageForRecent(imgResourceId, ImageFit.Fill);
      promise.then(() => {
        console.info(`Succeeded in setting image for recent`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to set image for recent. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to set image for recent.`);
    }
  }
};

```

## setShowOnLockScreen

```TypeScript
setShowOnLockScreen(showOnLockScreen: boolean): void
```

设置应用显示在锁屏之上。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| showOnLockScreen | boolean | 是 | 是否设置应用显示在锁屏之上。true表示显示在锁屏之上；false表示不显示在锁屏之上。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types. |
| [1300002](../../errorcode-universal.md#1300002-This) | This window state is abnormal. |
| [1300005](../../errorcode-universal.md#1300005-This) | This window stage is abnormal. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system<br/>API.&lt;br&gt;**适用版本：** 12+ |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  // ...

  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info('onWindowStageCreate');
    try {
      windowStage.setShowOnLockScreen(true);
    } catch (exception) {
      console.error(`Failed to show on lockscreen. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
};

```

