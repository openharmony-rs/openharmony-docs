# WindowProxy

UIExtension窗口代理。

**起始版本：** 12

<!--Device-uiExtension-interface WindowProxy--><!--Device-uiExtension-interface WindowProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiExtension } from '@kit.ArkUI';
```

<a id="hidenonsecurewindows"></a>
## hideNonSecureWindows

```TypeScript
hideNonSecureWindows(shouldHide: boolean): Promise<void>
```

设置是否隐藏不安全窗口，使用Promise异步回调。

> **说明：**  
>  
> - 不安全窗口是指可能遮挡[EmbeddedComponent](../../apis-arkui/arkts-components/arkts-arkui-embedded_component-i)（或  
> [UIExtensionComponent](../../apis-arkui/arkts-components/arkts-arkui-ui_extension_component-i)）组件的窗口，如全局悬浮窗、宿主子窗口和宿主创建的Dialog窗口  
> （不包括系统应用创建的上述类型窗口）。  
>  
> - 当EmbeddedComponent（或UIExtensionComponent）组件被用来显示敏感操作提示内容时，可以选择隐藏不安全窗口，保护敏感操作提示内容不会被遮挡。当EmbeddedComponent（或  
> UIExtensionComponent）组件不显示或销毁时，不安全窗口会重新显示。  
>  
> - 针对PC/2in1设备，当调用hideNonSecureWindows(true)时，不安全窗口中的全局悬浮窗不会被隐藏。

**起始版本：** 12

**需要权限：** ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowProxy-hideNonSecureWindows(shouldHide: boolean): Promise<void>--><!--Device-WindowProxy-hideNonSecureWindows(shouldHide: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shouldHide | boolean | 是 | 指示是否隐藏不安全窗口，true表示隐藏，false表示不隐藏。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes:1. Permission denied. Interface caller does not have permission "ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS".2. The UIExtension window proxy is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
// ExtensionProvider.ets

import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 隐藏非安全窗口
    extensionHostWindow.hideNonSecureWindows(true).then(()=> {
      console.info(`Succeeded in hiding the non-secure windows.`);
    }).catch((err: BusinessError)=> {
      console.error(`Failed to hide the non-secure windows. Cause:${JSON.stringify(err)}`);
    });
  }
  
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 取消隐藏非安全窗口
    extensionHostWindow.hideNonSecureWindows(false).then(()=> {
      console.info(`Succeeded in showing the non-secure windows.`);
    }).catch((err: BusinessError)=> {
      console.error(`Failed to show the non-secure windows. Cause:${JSON.stringify(err)}`);
    });
  }
}

```

<a id="setwatermarkflag"></a>
## setWaterMarkFlag

```TypeScript
setWaterMarkFlag(enable: boolean): Promise<void>
```

为当前窗口添加或删除安全水印标志，使用Promise异步回调。

> **说明：**  
>  
> 添加安全水印标志后，窗口在前台时会将当前全屏幕覆盖水印。全屏、悬浮窗、分屏等场景下只要有添加了安全水印标志的窗口在前台，就会显示全屏水印。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowProxy-setWaterMarkFlag(enable: boolean): Promise<void>--><!--Device-WindowProxy-setWaterMarkFlag(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否对窗口添加标志位。true表示添加，false表示删除。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | The UIExtension window proxy is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300008](../errorcode-window.md#1300008-显示设备异常) | The display device is abnormal. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 添加安全水印标志
    extensionHostWindow.setWaterMarkFlag(true).then(() => {
      console.info(`Succeeded in setting water mark flag of window.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to set water mark flag of window. Cause:${JSON.stringify(err)}`);
    });
  }
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 删除安全水印标志
    extensionHostWindow.setWaterMarkFlag(false).then(() => {
      console.info(`Succeeded in deleting water mark flag of window.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to delete water mark flag of window. Cause:${JSON.stringify(err)}`);
    });
  }
}

```

