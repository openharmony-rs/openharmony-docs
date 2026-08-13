# WindowProxy

UIExtension窗口代理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-uiExtension-interface WindowProxy--><!--Device-uiExtension-interface WindowProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## createSubWindowWithOptions

```TypeScript
createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise<window.Window>
```

创建该WindowProxy实例下的子窗口，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WindowProxy-createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise<window.Window>--><!--Device-WindowProxy-createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise<window.Window>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

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
| 1300035 | Creating a subwindow is not allowed in the current context. Possible cause: 1. An AgentUIExtensionAbility cannot create a subwindow. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible causes: 1. The window is not created or destroyed. 2. Internal task error. 3. The subWindow has been created and cannot be created again. 4. It is not allowed to create non-secure window when secure extension exists. |

## 示例

ArkTS-Dyn示例：

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    const subWindowOpts: window.SubWindowOptions = {
      title: 'This is a subwindow',
      decorEnabled: true
    };
    // 创建子窗口
    extensionWindow.createSubWindowWithOptions('subWindowForHost', subWindowOpts)
      .then((subWindow: window.Window) => {
        subWindow.setUIContent('pages/Index', (err, data) => {
          if (err && err.code) {
            return;
          }
          subWindow?.resize(300, 300, (err, data) => {
            if (err && err.code) {
              return;
            }
            subWindow?.moveWindowTo(100, 100, (err, data) => {
              if (err && err.code) {
                return;
              }
              subWindow?.showWindow((err, data) => {
                if (err && err.code) {
                  console.error(`Failed to show the subwindow. Code: ${err.code}, message: ${err.message}`);
                } else {
                  console.info(`The subwindow has been shown!`);
                }
              });
            });
          });
        });
      }).catch((error: BusinessError) => {
      console.error(`Create subwindow failed. Cause code: ${error.code}, message: ${error.message}`);
    });
  }
}
```

ArkTS-Sta示例：

```TypeScript
// ExtensionProvider.ets
import { UIExtensionContentSession, Want } from '@kit.AbilityKit';
import EmbeddedUIExtensionAbility from '@ohos.app.ability.EmbeddedUIExtensionAbility';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    const subWindowOpts: window.SubWindowOptions = {
      title: 'This is a subwindow',
      decorEnabled: true
    };
    // 创建子窗口
    extensionWindow.createSubWindowWithOptions('subWindowForHost', subWindowOpts)
      .then((subWindow: window.Window) => {
        subWindow.setUIContent('pages/Index', (err, data) => {
          if (err && err.code != 0) {
            return;
          }
          subWindow?.resize(300, 300, (err, data) => {
            if (err && err.code != 0) {
              return;
            }
            subWindow?.moveWindowTo(100, 100, (err, data) => {
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
      }).catch((err) => {
      let error = err as BusinessError;
      console.error(`Create subwindow failed. Cause code: ${error.code}, message: ${error.message}`);
    });
  }
}
```

## createSubWindowWithOptions

```TypeScript
createSubWindowWithOptions(name: string, subWindowConfig: window.SubWindowOptions,
        followCreatorLifecycle: boolean): Promise<window.Window>
```

创建该WindowProxy实例下的子窗口，可通过设置followCreatorLifecycle，决定子窗是否跟随组件（EmbeddedComponent或UIExtensionComponent）的生命周期，使用 Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowProxy-createSubWindowWithOptions(name: string, subWindowConfig: window.SubWindowOptions,        followCreatorLifecycle: boolean): Promise<window.Window>--><!--Device-WindowProxy-createSubWindowWithOptions(name: string, subWindowConfig: window.SubWindowOptions,        followCreatorLifecycle: boolean): Promise<window.Window>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 子窗口的名字。 |
| subWindowConfig | window.SubWindowOptions | 是 | 子窗口参数。 |
| followCreatorLifecycle | boolean | 是 | 子窗生命周期是否跟组件（EmbeddedComponent或UIExtensionComponent）保持同步。true表示该组件隐藏时， 子窗隐藏，该组件显示时子窗显示，false表示子窗的显隐不跟随该组件变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;window.Window&gt; | Promise used to return the subwindow. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 1300035 | Creating a subwindow is not allowed in the current context. Possible cause: 1. An AgentUIExtensionAbility cannot create a subwindow. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. 3. The subWindow has been created and cannot be created again. 4. It is not allowed to create non-secure window when secure extension exists. |

## 示例

ArkTS-Dyn示例：

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    const subWindowConfig: window.SubWindowOptions = {
      title: 'This is a subwindow',
      decorEnabled: true
    };
    // 创建子窗口
    extensionWindow.createSubWindowWithOptions('subWindowForHost', subWindowConfig, true)
      .then((subWindow: window.Window) => {
        subWindow.setUIContent('pages/Index', (err, data) => {
          if (err && err.code) {
            return;
          }
          subWindow?.resize(300, 300, (err, data) => {
            if (err && err.code) {
              return;
            }
            subWindow?.moveWindowTo(100, 100, (err, data) => {
              if (err && err.code) {
                return;
              }
              subWindow?.showWindow((err, data) => {
                if (err && err.code) {
                  console.error(`Failed to show the subwindow. Code: ${err.code}, message: ${err.message}`);
                } else {
                  console.info(`The subwindow has been shown!`);
                }
              });
            });
          });
        });
      }).catch((error: BusinessError) => {
      console.error(`Create subwindow failed. Cause code: ${error.code}, message: ${error.message}`);
    });
  }
}
```

ArkTS-Sta示例：

```TypeScript
// ExtensionProvider.ets
import { UIExtensionContentSession, Want } from '@kit.AbilityKit';
import EmbeddedUIExtensionAbility from '@ohos.app.ability.EmbeddedUIExtensionAbility';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    const subWindowConfig: window.SubWindowOptions = {
      title: 'This is a subwindow',
      decorEnabled: true
    };
    // 创建子窗口
    extensionWindow.createSubWindowWithOptions('subWindowForHost', subWindowConfig, true)
      .then((subWindow: window.Window) => {
        subWindow.setUIContent('pages/Index', (err, data) => {
          if (err && err.code != 0) {
            return;
          }
          subWindow?.resize(300, 300, (err, data) => {
            if (err && err.code != 0) {
              return;
            }
            subWindow?.moveWindowTo(100, 100, (err, data) => {
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
      }).catch((err) => {
      let error = err as BusinessError;
      console.error(`Create subwindow failed. Cause code: ${error.code}, message: ${error.message}`);
    });
  }
}
```

## getWindowAvoidArea

```TypeScript
getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea
```

获取宿主应用窗口内容规避的区域；如系统栏区域、刘海屏区域、手势区域、软键盘区域等与宿主窗口内容重叠时，需要宿主窗口内容避让的区域。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WindowProxy-getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea--><!--Device-WindowProxy-getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 获取宿主应用窗口的避让信息
    let avoidArea: window.AvoidArea | undefined = extensionWindow?.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
    console.info(`avoidArea: ${JSON.stringify(avoidArea)}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
// ExtensionProvider.ets
import { UIExtensionContentSession, Want } from '@kit.AbilityKit';
import EmbeddedUIExtensionAbility from '@ohos.app.ability.EmbeddedUIExtensionAbility';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 获取宿主应用窗口的避让信息
    let avoidArea: window.AvoidArea | undefined = extensionWindow?.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
    console.info(`avoidArea: ${JSON.stringify(avoidArea)}`);
  }
}
```

## occupyEvents

```TypeScript
occupyEvents(eventFlags: int): Promise<void>
```

设置组件（EmbeddedComponent或UIExtensionComponent）占用事件，宿主将不响应组件区域内被占用的事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WindowProxy-occupyEvents(eventFlags: int): Promise<void>--><!--Device-WindowProxy-occupyEvents(eventFlags: int): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventFlags | int | 是 | 占用的事件类型，具体取值可见[EventFlag](arkts-arkui-uiextension-eventflag-e.md#EventFlag)枚举值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. 2. Internal task error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { uiExtension } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 占用事件
    setTimeout(() => {
      try {
        extensionWindow.occupyEvents(uiExtension.EventFlag.EVENT_CLICK | uiExtension.EventFlag.EVENT_LONG_PRESS).then(() => {
          console.info(`Succeeded in occupying events`);
        }).catch((err: BusinessError) => {
          console.error(`Failed to occupy events. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (e) {
        console.error(`Occupy events got exception code: ${e.code}, message: ${e.message}`);
      }
    }, 500);
  }
}
```

ArkTS-Sta示例：

```TypeScript
// ExtensionProvider.ets
import { UIExtensionContentSession, Want } from '@kit.AbilityKit';
import EmbeddedUIExtensionAbility from '@ohos.app.ability.EmbeddedUIExtensionAbility';
import uiExtension from '@ohos.arkui.uiExtension';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 占用事件
    setTimeout(() => {
      try {
        extensionWindow.occupyEvents(uiExtension.EventFlag.EVENT_CLICK | uiExtension.EventFlag.EVENT_LONG_PRESS).then(() => {
          console.info(`Succeeded in occupying events`);
        }).catch((err) => {
          let error = err as BusinessError;
          console.error(`Failed to occupy events. Cause code: ${error.code}, message: ${error.message}`);
        });
      } catch (e) {
        console.error('Occupy events got exception:' + JSON.stringify(e));
      }
    }, 500);
  }
}
```

## offAvoidAreaChange

```TypeScript
offAvoidAreaChange(callback?: Callback<AvoidAreaInfo>): void
```

Unsubscribes from the event indicating changes to the area where the window cannot be displayed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowProxy-offAvoidAreaChange(callback?: Callback<AvoidAreaInfo>): void--><!--Device-WindowProxy-offAvoidAreaChange(callback?: Callback<AvoidAreaInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AvoidAreaInfo](arkts-arkui-uiextension-avoidareainfo-i.md)&gt; | 否 | Unregister the callback function. If not provided, all callbacks for the given event type will be removed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listening type is not registered. 3. The listener has not been registered. 4. The UIExtension window proxy is abnormal. |

## 示例

```TypeScript
// ArkTS-Sta示例
// ExtensionProvider.ets
import { UIExtensionContentSession } from '@kit.AbilityKit';
import EmbeddedUIExtensionAbility from '@ohos.app.ability.EmbeddedUIExtensionAbility';
import uiExtension from '@ohos.arkui.uiExtension';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    extensionWindow.onAvoidAreaChange((info: uiExtension.AvoidAreaInfo) => {
      console.info(`The avoid area of the host window is: ${JSON.stringify(info.area)}.`);
    });
    // 注销所有避让区变化的监听
    extensionWindow.offAvoidAreaChange();
  }
}
```

## offRectChange

```TypeScript
offRectChange(callback?: Callback<RectChangeOptions>): void
```

Unsubscribes from changes in the position and size of the component (EmbeddedComponent or UIExtensionComponent). This API can be used only on 2-in-1 devices.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowProxy-offRectChange(callback?: Callback<RectChangeOptions>): void--><!--Device-WindowProxy-offRectChange(callback?: Callback<RectChangeOptions>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;RectChangeOptions&gt; | 否 | Unregister the callback function. If not provided, all callbacks for the given event type will be removed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listening type is not registered. 3. The listener has not been registered. 4. The UIExtension window proxy is abnormal. |

## 示例

```TypeScript
// ArkTS-Sta示例
// ExtensionProvider.ets
import { UIExtensionContentSession } from '@kit.AbilityKit';
import EmbeddedUIExtensionAbility from '@ohos.app.ability.EmbeddedUIExtensionAbility';
import uiExtension from '@ohos.arkui.uiExtension';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    extensionWindow.onRectChange(uiExtension.RectChangeReason.HOST_WINDOW_RECT_CHANGE, (data: uiExtension.RectChangeOptions) => {
        console.info('Succeeded window rect changes. Data: ' + JSON.stringify(data));
    });
    // 注销组件（EmbeddedComponent或UIExtensionComponent）位置及尺寸变化的监听
    extensionWindow.offRectChange();
  }
}
```

## offWindowSizeChange

```TypeScript
offWindowSizeChange(callback?: Callback<window.Size>): void
```

Unsubscribes from the component (EmbeddedComponent or UIExtensionComponent) size change event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowProxy-offWindowSizeChange(callback?: Callback<window.Size>): void--><!--Device-WindowProxy-offWindowSizeChange(callback?: Callback<window.Size>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;window.Size&gt; | 否 | Unregister the callback function. If not provided, all callbacks for the given event type will be removed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listening type is not registered. 3. The listener has not been registered. 4. The UIExtension window proxy is abnormal. |

## 示例

```TypeScript
// ArkTS-Sta示例
// ExtensionProvider.ets
import { UIExtensionContentSession } from '@kit.AbilityKit';
import EmbeddedUIExtensionAbility from '@ohos.app.ability.EmbeddedUIExtensionAbility';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    extensionWindow.onWindowSizeChange((size: window.Size) => {
      console.info(`The size of the component is: ${JSON.stringify(size)}.`);
    });
    // 注销组件（EmbeddedComponent或UIExtensionComponent）大小变化的监听
    extensionWindow.offWindowSizeChange();
  }
}
```

## off_avoidAreaChange

```TypeScript
off(type: 'avoidAreaChange', callback?: Callback<AvoidAreaInfo>): void
```

注销系统避让区变化的监听。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WindowProxy-off(type: 'avoidAreaChange', callback?: Callback<AvoidAreaInfo>): void--><!--Device-WindowProxy-off(type: 'avoidAreaChange', callback?: Callback<AvoidAreaInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'avoidAreaChange' | 是 | 注销的事件类型，固定为'avoidAreaChange'，即系统避让区变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AvoidAreaInfo](arkts-arkui-uiextension-avoidareainfo-i.md)&gt; | 否 | 回调函数：如果传入该参数，则关闭该监听。如果未传入参数，则关闭所有系统避让区变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listening type is not registered. 3. The listener has not been registered. 4. The UIExtension window proxy is abnormal. |

## 示例

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 注销所有避让区变化的监听
    extensionWindow.off('avoidAreaChange');
  }
}
```

## off_rectChange

```TypeScript
off(type: 'rectChange', callback?: Callback<RectChangeOptions>): void
```

注销组件（EmbeddedComponent或UIExtensionComponent）位置及尺寸变化的监听。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WindowProxy-off(type: 'rectChange', callback?: Callback<RectChangeOptions>): void--><!--Device-WindowProxy-off(type: 'rectChange', callback?: Callback<RectChangeOptions>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'rectChange' | 是 | 监听事件，固定为'rectChange'，即组件（EmbeddedComponent或UIExtensionComponent）矩形变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;RectChangeOptions&gt; | 否 | 回调函数。返回当前组件（EmbeddedComponent或UIExtensionComponent）矩形变化值及变化原因。如 果传入参数，则关闭该监听。如果未传入参数，则关闭所有组件（EmbeddedComponent或UIExtensionComponent）矩形变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listening type is not registered. 3. The listener has not been registered. 4. The UIExtension window proxy is abnormal. |

## 示例

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 注销组件（EmbeddedComponent或UIExtensionComponent）位置及尺寸变化的监听
    extensionWindow.off('rectChange');
  }
}
```

## off_windowSizeChange

```TypeScript
off(type: 'windowSizeChange', callback?: Callback<window.Size>): void
```

注销组件（EmbeddedComponent或UIExtensionComponent）尺寸变化的监听。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WindowProxy-off(type: 'windowSizeChange', callback?: Callback<window.Size>): void--><!--Device-WindowProxy-off(type: 'windowSizeChange', callback?: Callback<window.Size>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowSizeChange' | 是 | 注销的事件类型，固定值：'windowSizeChange'，即组件（EmbeddedComponent或UIExtensionComponent）尺寸 变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;window.Size&gt; | 否 | 回调函数。返回当前的组件（EmbeddedComponent或UIExtensionComponent）尺寸。如果传入该参数，则关闭该 监听。如果未传入参数，则关闭组件（EmbeddedComponent或UIExtensionComponent）尺寸变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listening type is not registered. 3. The listener has not been registered. 4. The UIExtension window proxy is abnormal. |

## 示例

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 注销组件（EmbeddedComponent或UIExtensionComponent）大小变化的监听
    extensionWindow.off('windowSizeChange');
  }
}
```

## onAvoidAreaChange

```TypeScript
onAvoidAreaChange(callback: Callback<AvoidAreaInfo>): void
```

Subscribes to the event indicating changes to the area where the window cannot be displayed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowProxy-onAvoidAreaChange(callback: Callback<AvoidAreaInfo>): void--><!--Device-WindowProxy-onAvoidAreaChange(callback: Callback<AvoidAreaInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AvoidAreaInfo](arkts-arkui-uiextension-avoidareainfo-i.md)&gt; | 是 | Callback used to return the avoid area information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listener has been registered. 3. The UIExtension window proxy is abnormal. |

## 示例

```TypeScript
// ArkTS-Sta示例
// ExtensionProvider.ets
import { UIExtensionContentSession, Want } from '@kit.AbilityKit';
import EmbeddedUIExtensionAbility from '@ohos.app.ability.EmbeddedUIExtensionAbility';
import uiExtension from '@ohos.arkui.uiExtension';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 注册避让区变化的监听
    extensionWindow.onAvoidAreaChange((info: uiExtension.AvoidAreaInfo) => {
      console.info(`The avoid area of the host window is: ${JSON.stringify(info.area)}.`);
    });
  }
}
```

## onRectChange

```TypeScript
onRectChange(reasons: int, callback: Callback<RectChangeOptions>): void
```

Subscribes to changes in the position and size of the component (EmbeddedComponent or UIExtensionComponent). This API can be used only on 2-in-1 devices.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowProxy-onRectChange(reasons: int, callback: Callback<RectChangeOptions>): void--><!--Device-WindowProxy-onRectChange(reasons: int, callback: Callback<RectChangeOptions>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reasons | int | 是 | The reasons of component rect change. &lt;br&gt;取值范围为全体整数。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;RectChangeOptions&gt; | 是 | Callback used to return the RectChangeOptions. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes: &lt;br&gt; 1. The listening type is not supported. &lt;br&gt; 2. The listener has been registered. &lt;br&gt; 3. The UIExtension window proxy is abnormal. |

## 示例

```TypeScript
// ArkTS-Sta示例
// ExtensionProvider.ets
import { UIExtensionContentSession, Want } from '@kit.AbilityKit';
import EmbeddedUIExtensionAbility from '@ohos.app.ability.EmbeddedUIExtensionAbility';
import uiExtension from '@ohos.arkui.uiExtension';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 注册组件（EmbeddedComponent或UIExtensionComponent）位置及尺寸变化的监听
    extensionWindow.onRectChange(uiExtension.RectChangeReason.HOST_WINDOW_RECT_CHANGE, (data: uiExtension.RectChangeOptions) => {
        console.info('Succeeded window rect changes. Data: ' + JSON.stringify(data));
    });
  }
}
```

## onWindowSizeChange

```TypeScript
onWindowSizeChange(callback: Callback<window.Size>): void
```

Subscribes to the component (EmbeddedComponent or UIExtensionComponent) size change event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowProxy-onWindowSizeChange(callback: Callback<window.Size>): void--><!--Device-WindowProxy-onWindowSizeChange(callback: Callback<window.Size>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;window.Size&gt; | 是 | Callback used to return the window size. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listener has been registered. 3. The UIExtension window proxy is abnormal. |

## 示例

```TypeScript
// ArkTS-Sta示例
// ExtensionProvider.ets
import { UIExtensionContentSession, Want } from '@kit.AbilityKit';
import EmbeddedUIExtensionAbility from '@ohos.app.ability.EmbeddedUIExtensionAbility';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 注册组件（EmbeddedComponent或UIExtensionComponent）大小变化的监听
    extensionWindow.onWindowSizeChange((size: window.Size) => {
      console.info(`The size of the component is: ${JSON.stringify(size)}.`);
    });
  }
}
```

## on_avoidAreaChange

```TypeScript
on(type: 'avoidAreaChange', callback: Callback<AvoidAreaInfo>): void
```

注册系统避让区变化的监听。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WindowProxy-on(type: 'avoidAreaChange', callback: Callback<AvoidAreaInfo>): void--><!--Device-WindowProxy-on(type: 'avoidAreaChange', callback: Callback<AvoidAreaInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'avoidAreaChange' | 是 | 监听的事件类型，固定为'avoidAreaChange'，即系统避让区变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AvoidAreaInfo](arkts-arkui-uiextension-avoidareainfo-i.md)&gt; | 是 | 回调函数：入参用于接收当前避让区的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listener has been registered. 3. The UIExtension window proxy is abnormal. |

## 示例

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { uiExtension } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 注册避让区变化的监听
    extensionWindow.on('avoidAreaChange', (info: uiExtension.AvoidAreaInfo) => {
      console.info(`The avoid area of the host window is: ${JSON.stringify(info.area)}.`);
    });
  }
}
```

## on_rectChange

```TypeScript
on(type: 'rectChange', reasons: number, callback: Callback<RectChangeOptions>): void
```

注册组件（EmbeddedComponent或UIExtensionComponent）位置及尺寸变化的监听。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WindowProxy-on(type: 'rectChange', reasons: number, callback: Callback<RectChangeOptions>): void--><!--Device-WindowProxy-on(type: 'rectChange', reasons: number, callback: Callback<RectChangeOptions>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'rectChange' | 是 | 监听事件，固定为'rectChange'，即组件（EmbeddedComponent或UIExtensionComponent）矩形变化事件。 |
| reasons | number | 是 | 触发组件（EmbeddedComponent或UIExtensionComponent）位置及尺寸变化的原因，具体取值可参考 [RectChangeReason](arkts-arkui-uiextension-rectchangereason-e.md#RectChangeReason)枚举值。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;RectChangeOptions&gt; | 是 | 回调函数。返回当前组件（EmbeddedComponent或UIExtensionComponent）矩形变化值及变化原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listener has been registered. 3. The UIExtension window proxy is abnormal. |

## 示例

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { uiExtension } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 注册组件（EmbeddedComponent或UIExtensionComponent）位置及尺寸变化的监听
    extensionWindow.on('rectChange', uiExtension.RectChangeReason.HOST_WINDOW_RECT_CHANGE, (data: uiExtension.RectChangeOptions) => {
        console.info('Succeeded window rect changes. Data: ' + JSON.stringify(data));
    });
  }
}
```

## on_windowSizeChange

```TypeScript
on(type: 'windowSizeChange', callback: Callback<window.Size>): void
```

注册组件（EmbeddedComponent或UIExtensionComponent）尺寸变化的监听。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WindowProxy-on(type: 'windowSizeChange', callback: Callback<window.Size>): void--><!--Device-WindowProxy-on(type: 'windowSizeChange', callback: Callback<window.Size>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowSizeChange' | 是 | 监听的事件类型，固定为'windowSizeChange'，即组件（EmbeddedComponent或UIExtensionComponent）尺寸变 化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;window.Size&gt; | 是 | 回调函数：入参用于接收当前组件（EmbeddedComponent或UIExtensionComponent）的尺寸。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | Abnormal state. Possible causes: 1. The listening type is not supported. 2. The listener has been registered. 3. The UIExtension window proxy is abnormal. |

## 示例

```TypeScript
// ExtensionProvider.ets
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends EmbeddedUIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionWindow = session.getUIExtensionWindowProxy();
    // 注册组件（EmbeddedComponent或UIExtensionComponent）大小变化的监听
    extensionWindow.on('windowSizeChange', (size: window.Size) => {
      console.info(`The size of the component is: ${JSON.stringify(size)}.`);
    });
  }
}
```

## properties

```TypeScript
properties: WindowProxyProperties
```

组件（EmbeddedComponent或UIExtensionComponent）的信息。 **约束：** 由于架构约束，不建议在 [onSessionCreate](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#onSessionCreate)阶段同步获取该值，建议在收到 [on('windowSizeChange')](#on_avoidAreaChange) 回调之后获取。

**类型：** [WindowProxyProperties](arkts-arkui-uiextension-windowproxyproperties-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WindowProxy-properties: WindowProxyProperties--><!--Device-WindowProxy-properties: WindowProxyProperties-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

