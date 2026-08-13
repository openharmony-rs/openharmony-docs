# InputMethodAbility

InputMethodAbility是输入法应用的核心能力对象，提供输入法生命周期管理、面板创建与销毁、事件订阅等功能。输入法应用通过 [getInputMethodAbility](arkts-ime-inputmethodengine-getinputmethodability-f.md#getInputMethodAbility)获取该实例。 下列API均需使用[getInputMethodAbility](arkts-ime-inputmethodengine-getinputmethodability-f.md#getInputMethodAbility)获取到InputMethodAbility实例后，通过实例调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputMethodEngine-interface InputMethodAbility--><!--Device-inputMethodEngine-interface InputMethodAbility-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## createPanel

```TypeScript
createPanel(ctx: BaseContext, info: PanelInfo, callback: AsyncCallback<Panel>): void
```

创建输入法面板，仅支持输入法应用在 [InputMethodExtensionAbility](arkts-ime-inputmethodextensionability-c.md#InputMethodExtensionAbility)（输入法扩展能力）类中调用。使 用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-createPanel(ctx: BaseContext, info: PanelInfo, callback: AsyncCallback<Panel>): void--><!--Device-InputMethodAbility-createPanel(ctx: BaseContext, info: PanelInfo, callback: AsyncCallback<Panel>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | 是 | 当前输入法应用上下文信息。 |
| info | PanelInfo | 是 | 输入法面板信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Panel&gt; | 是 | 回调函数。当输入法面板创建成功，返回当前创建的输入法面板对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800004](../errorcode-inputmethod-framework.md#12800004-不是输入法应用) | not an input method application. |

## 示例

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

创建输入法面板，仅支持输入法应用在 [InputMethodExtensionAbility](arkts-ime-inputmethodextensionability-c.md#InputMethodExtensionAbility)类中调用。使用promise异 步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-createPanel(ctx: BaseContext, info: PanelInfo): Promise<Panel>--><!--Device-InputMethodAbility-createPanel(ctx: BaseContext, info: PanelInfo): Promise<Panel>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | 是 | 当前输入法应用上下文信息。 |
| info | PanelInfo | 是 | 输入法面板信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Panel&gt; | the promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800004](../errorcode-inputmethod-framework.md#12800004-不是输入法应用) | not an input method application. |

## 示例

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

销毁输入法面板。需先通过 createPanel 创建面板后调用。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-destroyPanel(panel: Panel, callback: AsyncCallback<void>): void--><!--Device-InputMethodAbility-destroyPanel(panel: Panel, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| panel | Panel | 是 | 要销毁的面板对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当输入法面板销毁成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

## 示例

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
  inputMethodEngine.getInputMethodAbility().destroyPanel(inputPanel, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to destroy panel. Code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info('Succeed in destroying panel.');
  })
}
```

## destroyPanel

```TypeScript
destroyPanel(panel: Panel): Promise<void>
```

销毁输入法面板。使用promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-destroyPanel(panel: Panel): Promise<void>--><!--Device-InputMethodAbility-destroyPanel(panel: Panel): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| panel | Panel | 是 | 要销毁的面板对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

## 示例

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

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-getSecurityMode(): SecurityMode--><!--Device-InputMethodAbility-getSecurityMode(): SecurityMode-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SecurityMode](arkts-ime-inputmethodengine-securitymode-e.md) | 安全模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800004](../errorcode-inputmethod-framework.md#12800004-不是输入法应用) | not an input method application. |

## 示例

```TypeScript
let security: inputMethodEngine.SecurityMode = inputMethodEngine.getInputMethodAbility().getSecurityMode();
console.error(`getSecurityMode, securityMode is : ${security}`);
```

## offCallingDisplayDidChange

```TypeScript
offCallingDisplayDidChange(callback?: Callback<int>): void
```

取消编辑框对应窗口所在屏幕ID变化。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-offCallingDisplayDidChange(callback?: Callback<int>): void--><!--Device-InputMethodAbility-offCallingDisplayDidChange(callback?: Callback<int>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 否 | 取消订阅的回调函数。 参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let inputMethodAbility = inputMethodEngine.getInputMethodAbility();

console.info(`unregist calling display changed `);
inputMethodAbility!.offCallingDisplayDidChange((num: int) => {
  console.info('inputMethodAbility delete calling display  notification.');
});
```

## offDiscardTypingText

```TypeScript
offDiscardTypingText(callback?: Callback<void>): void
```

取消订阅编辑框应用发送“清空候选词”事件到输入法。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-offDiscardTypingText(callback?: Callback<void>): void--><!--Device-InputMethodAbility-offDiscardTypingText(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import inputMethodEngine from '@ohos.inputMethodEngine';

let inputMethodAbility = inputMethodEngine.getInputMethodAbility();
console.info(`discard the typing text`);
inputMethodAbility!.offDiscardTypingText(() => {
  console.info('inputMethodAbility discard the typing text.');
});
```

## offInputStart

```TypeScript
offInputStart(callback?: IMAInputStartCallback): void
```

取消订阅输入法绑定成功事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-offInputStart(callback?: IMAInputStartCallback): void--><!--Device-InputMethodAbility-offInputStart(callback?: IMAInputStartCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [IMAInputStartCallback](arkts-ime-inputmethodengine-imainputstartcallback-t.md) | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();

inputMethodAbility!
  .offInputStart((kbController: inputMethodEngine.KeyboardController, textClient: inputMethodEngine.InputClient) => {
  console.info('delete inputStart notification.');
});
```

## offInputStop

```TypeScript
offInputStop(callback: Callback<void>): void
```

取消订阅输入法输入停止（inputStop）事件，停止监听系统要求输入法终止输入流程的触发动作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-offInputStop(callback: Callback<void>): void--><!--Device-InputMethodAbility-offInputStop(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 to terminate itself. |

## 示例

```TypeScript
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();
inputMethodAbility!.offInputStop(() => {
  console.info('inputMethodAbility delete inputStop notification.');
});
```

## offKeyboardHide

```TypeScript
offKeyboardHide(callback?: Callback<void>): void
```

取消订阅输入法键盘隐藏（keyboardHide）事件，停止监听输入法键盘隐藏的触发动作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-offKeyboardHide(callback?: Callback<void>): void--><!--Device-InputMethodAbility-offKeyboardHide(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数。 |

## 示例

```TypeScript
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();
inputMethodAbility!.offKeyboardShow(() => {
  console.info('inputMethodAbility delete keyboardShow notification.');
});
inputMethodAbility!.offKeyboardHide(() => {
  console.info('inputMethodAbility delete keyboardHide notification.');
});
```

## offKeyboardShow

```TypeScript
offKeyboardShow(callback?: Callback<void>): void
```

取消订阅输入法事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-offKeyboardShow(callback?: Callback<void>): void--><!--Device-InputMethodAbility-offKeyboardShow(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数。 |

## 示例

```TypeScript
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();

inputMethodAbility!.offKeyboardShow(() => {
  console.info('inputMethodAbility delete keyboardShow notification.');
});
inputMethodAbility!.offKeyboardHide(() => {
  console.info('inputMethodAbility delete keyboardHide notification.');
});
```

## offPrivateCommand

```TypeScript
offPrivateCommand(callback?: Callback<Record<string, CommandDataType>>): void
```

取消订阅输入法私有数据事件。使用callback异步回调。该接口只能被系统预置输入法调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-offPrivateCommand(callback?: Callback<Record<string, CommandDataType>>): void--><!--Device-InputMethodAbility-offPrivateCommand(callback?: Callback<Record<string, CommandDataType>>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Record&lt;string, CommandDataType&gt;&gt; | 否 | 回调函数，返回向输入法应用发送的私有数据。 参数不填写时，取消订阅type对应的所有回调事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800010](../errorcode-inputmethod-framework.md#12800010-不是系统配置的默认输入法) | not the preconfigured default input method. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let inputMethodAbility = inputMethodEngine.getInputMethodAbility();
let privateCommandCallback = (record: Record<string, inputMethodEngine.CommandDataType>) => {
  record.forEach((key, value) => {
    console.info(`private command key: ${key}, value: ${value}`);
  });
}
console.info(`regist private command `);
inputMethodAbility!.offPrivateCommand(privateCommandCallback);
```

## offSecurityModeChange

```TypeScript
offSecurityModeChange(callback?: Callback<SecurityMode>): void
```

取消订阅输入法安全模式改变类型事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-offSecurityModeChange(callback?: Callback<SecurityMode>): void--><!--Device-InputMethodAbility-offSecurityModeChange(callback?: Callback<SecurityMode>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SecurityMode](arkts-ime-inputmethodengine-securitymode-e.md)&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
let InputMethodEngine = inputMethodEngine.getInputMethodAbility();
let securityChangeCallback = (securityMode: inputMethodEngine.SecurityMode) => {
  console.info(`inputMethodAbility securityModeChange, security is ${securityMode}`);
};
InputMethodEngine.onSecurityModeChange(securityChangeCallback);
InputMethodEngine.offSecurityModeChange(securityChangeCallback);
```

## offSetCallingWindow

```TypeScript
offSetCallingWindow(callback: Callback<int>): void
```

取消订阅编辑框设置调用窗口 ID（setCallingWindow）事件，停止监听编辑框设置调用窗口标识的触发动作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-offSetCallingWindow(callback: Callback<int>): void--><!--Device-InputMethodAbility-offSetCallingWindow(callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 是 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();
inputMethodAbility!.offSetCallingWindow((wid: int) => {
  console.info('inputMethodAbility delete setCallingWindow notification.');
});
```

## offSetSubtype

```TypeScript
offSetSubtype(callback?: Callback<InputMethodSubtype>): void
```

取消订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-offSetSubtype(callback?: Callback<InputMethodSubtype>): void--><!--Device-InputMethodAbility-offSetSubtype(callback?: Callback<InputMethodSubtype>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md)&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 to switch subtype. |

## 示例

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();

inputMethodAbility!.offSetSubtype((inputMethodSubtype: InputMethodSubtype) => {
  console.info('inputMethodAbility setSubtype.');
});
```

## off_callingDisplayDidChange

```TypeScript
off(type: 'callingDisplayDidChange', callback?: Callback<number>): void
```

取消订阅编辑框对应窗口所在屏幕ID变化事件。使用callback异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-InputMethodAbility-off(type: 'callingDisplayDidChange', callback?: Callback<number>): void--><!--Device-InputMethodAbility-off(type: 'callingDisplayDidChange', callback?: Callback<number>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callingDisplayDidChange' | 是 | 设置监听类型，固定取值为'callingDisplayDidChange'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;number&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().off('callingDisplayDidChange', (displayId: number) => {
  console.info('InputMethodAbility delete calling display notification.');
});
```

## off_discardTypingText

```TypeScript
off(type: 'discardTypingText', callback?: Callback<void>): void
```

取消订阅编辑框应用发送\u201c清空候选词\u201d事件到输入法。使用callback异步回调。 **使用场景：** 编辑框应用需要通知输入法清空当前候选词列表时使用（如用户切换输入框、提交表单后等场景）。 **使用后效果：** 当编辑框应用发送清空候选词请求时触发回调，输入法应用应在回调中清空候选词列表和预输入文本。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-InputMethodAbility-off(type: 'discardTypingText', callback?: Callback<void>): void--><!--Device-InputMethodAbility-off(type: 'discardTypingText', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discardTypingText' | 是 | 设置监听类型，固定取值为'discardTypingText'。&lt;br/&gt; - 'discardTypingText'：表示取消订阅编辑框应用发送“清 空候选词”事件到输入法。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().off('discardTypingText', () => {
  console.info('InputMethodAbility discard the typing text.');
});
```

## off_inputStart

```TypeScript
off(type: 'inputStart', callback?: (kbController: KeyboardController, inputClient: InputClient) => void): void
```

取消订阅输入法绑定成功事件。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-InputMethodAbility-off(type: 'inputStart', callback?: (kbController: KeyboardController, inputClient: InputClient) => void): void--><!--Device-InputMethodAbility-off(type: 'inputStart', callback?: (kbController: KeyboardController, inputClient: InputClient) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'inputStart' | 是 | 设置监听类型，固定取值为'inputStart'。 |
| callback | (kbController: KeyboardController, inputClient: InputClient) =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().off('inputStart');
```

## off_inputStop

```TypeScript
off(type: 'inputStop', callback: () => void): void
```

取消订阅停止输入法应用事件。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-InputMethodAbility-off(type: 'inputStop', callback: () => void): void--><!--Device-InputMethodAbility-off(type: 'inputStop', callback: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'inputStop' | 是 | 设置监听类型，固定取值为'inputStop'。 |
| callback | () =&gt; void | 是 | 取消订阅的回调函数，用于取消特定的键盘显示/隐藏事件订阅。传入callback时取消指定回调的订阅，不传入时取消type对应的所有回调事件。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().off('inputStop', () => {
  console.info('inputMethodAbility delete inputStop notification.');
});
```

## off_keyboardHide

```TypeScript
off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void
```

取消订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-InputMethodAbility-off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void--><!--Device-InputMethodAbility-off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyboardShow' \| 'keyboardHide' | 是 | 设置监听类型。&lt;br/&gt;- 'keyboardShow'表示显示输入法软键盘。&lt;br/&gt;- 'keyboardHide'表示隐 藏输入法软键盘。 |
| callback | () =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().off('keyboardShow', () => {
  console.info('InputMethodAbility delete keyboardShow notification.');
});
inputMethodEngine.getInputMethodAbility().off('keyboardHide', () => {
  console.info('InputMethodAbility delete keyboardHide notification.');
});
```

## off_keyboardShow

```TypeScript
off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void
```

取消订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-InputMethodAbility-off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void--><!--Device-InputMethodAbility-off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyboardShow' \| 'keyboardHide' | 是 | 设置监听类型。&lt;br/&gt;- 'keyboardShow'表示显示输入法软键盘。&lt;br/&gt;- 'keyboardHide'表示隐 藏输入法软键盘。 |
| callback | () =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().off('keyboardShow', () => {
  console.info('InputMethodAbility delete keyboardShow notification.');
});
inputMethodEngine.getInputMethodAbility().off('keyboardHide', () => {
  console.info('InputMethodAbility delete keyboardHide notification.');
});
```

## off_privateCommand

```TypeScript
off(type: 'privateCommand', callback?: Callback<Record<string, CommandDataType>>): void
```

取消订阅输入法私有数据事件。使用callback异步回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-InputMethodAbility-off(type: 'privateCommand', callback?: Callback<Record<string, CommandDataType>>): void--><!--Device-InputMethodAbility-off(type: 'privateCommand', callback?: Callback<Record<string, CommandDataType>>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'privateCommand' | 是 | 设置监听类型，固定取值为'privateCommand'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Record&lt;string, CommandDataType&gt;&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800010](../errorcode-inputmethod-framework.md#12800010-不是系统配置的默认输入法) | not the preconfigured default input method. |

## 示例

```TypeScript
let privateCommandCallback: (record: Record<string, inputMethodEngine.CommandDataType>) => void =
  (record: Record<string, inputMethodEngine.CommandDataType>) => {
    for (const key in record) {
      console.info(`private command key: ${key}, value: ${record[key]}`);
    }
  }

inputMethodEngine.getInputMethodAbility().off('privateCommand', privateCommandCallback);
```

## off_securityModeChange

```TypeScript
off(type: 'securityModeChange', callback?: Callback<SecurityMode>): void
```

取消订阅输入法安全模式改变类型事件。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-InputMethodAbility-off(type: 'securityModeChange', callback?: Callback<SecurityMode>): void--><!--Device-InputMethodAbility-off(type: 'securityModeChange', callback?: Callback<SecurityMode>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'securityModeChange' | 是 | 设置监听类型，固定取值为'securityModeChange'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SecurityMode](arkts-ime-inputmethodengine-securitymode-e.md)&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
let securityChangeCallback: (securityMode: inputMethodEngine.SecurityMode) => void =
  (securityMode: inputMethodEngine.SecurityMode) => {
    console.info(`InputMethodAbility securityModeChange, security is ${securityMode}`);
  };
let inputMethodAbility: inputMethodEngine.InputMethodAbility = inputMethodEngine.getInputMethodAbility();
inputMethodAbility.on('securityModeChange', securityChangeCallback);
inputMethodAbility.off('securityModeChange', securityChangeCallback);
```

## off_setCallingWindow

```TypeScript
off(type: 'setCallingWindow', callback: (wid: number) => void): void
```

取消订阅设置调用窗口事件。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-InputMethodAbility-off(type: 'setCallingWindow', callback: (wid: number) => void): void--><!--Device-InputMethodAbility-off(type: 'setCallingWindow', callback: (wid: number) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'setCallingWindow' | 是 | 设置监听类型，固定取值为'setCallingWindow'。 |
| callback | (wid: number) =&gt; void | 是 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().off('setCallingWindow', (windowId: number) => {
  console.info('inputMethodAbility delete setCallingWindow notification.');
});
```

## off_setSubtype

```TypeScript
off(type: 'setSubtype', callback?: (inputMethodSubtype: InputMethodSubtype) => void): void
```

取消订阅设置输入法子类型事件。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-InputMethodAbility-off(type: 'setSubtype', callback?: (inputMethodSubtype: InputMethodSubtype) => void): void--><!--Device-InputMethodAbility-off(type: 'setSubtype', callback?: (inputMethodSubtype: InputMethodSubtype) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'setSubtype' | 是 | 设置监听类型，固定取值为'setSubtype'。 |
| callback | (inputMethodSubtype: InputMethodSubtype) =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().off('setSubtype', () => {
  console.info('InputMethodAbility delete setSubtype notification.');
});
```

## onCallingDisplayDidChange

```TypeScript
onCallingDisplayDidChange(callback: Callback<int>): void
```

订阅编辑框对应窗口所在屏幕ID变化。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-onCallingDisplayDidChange(callback: Callback<int>): void--><!--Device-InputMethodAbility-onCallingDisplayDidChange(callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 是 | 回调函数，返回编辑框设置对应窗口屏幕ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let inputMethodAbility = inputMethodEngine.getInputMethodAbility();
let callingDisplayDidChangeCallback = (num: int) => {
  console.info(`display id: ${num}`);
}

console.info(`regist calling display changed`);
inputMethodAbility!.onCallingDisplayDidChange(callingDisplayDidChangeCallback);
```

## onDiscardTypingText

```TypeScript
onDiscardTypingText(callback: Callback<void>): void
```

订阅编辑框应用发送“清空候选词”事件到输入法。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-onDiscardTypingText(callback: Callback<void>): void--><!--Device-InputMethodAbility-onDiscardTypingText(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import inputMethodEngine from '@ohos.inputMethodEngine';

let inputMethodAbility = inputMethodEngine.getInputMethodAbility();
console.info(`discard the typing text`);
inputMethodAbility!.onDiscardTypingText(() => {
  console.info('inputMethodAbility discard the typing text.');
});
```

## onInputStart

```TypeScript
onInputStart(callback: IMAInputStartCallback): void
```

订阅输入法绑定成功事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-onInputStart(callback: IMAInputStartCallback): void--><!--Device-InputMethodAbility-onInputStart(callback: IMAInputStartCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [IMAInputStartCallback](arkts-ime-inputmethodengine-imainputstartcallback-t.md) | 是 | 回调函数，返回订阅输入法的KeyboardController和TextInputClient实例。 |

## 示例

```TypeScript
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();

inputMethodAbility!
.onInputStart((kbController: inputMethodEngine.KeyboardController, client: inputMethodEngine.InputClient) => {
  let keyboardController = kbController;
  let inputClient = client;
});
```

## onInputStop

```TypeScript
onInputStop(callback: Callback<void>): void
```

订阅停止输入法应用事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-onInputStop(callback: Callback<void>): void--><!--Device-InputMethodAbility-onInputStop(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 系统要求输入法终止输入流程时触发的回调函数，无入参，用于执行输入停止后的清理逻辑（如隐藏键盘、释放资源等）。 to terminate itself. |

## 示例

```TypeScript
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();
inputMethodAbility!.onInputStop(() => {
  console.info('inputMethodAbility inputStop');
});
```

## onKeyboardHide

```TypeScript
onKeyboardHide(callback: Callback<void>): void
```

订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-onKeyboardHide(callback: Callback<void>): void--><!--Device-InputMethodAbility-onKeyboardHide(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数。 |

## 示例

```TypeScript
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();
inputMethodAbility!.onKeyboardShow(() => {
  console.info('inputMethodEngine keyboardShow.');
});
inputMethodAbility!.onKeyboardHide(() => {
  console.info('inputMethodEngine keyboardHide.');
});
```

## onKeyboardShow

```TypeScript
onKeyboardShow(callback: Callback<void>): void
```

订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-onKeyboardShow(callback: Callback<void>): void--><!--Device-InputMethodAbility-onKeyboardShow(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数。 |

## 示例

```TypeScript
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();
inputMethodAbility!.onKeyboardShow(() => {
  console.info('inputMethodEngine keyboardShow.');
});
inputMethodAbility!.onKeyboardHide(() => {
  console.info('inputMethodEngine keyboardHide.');
});
```

## onPrivateCommand

```TypeScript
onPrivateCommand(callback: Callback<Record<string, CommandDataType>>): void
```

订阅输入法私有数据事件。使用callback异步回调。该接口只能被系统预置输入法调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-onPrivateCommand(callback: Callback<Record<string, CommandDataType>>): void--><!--Device-InputMethodAbility-onPrivateCommand(callback: Callback<Record<string, CommandDataType>>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Record&lt;string, CommandDataType&gt;&gt; | 是 | 回调函数，返回向输入法应用发送的私有数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800010](../errorcode-inputmethod-framework.md#12800010-不是系统配置的默认输入法) | not the preconfigured default input method. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let inputMethodAbility = inputMethodEngine.getInputMethodAbility();

let privateCommandCallback = (record: Record<string, inputMethodEngine.CommandDataType>) => {
  record.forEach((key, value) => {
    console.info(`private command key: ${key}, value: ${value}`);
  });
}

console.info(`regist private command `);
inputMethodAbility!.onPrivateCommand(privateCommandCallback);
```

## onSecurityModeChange

```TypeScript
onSecurityModeChange(callback: Callback<SecurityMode>): void
```

订阅输入法安全模式改变类型事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-onSecurityModeChange(callback: Callback<SecurityMode>): void--><!--Device-InputMethodAbility-onSecurityModeChange(callback: Callback<SecurityMode>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SecurityMode](arkts-ime-inputmethodengine-securitymode-e.md)&gt; | 是 | 回调函数，返回当前输入法应用的安全模式。 |

## 示例

```TypeScript
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();

inputMethodAbility!.onSecurityModeChange((securityMode: inputMethodEngine.SecurityMode) => {
  console.info(`inputMethodAbility securityModeChange, security is ${securityMode}`);
});
```

## onSetCallingWindow

```TypeScript
onSetCallingWindow(callback: Callback<int>): void
```

订阅设置调用窗口事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-onSetCallingWindow(callback: Callback<int>): void--><!--Device-InputMethodAbility-onSetCallingWindow(callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 是 | 回调函数，返回调用方窗口的Id。 |

## 示例

```TypeScript
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();
inputMethodAbility!.onSetCallingWindow((wid: int) => {
  console.info('inputMethodAbility setCallingWindow');
});
```

## onSetSubtype

```TypeScript
onSetSubtype(callback: Callback<InputMethodSubtype>): void
```

订阅设置输入法子类型事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-InputMethodAbility-onSetSubtype(callback: Callback<InputMethodSubtype>): void--><!--Device-InputMethodAbility-onSetSubtype(callback: Callback<InputMethodSubtype>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md)&gt; | 是 | 回调函数，返回设置的输入法子类型。 to switch subtype. |

## 示例

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
let inputMethodAbility = inputMethodEngine.getInputMethodAbility();

inputMethodAbility!.onSetSubtype((inputMethodSubtype: InputMethodSubtype) => {
  console.info('inputMethodAbility setSubtype.');
});
```

## on_callingDisplayDidChange

```TypeScript
on(type: 'callingDisplayDidChange', callback: Callback<number>): void
```

订阅编辑框对应窗口所在屏幕ID变化事件。使用callback异步回调。 **使用场景：** 多屏幕设备场景下，编辑框在不同屏幕间切换时，输入法应用需根据新的屏幕ID调整面板位置和大小。 **使用后效果：** 当编辑框所在屏幕ID发生变化时触发回调，返回新的屏幕ID。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-InputMethodAbility-on(type: 'callingDisplayDidChange', callback: Callback<number>): void--><!--Device-InputMethodAbility-on(type: 'callingDisplayDidChange', callback: Callback<number>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callingDisplayDidChange' | 是 | 设置监听类型，固定取值为'callingDisplayDidChange'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;number&gt; | 是 | 回调函数，返回编辑框设置对应窗口屏幕ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().on('callingDisplayDidChange', (displayId: number) => {
  console.info(`display id: ${displayId}`);
});
inputMethodEngine.getInputMethodAbility().on('callingDisplayDidChange', callingDisplayDidChangeCallback);
```

## on_discardTypingText

```TypeScript
on(type: 'discardTypingText', callback: Callback<void>): void
```

订阅编辑框应用发送\u201c清空候选词\u201d事件到输入法。使用callback异步回调。 **使用场景：** 编辑框应用需要通知输入法清空当前候选词列表时使用（如用户切换输入框、提交表单后等场景）。 **使用后效果：** 当编辑框应用发送清空候选词请求时触发回调，输入法应用应在回调中清空候选词列表和预输入文本。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-InputMethodAbility-on(type: 'discardTypingText', callback: Callback<void>): void--><!--Device-InputMethodAbility-on(type: 'discardTypingText', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discardTypingText' | 是 | 设置监听类型，固定取值为'discardTypingText'。&lt;br/&gt; - 'discardTypingText'：表示订阅编辑框应用发送“清空候 选词”事件到输入法。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().on('discardTypingText', () => {
  console.info('InputMethodAbility discard the typing text.');
});
```

## on_inputStart

```TypeScript
on(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) => void): void
```

订阅输入法绑定成功事件。使用callback异步回调。 **使用场景：** 输入法应用需要在编辑框获得焦点并绑定输入法时，获取KeyboardController和InputClient实例以进行后续的键盘操作和文本交互。 **使用后效果：** 当编辑框绑定到输入法应用时，触发回调并返回KeyboardController和InputClient实例。输入法应用可在回调中创建面板、加载键盘页面、订阅KeyboardDelegate事件等。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-InputMethodAbility-on(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) => void): void--><!--Device-InputMethodAbility-on(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'inputStart' | 是 | 设置监听类型，固定取值为'inputStart'。 |
| callback | (kbController: KeyboardController, inputClient: InputClient) =&gt; void | 是 | 回调函数，返回输入法操作相关实例。kbController为键盘控制器实例，用于控制键盘显示/隐藏；inputClient为输入客户端实例，用于与编辑框进行文本交 互。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility()
  .on('inputStart',
    (keyboardController: inputMethodEngine.KeyboardController, inputClient: inputMethodEngine.InputClient) => {
      // 使用kbController和client进行相关操作
    });
```

## on_inputStop

```TypeScript
on(type: 'inputStop', callback: () => void): void
```

订阅停止输入法应用事件。使用callback异步回调。 **使用场景：** 输入法应用需要在编辑框失去焦点或用户切换输入法时，执行清理操作（如隐藏面板、释放资源）。 **使用后效果：** 当输入法应用被停止绑定时触发回调。输入法应用应在回调中隐藏面板、取消事件订阅、释放InputClient相关资源。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-InputMethodAbility-on(type: 'inputStop', callback: () => void): void--><!--Device-InputMethodAbility-on(type: 'inputStop', callback: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'inputStop' | 是 | 设置监听类型，固定取值为'inputStop'。 |
| callback | () =&gt; void | 是 | 回调函数，无返回参数。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().on('inputStop', () => {
  console.info('inputMethodAbility inputStop');
});
```

## on_keyboardHide

```TypeScript
on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void
```

订阅输入法软键盘显示或隐藏事件。使用callback异步回调。 **使用场景：** 输入法应用需要在软键盘显示/隐藏时，执行相应的界面更新操作（如调整面板布局、更新候选词区域）。 **使用后效果：** 当软键盘显示请求触发时，'keyboardShow'回调被调用，输入法应用应在回调中调用panel.show()显示面板；当软键盘隐藏请求触发时，'keyboardHide'回调被调用，输入法应用应在回调 中调用panel.hide()隐藏面板。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-InputMethodAbility-on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void--><!--Device-InputMethodAbility-on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyboardShow' \| 'keyboardHide' | 是 | 设置监听类型。&lt;br/&gt;- 'keyboardShow'表示显示输入法软键盘。&lt;br/&gt;- 'keyboardHide'表示隐 藏输入法软键盘。 |
| callback | () =&gt; void | 是 | 回调函数。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().on('keyboardShow', () => {
  console.info('InputMethodAbility keyboardShow.');
});
inputMethodEngine.getInputMethodAbility().on('keyboardHide', () => {
  console.info('InputMethodAbility keyboardHide.');
});
```

## on_keyboardShow

```TypeScript
on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void
```

订阅输入法软键盘显示或隐藏事件。使用callback异步回调。 **使用场景：** 输入法应用需要在软键盘显示/隐藏时，执行相应的界面更新操作（如调整面板布局、更新候选词区域）。 **使用后效果：** 当软键盘显示请求触发时，'keyboardShow'回调被调用，输入法应用应在回调中调用panel.show()显示面板；当软键盘隐藏请求触发时，'keyboardHide'回调被调用，输入法应用应在回调 中调用panel.hide()隐藏面板。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-InputMethodAbility-on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void--><!--Device-InputMethodAbility-on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyboardShow' \| 'keyboardHide' | 是 | 设置监听类型。&lt;br/&gt;- 'keyboardShow'表示显示输入法软键盘。&lt;br/&gt;- 'keyboardHide'表示隐 藏输入法软键盘。 |
| callback | () =&gt; void | 是 | 回调函数。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().on('keyboardShow', () => {
  console.info('InputMethodAbility keyboardShow.');
});
inputMethodEngine.getInputMethodAbility().on('keyboardHide', () => {
  console.info('InputMethodAbility keyboardHide.');
});
```

## on_privateCommand

```TypeScript
on(type: 'privateCommand', callback: Callback<Record<string, CommandDataType>>): void
```

订阅输入法私有数据事件。使用callback异步回调。 **使用场景：** 应用与输入法之间需要传递私有数据（如自定义命令、配置信息等）时使用。仅系统默认输入法应用可订阅此事件。 **使用后效果：** 当绑定应用向输入法发送私有数据时触发回调，返回私有数据记录。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-InputMethodAbility-on(type: 'privateCommand', callback: Callback<Record<string, CommandDataType>>): void--><!--Device-InputMethodAbility-on(type: 'privateCommand', callback: Callback<Record<string, CommandDataType>>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'privateCommand' | 是 | 设置监听类型，固定取值为'privateCommand'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Record&lt;string, CommandDataType&gt;&gt; | 是 | 回调函数，返回向输入法应用发送的私有数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800010](../errorcode-inputmethod-framework.md#12800010-不是系统配置的默认输入法) | not the preconfigured default input method. |

## 示例

```TypeScript
let privateCommandCallback: (record: Record<string, inputMethodEngine.CommandDataType>) => void =
  (record: Record<string, inputMethodEngine.CommandDataType>) => {
    for (const key in record) {
      console.info(`private command key: ${key}, value: ${record[key]}`);
    }
  }
inputMethodEngine.getInputMethodAbility().on('privateCommand', privateCommandCallback);
```

## on_securityModeChange

```TypeScript
on(type: 'securityModeChange', callback: Callback<SecurityMode>): void
```

订阅输入法安全模式改变类型事件。使用callback异步回调。 **使用场景：** 输入法应用需要在安全模式发生变化时（如编辑框切换到密码输入模式、隐私模式等），调整键盘行为（如禁止截图、切换到安全键盘布局等）。 **使用后效果：** 当安全模式变化时触发回调，返回当前的安全模式值。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-InputMethodAbility-on(type: 'securityModeChange', callback: Callback<SecurityMode>): void--><!--Device-InputMethodAbility-on(type: 'securityModeChange', callback: Callback<SecurityMode>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'securityModeChange' | 是 | 设置监听类型，固定取值为'securityModeChange'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SecurityMode](arkts-ime-inputmethodengine-securitymode-e.md)&gt; | 是 | 回调函数，返回当前输入法应用的安全模式。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility()
  .on('securityModeChange', (securityMode: inputMethodEngine.SecurityMode) => {
    console.info(`InputMethodAbility securityModeChange, security is ${securityMode}`);
  });
```

## on_setCallingWindow

```TypeScript
on(type: 'setCallingWindow', callback: (wid: number) => void): void
```

订阅设置调用窗口事件。使用callback异步回调。 **使用场景：** 输入法应用需要在绑定应用的窗口发生变化时（如应用切换窗口、多窗口场景），调整面板位置或重新定位。 **使用后效果：** 当调用方窗口发生变化时触发回调，返回新的窗口ID。输入法应用可根据窗口ID调整面板位置。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-InputMethodAbility-on(type: 'setCallingWindow', callback: (wid: number) => void): void--><!--Device-InputMethodAbility-on(type: 'setCallingWindow', callback: (wid: number) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'setCallingWindow' | 是 | 设置监听类型，固定取值为'setCallingWindow'。 |
| callback | (wid: number) =&gt; void | 是 | 回调函数，参数为调用方窗口的Id。 |

## 示例

```TypeScript
inputMethodEngine.getInputMethodAbility().on('setCallingWindow', (windowId: number) => {
  console.info('inputMethodAbility setCallingWindow');
});
```

## on_setSubtype

```TypeScript
on(type: 'setSubtype', callback: (inputMethodSubtype: InputMethodSubtype) => void): void
```

订阅设置输入法子类型事件。使用callback异步回调。 **使用场景：** 输入法应用需要在子类型（如语言、输入模式）发生变化时，切换到对应的键盘布局或输入逻辑。 **使用后效果：** 当输入法子类型变化时触发回调，返回新的输入法子类型信息。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-InputMethodAbility-on(type: 'setSubtype', callback: (inputMethodSubtype: InputMethodSubtype) => void): void--><!--Device-InputMethodAbility-on(type: 'setSubtype', callback: (inputMethodSubtype: InputMethodSubtype) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'setSubtype' | 是 | 设置监听类型，固定取值为'setSubtype'。 |
| callback | (inputMethodSubtype: InputMethodSubtype) =&gt; void | 是 | 回调函数，返回设置的输入法子类型（InputMethodSubtype，输入法子类型）。 |

## 示例

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';

inputMethodEngine.getInputMethodAbility().on('setSubtype', (inputMethodSubtype: InputMethodSubtype) => {
  console.info('InputMethodAbility setSubtype.');
});
```

