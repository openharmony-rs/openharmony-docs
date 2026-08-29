# InputMethodAbility

InputMethodAbility是输入法应用的核心能力对象，提供输入法生命周期管理、面板创建与销毁、事件订阅等功能。输入法应用通过 [getInputMethodAbility](arkts-ime-inputmethodengine-getinputmethodability-f.md)获取该实例。 核心功能概述：   
- 生命周期事件订阅：通过on('inputStart')订阅输入法绑定事件获取[KeyboardController](arkts-ime-inputmethodengine-keyboardcontroller-i.md)和 [InputClient](arkts-ime-inputmethodengine-inputclient-i.md)实例，通过on('inputStop')订阅输入法解绑事件，通过on('keyboardShow'|'keyboardHide') 订阅软键盘显示/隐藏事件。   
- 面板管理：通过 [createPanel](#createpanel) 创建输入法面板，通过 [destroyPanel](#destroypanel) 销毁面板。createPanel与destroyPanel需配对调用，防止资源泄漏。   
- 子类型与安全模式：通过on('setSubtype')订阅输入法子类型变化事件，通过on('securityModeChange')订阅安全模式变化事件，通过 [getSecurityMode](#getsecuritymode)获取当前安全模式。   
- 私有通信：通过on('privateCommand')订阅应用私有数据事件，用于输入法应用与绑定应用之间的私有数据交互。   
- 屏幕与窗口信息：通过on('setCallingWindow')订阅调用方窗口变化事件，通过on('callingDisplayDidChange')订阅屏幕ID变化事件，通过on('discardTypingText')订阅 丢弃文本事件。   
 典型调用顺序： 
1. 输入法应用在[InputMethodExtensionAbility](arkts-ime-inputmethodextensionability-c.md)的onCreate生命周期中调用getInputMethodAbility()获取实例。 
2. 订阅on('inputStart')事件，在回调中获取KeyboardController和InputClient实例。 
3. 在on('inputStart')回调中调用createPanel()创建面板，并调用panel.setUiContent()加载键盘页面。 
4. 订阅on('keyboardShow'|'keyboardHide')事件，在回调中调用panel.show()/panel.hide()显示/隐藏面板。 
5. 在InputMethodExtensionAbility的onDestroy生命周期中调用destroyPanel()销毁面板，取消所有事件订阅。
下列API均需使用[getInputMethodAbility](arkts-ime-inputmethodengine-getinputmethodability-f.md)获取到InputMethodAbility实例后，通过实例调用。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## createPanel

```TypeScript
createPanel(ctx: BaseContext, info: PanelInfo, callback: AsyncCallback<Panel>): void
```

创建输入法面板，仅支持输入法应用在 [InputMethodExtensionAbility](arkts-ime-inputmethodextensionability-c.md)（输入法扩展能力）类中调用。使 用callback异步回调。 配对调用：   
- 调用createPanel()创建面板后，必须在使用完毕后调用 [destroyPanel](#destroypanel) 销毁面板以释放资源。   
- 未调用destroyPanel()会导致面板资源泄漏，影响系统资源使用。   
- 单个输入法应用仅允许创建一个软键盘类型和一个状态栏类型的面板。   
   
> **说明：**
   
> 
   
> 单个输入法应用仅允许创建一个[软键盘类型](arkts-ime-inputmethodengine-paneltype-e.md)和一个[状态栏类型](arkts-ime-inputmethodengine-paneltype-e.md)的面板。
   
> 
   
> 输入法面板不支持创建子窗口。例如：不支持使用window.createWindow[设置应用子窗口](../../../windowmanager/application-window-fa.md#设置应用子窗口)、
   
> [bindContextMenu](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md#bindcontextmenu)
   
> 、CustomDialog等接口创建子窗口弹窗。建议开发者采用非子窗的替代方案，如
   
> 弹出框、
   
> [bindMenu](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md#bindmenu)或设置
   
> showInSubwindow为false。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | 是 | 当前输入法应用上下文信息。 |
| info | PanelInfo | 是 | 输入法面板信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Panel&gt; | 是 | 回调函数。当输入法面板创建成功，err为undefined，data为获取到的Panel对象;否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800004](../errorcode-inputmethod-framework.md#12800004-不是输入法应用) | not an input method application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine, InputMethodExtensionAbility } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';

// 创建面板信息，设置面板类型为软键盘，状态为固定态
let panelInfo: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}

class InputMethodExt extends InputMethodExtensionAbility {
    onCreate(want: Want): void {
        console.info(`onCreate, want: ${want.abilityName}`);
        // context为InputMethodExtensionAbility类提供的上下文对象，无需额外获取
        if (this.context) {
            // 创建输入法面板
            inputMethodEngine.getInputMethodAbility()
            .createPanel(this.context, panelInfo, (err: BusinessError, panel: inputMethodEngine.Panel) => {
                if (err) {
                console.error(`Failed to createPanel. Code is ${err.code}, message is ${err.message}`);
                return;
              }
                console.info('Succeed in creating panel.');
            })
        }
    }
}
```

## createPanel

```TypeScript
createPanel(ctx: BaseContext, info: PanelInfo): Promise<Panel>
```

创建输入法面板，仅支持输入法应用在 [InputMethodExtensionAbility](arkts-ime-inputmethodextensionability-c.md)类中调用。使用promise异 步回调。   
> **说明：**
   
> 
   
> 单个输入法应用仅允许创建一个[软键盘类型](arkts-ime-inputmethodengine-paneltype-e.md)和一个[状态栏类型](arkts-ime-inputmethodengine-paneltype-e.md)的面板。
   
> 
   
> 输入法面板不支持创建子窗口。例如：不支持使用window.createWindow[设置应用子窗口](../../../windowmanager/application-window-fa.md#设置应用子窗口)、
   
> [bindContextMenu](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md#bindcontextmenu)
   
> 、CustomDialog等接口创建子窗口弹窗。建议开发者采用非子窗的替代方案，如
   
> 弹出框、
   
> [bindMenu](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md#bindmenu)或设置
   
> showInSubwindow为false。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | 是 | 当前输入法应用上下文信息。 |
| info | PanelInfo | 是 | 输入法面板信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Panel&gt; | Promise对象，返回Panel对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800004](../errorcode-inputmethod-framework.md#12800004-不是输入法应用) | not an input method application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine, InputMethodExtensionAbility } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';

// 创建面板信息，设置面板类型为软键盘，状态为固定态
let panelInfo: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}

class InputMethodExt extends InputMethodExtensionAbility {
    onCreate(want: Want): void {
        console.info(`onCreate, want: ${want.abilityName}`);
        if (this.context) {
            inputMethodEngine.getInputMethodAbility().createPanel(this.context, panelInfo)
                .then((panel: inputMethodEngine.Panel) => {
                console.info('Succeed in creating panel.');
            }).catch((err: BusinessError) => {
                console.error(`Failed to create panel. Code is ${err.code}, message is ${err.message}`);
            })
        }
    }
}
```

## destroyPanel

```TypeScript
destroyPanel(panel: Panel, callback: AsyncCallback<void>): void
```

销毁输入法面板。需先通过 [createPanel](#createpanel) 创建面板后调用。使用callback异步回调。 配对调用：   
- 必须与 [createPanel](#createpanel) 方法配合使用，用于销毁由createPanel()创建的输入法面板。   
- 销毁的面板必须是已成功创建的面板对象。   
- 未正确销毁面板会导致资源泄漏，建议在面板使用完毕后及时调用destroyPanel()释放资源。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| panel | Panel | 是 | 要销毁的面板对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当输入法面板销毁成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 创建面板信息，设置面板类型为软键盘，状态为固定态
let panelInfo: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}

// 在InputMethodExtensionAbility类中使用
let inputPanel: inputMethodEngine.Panel | undefined = undefined;
inputMethodEngine.getInputMethodAbility().createPanel(this.context, panelInfo, (err: BusinessError, panel: inputMethodEngine.Panel) => {
  if (err) {
    console.error(`Failed to create panel. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  inputPanel = panel;
  console.info('Succeed in creating panel.');
  // 创建成功后再销毁
  if (inputPanel) {
    inputMethodEngine.getInputMethodAbility().destroyPanel(inputPanel, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to destroy panel. Code is ${err.code}, message is ${err.message}`);
        return;
      }
      console.info('Succeed in destroying panel.');
    });
  }
});
```

## destroyPanel

```TypeScript
destroyPanel(panel: Panel): Promise<void>
```

销毁输入法面板。使用promise异步回调。 配对调用：   
- 必须与 [createPanel](#createpanel) 方法配合使用，用于销毁由createPanel()创建的输入法面板。   
- 销毁的面板必须是已成功创建的面板对象。   
- 未正确销毁面板会导致资源泄漏，建议在面板使用完毕后及时调用destroyPanel()释放资源。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| panel | Panel | 是 | 要销毁的面板对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 创建面板信息，设置面板类型为软键盘，状态为固定态
let panelInfo: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}

let inputPanel: inputMethodEngine.Panel | undefined = undefined;
// context为InputMethodExtensionAbility类提供的上下文对象，无需额外获取
if (this.context) {
  inputMethodEngine.getInputMethodAbility()
    .createPanel(this.context, panelInfo, (err: BusinessError, panel: inputMethodEngine.Panel) => {
      if (err) {
        console.error(`Failed to create panel. Code is ${err.code}, message is ${err.message}`);
        return;
      }
      inputPanel = panel;
      console.info('Succeed in creating panel.');
    })
}

if (inputPanel) {
  inputMethodEngine.getInputMethodAbility().destroyPanel(inputPanel).then(() => {
    console.info('Succeed in destroying panel.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to destroy panel. Code is ${err.code}, message is ${err.message}`);
  });
}
```

## getSecurityMode

```TypeScript
getSecurityMode(): SecurityMode
```

获取输入法应用的当前安全模式。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SecurityMode](arkts-ime-inputmethodengine-securitymode-e.md) | 安全模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800004](../errorcode-inputmethod-framework.md#12800004-不是输入法应用) | not an input method application. |

**示例**

```TypeScript
let security: inputMethodEngine.SecurityMode = inputMethodEngine.getInputMethodAbility().getSecurityMode();
console.info(`getSecurityMode, securityMode is : ${security}`);
```

## off('inputStart')

```TypeScript
off(type: 'inputStart', callback?: (kbController: KeyboardController, inputClient: InputClient) => void): void
```

取消订阅输入法绑定成功事件。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'inputStart' | 是 | 设置监听类型，固定取值为'inputStart'。 |
| callback | (kbController: KeyboardController, inputClient: InputClient) =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility().off('inputStart');
```

## off('inputStop')

```TypeScript
off(type: 'inputStop', callback: () => void): void
```

取消订阅停止输入法应用事件。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'inputStop' | 是 | 设置监听类型，固定取值为'inputStop'。 |
| callback | () =&gt; void | 是 | 取消订阅的回调函数。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility().off('inputStop', () => {
  console.info('inputMethodAbility delete inputStop notification.');
});
```

## off('setCallingWindow')

```TypeScript
off(type: 'setCallingWindow', callback: (wid: number) => void): void
```

取消订阅设置调用窗口事件。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'setCallingWindow' | 是 | 设置监听类型，固定取值为'setCallingWindow'。 |
| callback | (wid: number) =&gt; void | 是 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility().off('setCallingWindow', (windowId: number) => {
  console.info('inputMethodAbility delete setCallingWindow notification.');
});
```

## off('keyboardShow' | 'keyboardHide')

```TypeScript
off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void
```

取消订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyboardShow' \| 'keyboardHide' | 是 | 设置监听类型。   - 'keyboardShow'表示显示输入法软键盘。   - 'keyboardHide'表示隐 藏输入法软键盘。 |
| callback | () =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility().off('keyboardShow', () => {
  console.info('InputMethodAbility delete keyboardShow notification.');
});
inputMethodEngine.getInputMethodAbility().off('keyboardHide', () => {
  console.info('InputMethodAbility delete keyboardHide notification.');
});
```

## off('keyboardShow' | 'keyboardHide')

```TypeScript
off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void
```

取消订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyboardShow' \| 'keyboardHide' | 是 | 设置监听类型。   - 'keyboardShow'表示显示输入法软键盘。   - 'keyboardHide'表示隐 藏输入法软键盘。 |
| callback | () =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例**

参见 off

## off('setSubtype')

```TypeScript
off(type: 'setSubtype', callback?: (inputMethodSubtype: InputMethodSubtype) => void): void
```

取消订阅设置输入法子类型事件。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'setSubtype' | 是 | 设置监听类型，固定取值为'setSubtype'。 |
| callback | (inputMethodSubtype: InputMethodSubtype) =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility().off('setSubtype', () => {
  console.info('InputMethodAbility delete setSubtype notification.');
});
```

## off('securityModeChange')

```TypeScript
off(type: 'securityModeChange', callback?: Callback<SecurityMode>): void
```

取消订阅输入法安全模式改变类型事件。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'securityModeChange' | 是 | 设置监听类型，固定取值为'securityModeChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SecurityMode](arkts-ime-inputmethodengine-securitymode-e.md)&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例**

```TypeScript
let securityChangeCallback: (securityMode: inputMethodEngine.SecurityMode) => void =
  (securityMode: inputMethodEngine.SecurityMode) => {
    console.info(`InputMethodAbility securityModeChange, security is ${securityMode}`);
  };
let inputMethodAbility: inputMethodEngine.InputMethodAbility = inputMethodEngine.getInputMethodAbility();
inputMethodAbility.on('securityModeChange', securityChangeCallback);
inputMethodAbility.off('securityModeChange', securityChangeCallback);
```

## off('privateCommand')

```TypeScript
off(type: 'privateCommand', callback?: Callback<Record<string, CommandDataType>>): void
```

取消订阅输入法私有数据事件。使用callback异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'privateCommand' | 是 | 设置监听类型，固定取值为'privateCommand'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, CommandDataType&gt;&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800010](../errorcode-inputmethod-framework.md#12800010-不是系统配置的默认输入法) | not the preconfigured default input method. |

**示例**

```TypeScript
let privateCommandCallback: (record: Record<string, inputMethodEngine.CommandDataType>) => void =
  (record: Record<string, inputMethodEngine.CommandDataType>) => {
    for (const key in record) {
      console.info(`private command key: ${key}, value: ${record[key]}`);
    }
  }

inputMethodEngine.getInputMethodAbility().off('privateCommand', privateCommandCallback);
```

## off('callingDisplayDidChange')

```TypeScript
off(type: 'callingDisplayDidChange', callback?: Callback<number>): void
```

取消订阅编辑框对应窗口所在屏幕ID变化事件。使用callback异步回调。

**起始版本：** 18

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callingDisplayDidChange' | 是 | 设置监听类型，固定取值为'callingDisplayDidChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility().off('callingDisplayDidChange', (displayId: number) => {
  console.info('InputMethodAbility delete calling display notification.');
});
```

## off('discardTypingText')

```TypeScript
off(type: 'discardTypingText', callback?: Callback<void>): void
```

取消订阅编辑框应用发送\u201c清空候选词\u201d事件到输入法。使用callback异步回调。 使用场景：编辑框应用需要通知输入法清空当前候选词列表时使用（如用户切换输入框、提交表单后等场景）。 使用后效果：当编辑框应用发送清空候选词请求时触发回调，输入法应用应在回调中清空候选词列表和预输入文本。

**起始版本：** 20

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discardTypingText' | 是 | 设置监听类型，固定取值为'discardTypingText'。    - 'discardTypingText'：表示取消订阅编辑框应用发送“清 空候选词”事件到输入法。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility().off('discardTypingText', () => {
  console.info('InputMethodAbility discard the typing text.');
});
```

## on('inputStart')

```TypeScript
on(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) => void): void
```

订阅输入法绑定成功事件。使用callback异步回调。 使用场景：输入法应用需要在编辑框获得焦点并绑定输入法时，获取KeyboardController和InputClient实例以进行后续的键盘操作和文本交互。 使用后效果：当编辑框绑定到输入法应用时，触发回调并返回KeyboardController和InputClient实例。输入法应用可在回调中创建面板、加载键盘页面、订阅KeyboardDelegate事件等。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'inputStart' | 是 | 设置监听类型，固定取值为'inputStart'。 |
| callback | (kbController: KeyboardController, inputClient: InputClient) =&gt; void | 是 | 回调函数，返回输入法操作相关实例。kbController为键盘控制器实例，用于控制键盘显示/隐藏；inputClient为输入客户端实例，用于与编辑框进行文本交 互。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility()
  .on('inputStart',
    (keyboardController: inputMethodEngine.KeyboardController, inputClient: inputMethodEngine.InputClient) => {
      // 使用kbController和client进行相关操作
    });
```

## on('inputStop')

```TypeScript
on(type: 'inputStop', callback: () => void): void
```

订阅停止输入法应用事件。使用callback异步回调。 使用场景：输入法应用需要在编辑框失去焦点或用户切换输入法时，执行清理操作（如隐藏面板、释放资源）。 使用后效果：当输入法应用被停止绑定时触发回调。输入法应用应在回调中隐藏面板、取消事件订阅、释放InputClient相关资源。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'inputStop' | 是 | 设置监听类型，固定取值为'inputStop'。 |
| callback | () =&gt; void | 是 | 回调函数，无返回参数。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility().on('inputStop', () => {
  console.info('inputMethodAbility inputStop');
});
```

## on('setCallingWindow')

```TypeScript
on(type: 'setCallingWindow', callback: (wid: number) => void): void
```

订阅设置调用窗口事件。使用callback异步回调。 使用场景：输入法应用需要在绑定应用的窗口发生变化时（如应用切换窗口、多窗口场景），调整面板位置或重新定位。 使用后效果：当调用方窗口发生变化时触发回调，返回新的窗口ID。输入法应用可根据窗口ID调整面板位置。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'setCallingWindow' | 是 | 设置监听类型，固定取值为'setCallingWindow'。 |
| callback | (wid: number) =&gt; void | 是 | 回调函数，参数为调用方窗口的Id。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility().on('setCallingWindow', (windowId: number) => {
  console.info('inputMethodAbility setCallingWindow');
});
```

## on('keyboardShow' | 'keyboardHide')

```TypeScript
on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void
```

订阅输入法软键盘显示或隐藏事件。使用callback异步回调。 使用场景：输入法应用需要在软键盘显示/隐藏时，执行相应的界面更新操作（如调整面板布局、更新候选词区域）。 使用后效果：当软键盘显示请求触发时，'keyboardShow'回调被调用，输入法应用应在回调中调用panel.show()显示面板；当软键盘隐藏请求触发时，'keyboardHide'回调被调用，输入法应用应在回调中调用 panel.hide()隐藏面板。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyboardShow' \| 'keyboardHide' | 是 | 设置监听类型。   - 'keyboardShow'表示显示输入法软键盘。   - 'keyboardHide'表示隐 藏输入法软键盘。 |
| callback | () =&gt; void | 是 | 回调函数。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility().on('keyboardShow', () => {
  console.info('InputMethodAbility keyboardShow.');
});
inputMethodEngine.getInputMethodAbility().on('keyboardHide', () => {
  console.info('InputMethodAbility keyboardHide.');
});
```

## on('keyboardShow' | 'keyboardHide')

```TypeScript
on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void
```

订阅输入法软键盘显示或隐藏事件。使用callback异步回调。 使用场景：输入法应用需要在软键盘显示/隐藏时，执行相应的界面更新操作（如调整面板布局、更新候选词区域）。 使用后效果：当软键盘显示请求触发时，'keyboardShow'回调被调用，输入法应用应在回调中调用panel.show()显示面板；当软键盘隐藏请求触发时，'keyboardHide'回调被调用，输入法应用应在回调中调用 panel.hide()隐藏面板。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyboardShow' \| 'keyboardHide' | 是 | 设置监听类型。   - 'keyboardShow'表示显示输入法软键盘。   - 'keyboardHide'表示隐 藏输入法软键盘。 |
| callback | () =&gt; void | 是 | 回调函数。 |

**示例**

参见 on

## on('setSubtype')

```TypeScript
on(type: 'setSubtype', callback: (inputMethodSubtype: InputMethodSubtype) => void): void
```

订阅设置输入法子类型事件。使用callback异步回调。 使用场景：输入法应用需要在子类型（如语言、输入模式）发生变化时，切换到对应的键盘布局或输入逻辑。 使用后效果：当输入法子类型变化时触发回调，返回新的输入法子类型信息。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'setSubtype' | 是 | 设置监听类型，固定取值为'setSubtype'。 |
| callback | (inputMethodSubtype: InputMethodSubtype) =&gt; void | 是 | 回调函数，返回设置的输入法子类型（InputMethodSubtype，输入法子类型）。 |

**示例**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';

inputMethodEngine.getInputMethodAbility().on('setSubtype', (inputMethodSubtype: InputMethodSubtype) => {
  console.info('InputMethodAbility setSubtype.');
});
```

## on('securityModeChange')

```TypeScript
on(type: 'securityModeChange', callback: Callback<SecurityMode>): void
```

订阅输入法安全模式改变类型事件。使用callback异步回调。 使用场景：输入法应用需要在安全模式发生变化时（如编辑框切换到密码输入模式、隐私模式等），调整键盘行为（如禁止截图、切换到安全键盘布局等）。 使用后效果：当安全模式变化时触发回调，返回当前的安全模式值。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'securityModeChange' | 是 | 设置监听类型，固定取值为'securityModeChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SecurityMode](arkts-ime-inputmethodengine-securitymode-e.md)&gt; | 是 | 回调函数，返回当前输入法应用的安全模式。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility()
  .on('securityModeChange', (securityMode: inputMethodEngine.SecurityMode) => {
    console.info(`InputMethodAbility securityModeChange, security is ${securityMode}`);
  });
```

## on('privateCommand')

```TypeScript
on(type: 'privateCommand', callback: Callback<Record<string, CommandDataType>>): void
```

订阅输入法私有数据事件。使用callback异步回调。 使用场景：应用与输入法之间需要传递私有数据（如自定义命令、配置信息等）时使用。仅系统默认输入法应用可订阅此事件。 使用后效果：当绑定应用向输入法发送私有数据时触发回调，返回私有数据记录。

**起始版本：** 12

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'privateCommand' | 是 | 设置监听类型，固定取值为'privateCommand'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, CommandDataType&gt;&gt; | 是 | 回调函数，返回向输入法应用发送的私有数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800010](../errorcode-inputmethod-framework.md#12800010-不是系统配置的默认输入法) | not the preconfigured default input method. |

**示例**

```TypeScript
let privateCommandCallback: (record: Record<string, inputMethodEngine.CommandDataType>) => void =
  (record: Record<string, inputMethodEngine.CommandDataType>) => {
    for (const key in record) {
      console.info(`private command key: ${key}, value: ${record[key]}`);
    }
  }
inputMethodEngine.getInputMethodAbility().on('privateCommand', privateCommandCallback);
```

## on('callingDisplayDidChange')

```TypeScript
on(type: 'callingDisplayDidChange', callback: Callback<number>): void
```

订阅编辑框对应窗口所在屏幕ID变化事件。使用callback异步回调。 使用场景：多屏幕设备场景下，编辑框在不同屏幕间切换时，输入法应用需根据新的屏幕ID调整面板位置和大小。 使用后效果：当编辑框所在屏幕ID发生变化时触发回调，返回新的屏幕ID。

**起始版本：** 18

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callingDisplayDidChange' | 是 | 设置监听类型，固定取值为'callingDisplayDidChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 回调函数，返回编辑框设置对应窗口屏幕ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility().on('callingDisplayDidChange', (displayId: number) => {
  console.info(`display id: ${displayId}`);
});
inputMethodEngine.getInputMethodAbility().on('callingDisplayDidChange', callingDisplayDidChangeCallback);
```

## on('discardTypingText')

```TypeScript
on(type: 'discardTypingText', callback: Callback<void>): void
```

订阅编辑框应用发送\u201c清空候选词\u201d事件到输入法。使用callback异步回调。 使用场景：编辑框应用需要通知输入法清空当前候选词列表时使用（如用户切换输入框、提交表单后等场景）。 使用后效果：当编辑框应用发送清空候选词请求时触发回调，输入法应用应在回调中清空候选词列表和预输入文本。

**起始版本：** 20

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discardTypingText' | 是 | 设置监听类型，固定取值为'discardTypingText'。    - 'discardTypingText'：表示订阅编辑框应用发送“清空候 选词”事件到输入法。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**示例**

```TypeScript
inputMethodEngine.getInputMethodAbility().on('discardTypingText', () => {
  console.info('InputMethodAbility discard the typing text.');
});
```
