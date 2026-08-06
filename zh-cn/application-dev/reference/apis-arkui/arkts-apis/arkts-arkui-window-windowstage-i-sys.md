# WindowStage

窗口管理器。管理各个基本窗口单元，即[Window]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_实例。 下列API示例中都需在[onWindowStageCreate()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_函数中使用WindowStage 的实例调用对应方法。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-window-interface WindowStage--><!--Device-window-interface WindowStage-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## disableWindowDecor

```TypeScript
disableWindowDecor(): void
```

禁止窗口装饰。 禁止窗口装饰后，当主窗口进入全屏沉浸状态时，此时鼠标Hover到上方窗口标题栏热区上会显示悬浮标题栏。若想禁用悬浮标题栏显示，请使用 [setTitleAndDockHoverShown()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowStage-disableWindowDecor(): void--><!--Device-WindowStage-disableWindowDecor(): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal. |

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

ArkTS-Dyn:
```TypeScript
setImageForRecent(imageResource: number | image.PixelMap, value: ImageFit): Promise<void>
```

ArkTS-Sta:
```TypeScript
setImageForRecent(imageResource: long | image.PixelMap, value: ImageFit): Promise<void>
```

设置应用在多任务中和Dock栏悬停时显示的图片，使用Promise异步回调。 > **说明：** > > 调用该接口前，建议先通过\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_方法或者\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_ > 方法完成页面加载。如果应用窗口未完成页面加载就直接调用该接口，功能将不会生效。此时多任务中只显示应用启动页。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**需要权限：** 
- API版本26.0.0+：ohos.permission.MANAGE_RECENT_SNAPSHOT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowStage-setImageForRecent(imageResource: long | image.PixelMap, value: ImageFit): Promise<void>--><!--Device-WindowStage-setImageForRecent(imageResource: long | image.PixelMap, value: ImageFit): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageResource | ArkTS-Dyn: number \| image.PixelMap  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long \| image.PixelMap | 是 | 应用自定义的图片资源，可传入资源id或PixelMap位图。传入资源id时，图片资源需放在resources/base/media目录下，通过\_\_\_ESCAPED\_DOLLAR\_\_\_r资源访问方式获取对应图片的资源id，这里以获取startIcon图片的资源id为例给出示意：\_\_\_ESCAPED\_DOLLAR\_\_\_r("app.media.startIcon").id。 |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 应用自定义图片的填充方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required or a non-system application calls the API.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 26.0.0+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 22 - 24 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:1. The window is not created or destroyed.2. The WindowStage is running in the background.3. Internal task error. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible cause:1. Invalid parameter range. 2. Invalid parameter length. |

## setImageForRecent

```TypeScript
setImageForRecent(imgResourceId: number, value: ImageFit): Promise<void>
```

设置应用在多任务中和Dock栏悬停时显示的图片，使用Promise异步回调。 > **说明：** > > 调用该接口前，建议先通过\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_方法或者\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_ > 方法完成页面加载。如果应用窗口未完成页面加载就直接调用该接口，功能将不会生效。此时多任务中只显示应用启动页。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowStage-setImageForRecent(imgResourceId: number, value: ImageFit): Promise<void>--><!--Device-WindowStage-setImageForRecent(imgResourceId: number, value: ImageFit): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imgResourceId | number | 是 | 应用自定义图片的资源id，图片资源需放在resources/base/media目录下，通过\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_资源访问方式获取对应图片的资源id，这里以获取startIcon图片的资源id为例给出示意：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 应用自定义图片的填充方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible cause:1. Invalid parameter range. 2. Invalid parameter length. 3. Incorrect parameter format. |

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

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowStage-setShowOnLockScreen(showOnLockScreen: boolean): void--><!--Device-WindowStage-setShowOnLockScreen(showOnLockScreen: boolean): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| showOnLockScreen | boolean | 是 | 是否设置应用显示在锁屏之上。true表示显示在锁屏之上；false表示不显示在锁屏之上。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300005](../errorcode-window.md#1300005-windowstage异常) | This window stage is abnormal. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

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
      let err = exception as BusinessError;
      console.error(`Failed to show on lockscreen. Cause code: ${err.code}, message: ${err.message}`);
    }
  }
};
```

