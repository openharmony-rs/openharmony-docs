# UIExtensionHostWindowProxy（系统接口）

Transition Controller

**起始版本：** 11

<!--Device-uiExtensionHost-interface UIExtensionHostWindowProxy--><!--Device-uiExtensionHost-interface UIExtensionHostWindowProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiExtensionHost } from '@kit.ArkUI';
```

<a id="createsubwindowwithoptions"></a>
## createSubWindowWithOptions

```TypeScript
createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise<window.Window>
```

创建该UIExtensionHostWindowProxy实例下的子窗口，使用Promise异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionHostWindowProxy-createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise<window.Window>--><!--Device-UIExtensionHostWindowProxy-createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise<window.Window>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 子窗口的名字。 |
| subWindowOptions | window.SubWindowOptions | 是 | 子窗口参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;window.Window&gt; | Promise used to return the subwindow created. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible causes:1. The window is not created or destroyed.2. Internal task error.3. The subWindow has been created and can not be created again.4. It is not allowed to create non-secure window when secure extension exists. |
| 1300035 | Creating a subwindow is not allowed in the current context. Possible cause:1. An AgentUIExtensionAbility cannot create a subwindow. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    const subWindowOpts: window.SubWindowOptions = {
      title: 'This is a subwindow',
      decorEnabled: true
    };
    // 创建子窗口
    extensionHostWindow.createSubWindowWithOptions('subWindowForHost', subWindowOpts)
      .then((subWindow: window.Window) => {
        subWindow.setUIContent('pages/Index', (err, data) =>{
          if (err && err.code != 0) {
            return;
          }
          subWindow?.resize(300, 300, (err, data)=>{
            if (err && err.code != 0) {
              return;
            }
            subWindow?.moveWindowTo(100, 100, (err, data)=>{
              if (err && err.code != 0) {
                return;
              }
              subWindow?.showWindow((err, data) => {
                if (err && err.code == 0) {
                  console.info(`The subwindow has been shown!`);
                } else {
                  console.error(`Failed to show the subwindow!`);
                }
              });
            });
          });
        });
      }).catch((error: BusinessError) => {
        console.error(`Create subwindow failed: ${JSON.stringify(error)}`);
      });
  }
}

```

<a id="createsubwindowwithoptions-1"></a>
## createSubWindowWithOptions

```TypeScript
createSubWindowWithOptions(name: string, subWindowConfig: window.SubWindowOptions,
        followCreatorLifecycle: boolean): Promise<window.Window>
```

创建该UIExtensionHostWindowProxy实例下的子窗口，可通过设置followCreatorLifecycle，决定子窗是否跟随组件（EmbeddedComponent或UIExtensionComponent）的生命周期，使用Promise异步回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionHostWindowProxy-createSubWindowWithOptions(name: string, subWindowConfig: window.SubWindowOptions,
        followCreatorLifecycle: boolean): Promise<window.Window>--><!--Device-UIExtensionHostWindowProxy-createSubWindowWithOptions(name: string, subWindowConfig: window.SubWindowOptions,
        followCreatorLifecycle: boolean): Promise<window.Window>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 子窗口的名字。 |
| subWindowConfig | window.SubWindowOptions | 是 | 子窗口参数。 |
| followCreatorLifecycle | boolean | 是 | 子窗生命周期是否跟组件（EmbeddedComponent或UIExtensionComponent）保持同步。true表示该组件隐藏时，子窗隐藏，该组件显示时子窗显示，false表示子窗的显隐不跟随该组件变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;window.Window&gt; | Promise used to return the subwindow. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible causes:1. The window is not created or destroyed.2. Internal task error.3. The subWindow has been created and can not be created again.4. It is not allowed to create non-secure window when secure extension exists. |
| 1300035 | Creating a subwindow is not allowed in the current context. Possible cause:1. An AgentUIExtensionAbility cannot create a subwindow. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    const subWindowConfig: window.SubWindowOptions = {
      title: 'This is a subwindow',
      decorEnabled: true
    };
    // 创建子窗口
    extensionHostWindow.createSubWindowWithOptions('subWindowForHost', subWindowConfig, true)
      .then((subWindow: window.Window) => {
        subWindow.setUIContent('pages/Index', (err, data) =>{
          if (err && err.code != 0) {
            return;
          }
          subWindow?.resize(300, 300, (err, data)=>{
            if (err && err.code != 0) {
              return;
            }
            subWindow?.moveWindowTo(100, 100, (err, data)=>{
              if (err && err.code != 0) {
                return;
              }
              subWindow?.showWindow((err, data) => {
                if (err && err.code == 0) {
                  console.info(`The subwindow has been shown!`);
                } else {
                  console.error(`Failed to show the subwindow!`);
                }
              });
            });
          });
        });
      }).catch((error: BusinessError) => {
        console.error(`Create subwindow failed: ${JSON.stringify(error)}`);
      });
  }
}

```

<a id="getwindowavoidarea"></a>
## getWindowAvoidArea

```TypeScript
getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea
```

获取宿主应用窗口内容规避的区域；如系统栏区域、刘海屏区域、手势区域、软键盘区域等与宿主窗口内容重叠时，需要宿主窗口内容避让的区域。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionHostWindowProxy-getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea--><!--Device-UIExtensionHostWindowProxy-getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | window.AvoidAreaType | 是 | 表示避让区类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| window.AvoidArea | Avoidance area for the content of the host window. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. |

**示例：**

```TypeScript
// ExtensionProvider.ets

import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 获取宿主应用窗口的避让信息
    const avoidArea = extensionHostWindow.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
    console.info(`avoidArea: ${JSON.stringify(avoidArea)}`);
  }
}

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

**起始版本：** 11

**需要权限：** 
- API版本12+：ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionHostWindowProxy-hideNonSecureWindows(shouldHide: boolean): Promise<void>--><!--Device-UIExtensionHostWindowProxy-hideNonSecureWindows(shouldHide: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shouldHide | boolean | 是 | 指示是否隐藏不安全窗口，true表示隐藏，false表示不隐藏。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。、 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes:1. Permission denied. Interface caller does not have permission "ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS".2. The UIExtension window proxy is abnormal.<br>**适用版本：** 12+ |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally.<br>**适用版本：** 12+ |

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

<a id="hideprivacycontentforhost"></a>
## hidePrivacyContentForHost

```TypeScript
hidePrivacyContentForHost(shouldHide: boolean): Promise<void>
```

设置UIExtension组件在非系统截图时的隐私内容保护开关，使用Promise异步回调。

> **说明：**  
>  
> 开启截图隐私内容保护后，使用窗口截图[window.snapshot](docroot://reference/apis-arkui/arkts-apis-window-Window.md#snapshot9)或者组件截图  
> [UIContext.getComponentSnapshot](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)  
> 将无法截取到当前组件的内容（不包括该组件下创建的子窗）。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionHostWindowProxy-hidePrivacyContentForHost(shouldHide: boolean): Promise<void>--><!--Device-UIExtensionHostWindowProxy-hidePrivacyContentForHost(shouldHide: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shouldHide | boolean | 是 | 是否开启截图隐私保护。true表示开启，false表示不开启。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes:1. The UIExtension window proxy is abnormal.2. Not the UIExtensionAbility process calling. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 开启截图隐私内容保护
    extensionHostWindow.hidePrivacyContentForHost(true).then(() => {
      console.info(`Succeeded in enabling privacy protection for non-system screenshots.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to enable privacy protection for non-system screenshots. Cause:${JSON.stringify(err)}`);
    });
  }
}

```

<a id="off"></a>
## off('avoidAreaChange')

```TypeScript
off(type: 'avoidAreaChange', callback?: Callback<{ type: window.AvoidAreaType, area: window.AvoidArea }>): void
```

注销系统避让区变化的监听。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionHostWindowProxy-off(type: 'avoidAreaChange', callback?: Callback<{ type: window.AvoidAreaType, area: window.AvoidArea }>): void--><!--Device-UIExtensionHostWindowProxy-off(type: 'avoidAreaChange', callback?: Callback<{ type: window.AvoidAreaType, area: window.AvoidArea }>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'avoidAreaChange' | 是 | 注销的事件类型，固定为'avoidAreaChange'，即系统避让区变化事件。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;{ type: window.AvoidAreaType, area: window.AvoidArea }&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes:1. The listening type is not supported.2. The listening type is not registered.3. The listener has not been registered.4. The UIExtension window proxy is abnormal. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession} from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 注销所有避让区变化的监听
    extensionHostWindow.off('avoidAreaChange');
  }
}

```

<a id="off-1"></a>
## off('windowSizeChange')

```TypeScript
off(type: 'windowSizeChange', callback?: Callback<window.Size>): void
```

注销组件（EmbeddedComponent或UIExtensionComponent）尺寸变化的监听。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionHostWindowProxy-off(type: 'windowSizeChange', callback?: Callback<window.Size>): void--><!--Device-UIExtensionHostWindowProxy-off(type: 'windowSizeChange', callback?: Callback<window.Size>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowSizeChange' | 是 | 注销的事件类型，固定值：'windowSizeChange'，即组件（EmbeddedComponent或UIExtensionComponent）尺寸变化事件。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;window.Size&gt; | 否 | 回调函数。返回当前的组件（EmbeddedComponent或UIExtensionComponent）尺寸。如果传入该参数，则关闭该监听。如果未传入参数，则关闭组件（EmbeddedComponent或UIExtensionComponent）尺寸变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes:1. The listening type is not supported.2. The listening type is not registered.3. The listener has not been registered.4. The UIExtension window proxy is abnormal. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 注销组件（EmbeddedComponent或UIExtensionComponent）大小变化的监听
    extensionHostWindow.off('windowSizeChange');
  }
}

```

<a id="on"></a>
## on('avoidAreaChange')

```TypeScript
on(type: 'avoidAreaChange', callback: Callback<{ type: window.AvoidAreaType, area: window.AvoidArea }>): void
```

注册系统避让区变化的监听。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionHostWindowProxy-on(type: 'avoidAreaChange', callback: Callback<{ type: window.AvoidAreaType, area: window.AvoidArea }>): void--><!--Device-UIExtensionHostWindowProxy-on(type: 'avoidAreaChange', callback: Callback<{ type: window.AvoidAreaType, area: window.AvoidArea }>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'avoidAreaChange' | 是 | 监听的事件类型，固定为'avoidAreaChange'，即系统避让区变化事件。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;{ type: window.AvoidAreaType, area: window.AvoidArea }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes:1. The listening type is not supported.2. The listener has been registered.3. The UIExtension window proxy is abnormal. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 注册避让区变化的监听
    extensionHostWindow.on('avoidAreaChange', (info) => {
      console.info(`The avoid area of the host window is: ${JSON.stringify(info.area)}.`);
    });
  }
}

```

<a id="on-1"></a>
## on('windowSizeChange')

```TypeScript
on(type: 'windowSizeChange', callback: Callback<window.Size>): void
```

注册组件（EmbeddedComponent或UIExtensionComponent）尺寸变化的监听。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionHostWindowProxy-on(type: 'windowSizeChange', callback: Callback<window.Size>): void--><!--Device-UIExtensionHostWindowProxy-on(type: 'windowSizeChange', callback: Callback<window.Size>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowSizeChange' | 是 | 监听的事件类型，固定为'windowSizeChange'，即组件（EmbeddedComponent或UIExtensionComponent）尺寸变化事件。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;window.Size&gt; | 是 | 回调函数：入参用于接收当前组件（EmbeddedComponent或UIExtensionComponent）的尺寸。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes:1. The listening type is not supported.2. The listener has been registered.3. The UIExtension window proxy is abnormal. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 注册组件（EmbeddedComponent或UIExtensionComponent）大小变化的监听
    extensionHostWindow.on('windowSizeChange', (size) => {
      console.info(`The size of the component is: ${JSON.stringify(size)}.`);
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

<!--Device-UIExtensionHostWindowProxy-setWaterMarkFlag(enable: boolean): Promise<void>--><!--Device-UIExtensionHostWindowProxy-setWaterMarkFlag(enable: boolean): Promise<void>-End-->

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

## properties

```TypeScript
properties: UIExtensionHostWindowProxyProperties
```

UIExtensionComponent组件以及宿主窗口的信息。

**约束：** 由于架构约束，不建议在[onSessionCreate](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#onsessioncreate-1)阶段同步获取该值，建议在收到[on('windowSizeChange')](@ohos.uiExtensionHost:uiExtensionHost.UIExtensionHostWindowProxy.on(type: 'windowSizeChange', callback: Callback<window.Size>))回调之后获取。

**类型：** UIExtensionHostWindowProxyProperties

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionHostWindowProxy-properties: UIExtensionHostWindowProxyProperties--><!--Device-UIExtensionHostWindowProxy-properties: UIExtensionHostWindowProxyProperties-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

