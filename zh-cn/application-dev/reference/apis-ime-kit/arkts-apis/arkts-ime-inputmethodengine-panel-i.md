# Panel

Panel是输入法面板对象，提供面板页面加载、显示/隐藏、尺寸调整、位置移动、模式切换等功能。Panel实例通过InputMethodAbility的 [createPanel]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 接口获取，使用完毕后需调用 [destroyPanel]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 销毁以释放资源。createPanel与destroyPanel必须配对调用。 **核心功能概述：** - **页面加载**：通过 [setUiContent]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_为面板加载键盘页面内容， 支持加载普通页面和与LocalStorage关联的页面。 - **显示与隐藏**：通过[show]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_显示面板，通过 [hide]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_隐藏面板。面板的显示/隐藏也可通过订阅on('show')/on('hide')事件 监听状态变化。 - **尺寸与位置调整**：通过 [resize]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_调整面板尺寸，通过 [moveTo]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_移动面板位置，通过 [startMoving]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_拖拽移动面板，通过 [adjustPanelRect]\_\_\_JSDOC\_LINK\_DESC\_USD\_8\_\_\_/ [updatePanelRect]\_\_\_JSDOC\_LINK\_DESC\_USD\_9\_\_\_/ [updateRegion]\_\_\_JSDOC\_LINK\_DESC\_USD\_10\_\_\_调整面板区域。 - **模式设置**：通过[changeFlag]\_\_\_JSDOC\_LINK\_DESC\_USD\_11\_\_\_切换面板固定态/浮动态，通过 [setPrivacyMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_12\_\_\_设置隐私模式，通过 [setImmersiveMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_13\_\_\_/ [getImmersiveMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_14\_\_\_设置/获取沉浸模式。 - **事件监听**：通过on('show')/on('hide')/on('sizeChange')监听面板状态变化事件。 **面板生命周期：** 1. 在InputMethodAbility的[createPanel]\_\_\_JSDOC\_LINK\_DESC\_USD\_15\_\_\_中创建Panel实例并指定面板类型和标志位。 2. 调用[setUiContent]\_\_\_JSDOC\_LINK\_DESC\_USD\_16\_\_\_加载键盘页面内容。 3. 调用[show]\_\_\_JSDOC\_LINK\_DESC\_USD\_17\_\_\_显示面板，用户可交互。 4. 根据需要调用resize、moveTo、changeFlag等接口动态调整面板。 5. 使用完毕后调用[destroyPanel]\_\_\_JSDOC\_LINK\_DESC\_USD\_18\_\_\_销毁面板，释放资源。 下列API均需使用 [createPanel]\_\_\_JSDOC\_LINK\_DESC\_USD\_19\_\_\_ 获取到Panel实例后，通过实例调用。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-inputMethodEngine-interface Panel--><!--Device-inputMethodEngine-interface Panel-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## adjustPanelRect

```TypeScript
adjustPanelRect(flag: PanelFlag, rect: PanelRect): void
```

预设置输入法应用横竖屏大小。接口调用完毕表示adjust请求已提交到输入法框架，不表示执行完毕。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Panel-adjustPanelRect(flag: PanelFlag, rect: PanelRect): void--><!--Device-Panel-adjustPanelRect(flag: PanelFlag, rect: PanelRect): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flag | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板状态类型。类型为FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FIXED或FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FLOATING。 |
| rect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板横屏状态及竖屏状态的横坐标，纵坐标，宽度以及高度。固定态：高度不能超过屏幕高度的70%，宽度不能超过屏幕宽度；悬浮态：高度不能超过屏幕高度，宽度不能超过屏幕宽度。超出范围时返回错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';

// 定义横屏状态下面板的矩形区域
let landscapeRect: window.Rect = {
  left: 100,
  top: 100,
  width: 400,
  height: 400
};

// 定义竖屏状态下面板的矩形区域
let portraitRect: window.Rect = {
  left: 200,
  top: 200,
  width: 300,
  height: 300
};

// 设置面板状态为固定态
let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
// 配置面板的横竖屏矩形区域
let panelRect: inputMethodEngine.PanelRect = {
  landscapeRect: landscapeRect,
  portraitRect: portraitRect
};
// 预设置输入法应用横竖屏大小
panel.adjustPanelRect(panelFlag, panelRect);
```

## adjustPanelRect

```TypeScript
adjustPanelRect(flag: PanelFlag, rect: EnhancedPanelRect): void
```

预设置输入法应用横竖屏大小、位置、自定义避让区域以及热区。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-Panel-adjustPanelRect(flag: PanelFlag, rect: EnhancedPanelRect): void--><!--Device-Panel-adjustPanelRect(flag: PanelFlag, rect: EnhancedPanelRect): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flag | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板状态类型。类型为FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FIXED或FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FLOATING。 |
| rect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板横屏状态及竖屏状态的位置、大小、避让区域以及热区。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-无效的面板类型或面板状态) | invalid panel type or panel flag. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';

let landscapeRect1: window.Rect = {
  left: 300,
  top: 650,
  width: 2000,
  height: 500
};
let landscapeInputRegion: Array<window.Rect> = [landscapeRect1];

let portraitRect1: window.Rect = {
  left: 0,
  top: 1800,
  width: 1200,
  height: 800
}
let portraitInputRegion: Array<window.Rect> = [portraitRect1];
// 目标面板状态类型。
let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
// 目标面板横屏状态及竖屏状态的位置、大小、避让区域以及热区。
let panelRect: inputMethodEngine.EnhancedPanelRect = {
  landscapeAvoidY: 650,
  landscapeInputRegion: landscapeInputRegion,
  portraitAvoidY: 1800,
  portraitInputRegion: portraitInputRegion,
  fullScreenMode: true
};
panel.adjustPanelRect(panelFlag, panelRect);
```

## changeFlag

```TypeScript
changeFlag(flag: PanelFlag): void
```

将输入法应用的面板状态改变为其他[PanelFlag]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_形态，仅对 [SOFT\_KEYBOARD]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_生效。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-changeFlag(flag: PanelFlag): void--><!--Device-Panel-changeFlag(flag: PanelFlag): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flag | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板状态类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```TypeScript
let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
panel.changeFlag(panelFlag);
```

## getDisplayId

ArkTS-Dyn:
```TypeScript
getDisplayId(): Promise<number>
```

ArkTS-Sta:
```TypeScript
getDisplayId(): Promise<long>
```

获取当前窗口的所在id，使用Promise异步回调。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-Panel-getDisplayId(): Promise<long>--><!--Device-Panel-getDisplayId(): Promise<long>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;long&gt; | Promise对象。返回窗口的displayId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.getDisplayId().then((result: number) => {
  console.info('get displayId:' + result);
}).catch((err: BusinessError) => {
  console.error(`Failed to get displayId. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.getDisplayId().then((result: long) => {
  console.info('get displayId:' + result);
}).catch((err: BusinessError) => {
  console.error(`Failed to get displayId. Code is ${err.code}, message is ${err.message}`);
});
```

## getImmersiveMode

```TypeScript
getImmersiveMode(): ImmersiveMode
```

获取输入法应用的沉浸模式。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-Panel-getImmersiveMode(): ImmersiveMode--><!--Device-Panel-getImmersiveMode(): ImmersiveMode-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 沉浸模式。 |

**示例：**

```TypeScript
let mode: inputMethodEngine.ImmersiveMode = panel.getImmersiveMode();
```

## getSystemPanelCurrentInsets

```TypeScript
getSystemPanelCurrentInsets(displayId: number): Promise<SystemPanelInsets>
```

获取指定屏幕当前状态（例如：折叠或展开）下，当前输入法键盘状态（例如：悬浮或固定）下输入法软键盘相对系统面板的偏移区域。使用Promise异步回调。

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

<!--Device-Panel-getSystemPanelCurrentInsets(displayId: number): Promise<SystemPanelInsets>--><!--Device-Panel-getSystemPanelCurrentInsets(displayId: number): Promise<SystemPanelInsets>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 输入法键盘所在屏幕的displayId，可通过[getDisplayId]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获取 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SystemPanelInsets&gt; | Promise对象。输入法键盘与系统面板的偏移区域。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-无效的面板类型或面板状态) | invalid panel type or panel flag. Possible causes:1. Current panel's type is not SOFT\_\_\_ESCAPED\_UNDERSCORE\_\_\_KEYBOARD. 2. Panel's flag is not FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FIXED or FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FLOATING. |
| [12800022](../errorcode-inputmethod-framework.md#12800022-无效的displayid) | invalid displayId. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let inputMethodAbility: inputMethodEngine.InputMethodAbility = inputMethodEngine.getInputMethodAbility();
let panelConfig: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}
// 以下逻辑需要在输入法InputMethodExtensionAbility中执行，this.context是InputMethodExtensionAbility的上下文
inputMethodAbility.createPanel(this.context, panelConfig).then( (panel: inputMethodEngine.Panel) =>{
  panel.getDisplayId().then((displayId: number) => {
    panel.getSystemPanelCurrentInsets(displayId).then((insets: inputMethodEngine.SystemPanelInsets) => {
      console.info(`getSystemPanelCurrentInsets success, insets is { left: ${insets.left}, right: ${insets.right}, bottom: ${insets.bottom} }`);
    }).catch((error: BusinessError) => {
      console.error(`getSystemPanelCurrentInsets failed, code: ${error.code}, message: ${error.message}`);
    })
  });
})
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let inputMethodAbility: inputMethodEngine.InputMethodAbility = inputMethodEngine.getInputMethodAbility();
let panelConfig: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}
// 以下逻辑需要在输入法InputMethodExtensionAbility中执行，this.context是InputMethodExtensionAbility的上下文
inputMethodAbility.createPanel(this.context, panelConfig).then( (panel: inputMethodEngine.Panel) =>{
  panel.getDisplayId().then((displayId: long) => {
    panel.getSystemPanelCurrentInsets(displayId).then((insets: inputMethodEngine.SystemPanelInsets | null) => {
      if (insets) {
        console.info(`getSystemPanelCurrentInsets success, insets is { left: ${insets.left}, right: ${insets.right}, bottom: ${insets.bottom} }`);
      }
    }).catch((error: BusinessError) => {
      console.error(`getSystemPanelCurrentInsets failed, code: ${error.code}, message: ${error.message}`);
    })
  });
})
```

## getSystemPanelCurrentInsets

```TypeScript
getSystemPanelCurrentInsets(displayId: long): Promise<SystemPanelInsets | null>
```

获取指定屏幕当前状态（例如：折叠或展开）下，当前输入法键盘状态（例如：悬浮或固定）下输入法软键盘相对系统面板的偏移区域。使用Promise异步回调。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_仅支持悬浮或固定键盘.\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_获取指定屏幕当前状态（例如：折叠或展开）下，当前输入法键盘状态（例如：悬浮或固定）下输入法软键盘相对系统面板的偏移区域。\_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_当屏幕状态发生变化，需要重新获取偏移区域。\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Panel-getSystemPanelCurrentInsets(displayId: long): Promise<SystemPanelInsets | null>--><!--Device-Panel-getSystemPanelCurrentInsets(displayId: long): Promise<SystemPanelInsets | null>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | long | 是 | specify which display's system panel insets. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SystemPanelInsets \| null&gt; | the promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-无效的面板类型或面板状态) | invalid panel type or panel flag. Possible causes:1. Current panel's type is not SOFT\_\_\_ESCAPED\_UNDERSCORE\_\_\_KEYBOARD. 2. Panel's flag is not FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FIXED or FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FLOATING. |
| [12800022](../errorcode-inputmethod-framework.md#12800022-无效的displayid) | invalid displayId. |

## hide

```TypeScript
hide(callback: AsyncCallback<void>): void
```

隐藏当前输入法面板，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-hide(callback: AsyncCallback<void>): void--><!--Device-Panel-hide(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当面板隐藏成功，err为undefined，否则err为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.hide((err: BusinessError) => {
  if (err) {
    console.error(`Failed to hide panel. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding the panel.');
});
```

## hide

```TypeScript
hide(): Promise<void>
```

隐藏当前输入法面板，使用promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-hide(): Promise<void>--><!--Device-Panel-hide(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.hide().then(() => {
  console.info('Succeeded in hiding the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide panel. Code is ${err.code}, message is ${err.message}`);
});
```

## moveTo

ArkTS-Dyn:
```TypeScript
moveTo(x: number, y: number, callback: AsyncCallback<void>): void
```

ArkTS-Sta:
```TypeScript
moveTo(x: int, y: int, callback: AsyncCallback<void>): void
```

移动面板位置，使用callback异步回调。[面板状态]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_为固定态时，不产生实际移动效果。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-moveTo(x: int, y: int, callback: AsyncCallback<void>): void--><!--Device-Panel-moveTo(x: int, y: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 横轴方向移动的值，单位为px。该参数应为整数。值大于0表示右移，小于0表示左移。超出屏幕范围时返回错误码401。 |
| y | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 纵轴方向移动的值，单位为px。该参数应为整数。值大于0表示下移，小于0表示上移。超出屏幕范围时返回错误码401。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当面板位置移动成功，err为undefined，否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 移动输入法面板位置
panel.moveTo(300, 300, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to move panel. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in moving the panel.');
});
```

## moveTo

ArkTS-Dyn:
```TypeScript
moveTo(x: number, y: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
moveTo(x: int, y: int): Promise<void>
```

移动面板位置，使用promise异步回调。[面板状态]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_为固定态时，不产生实际移动效果。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-moveTo(x: int, y: int): Promise<void>--><!--Device-Panel-moveTo(x: int, y: int): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 横轴方向移动的值，值大于0表示右移，单位为px。该参数应为整数。 |
| y | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 纵轴方向移动的值，值大于0表示下移，单位为px。该参数应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 移动输入法面板位置
panel.moveTo(300, 300).then(() => {
  console.info('Succeeded in moving the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to move panel. Code is ${err.code}, message is ${err.message}`);
});
```

## off('show')

```TypeScript
off(type: 'show', callback?: () => void): void
```

取消监听当前面板的显示状态，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-Panel-off(type: 'show', callback?: () => void): void--><!--Device-Panel-off(type: 'show', callback?: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'show' | 是 | 取消监听当前面板的状态类型，固定取值为'show'。 |
| callback | () =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```TypeScript
panel.off('show');
```

## off('hide')

```TypeScript
off(type: 'hide', callback?: () => void): void
```

取消监听当前面板的隐藏状态，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-Panel-off(type: 'hide', callback?: () => void): void--><!--Device-Panel-off(type: 'hide', callback?: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hide' | 是 | 要取消监听的当前面板状态类型，固定取值为'hide'。 |
| callback | () =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```TypeScript
panel.off('hide');
```

## off('sizeChange')

```TypeScript
off(type: 'sizeChange', callback?: SizeChangeCallback): void
```

取消监听当前面板大小变化，使用callback异步回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-Panel-off(type: 'sizeChange', callback?: SizeChangeCallback): void--><!--Device-Panel-off(type: 'sizeChange', callback?: SizeChangeCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sizeChange' | 是 | 监听当前面板的大小是否产生变化，固定取值为'sizeChange'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数。返回当前软键盘面板的大小，包含宽度和高度值。参数不填写时，取消订阅type对应的所有回调事件。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 15 |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';

panel.off('sizeChange', (windowSize: window.Size) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
```

## offHide

```TypeScript
offHide(callback?: Callback<void>): void
```

取消监听当前面板隐藏状态，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Panel-offHide(callback?: Callback<void>): void--><!--Device-Panel-offHide(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
panel.offHide();
```

## offShow

```TypeScript
offShow(callback?: Callback<void>): void
```

取消监听当前输入法面板的隐藏状态，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Panel-offShow(callback?: Callback<void>): void--><!--Device-Panel-offShow(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
panel.offShow();
```

## offSizeChange

```TypeScript
offSizeChange(callback?: SizeChangeCallback): void
```

取消监听当前面板大小变化，使用callback异步回调。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_此接口仅支持固定或悬浮态的软键盘类型Panel。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Panel-offSizeChange(callback?: SizeChangeCallback): void--><!--Device-Panel-offSizeChange(callback?: SizeChangeCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数。返回当前软键盘面板的大小，包含宽度和高度值。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';

panel.offSizeChange((windowSize: window.Size) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
```

## on('show')

```TypeScript
on(type: 'show', callback: () => void): void
```

监听当前面板显示状态，使用 callback 异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-Panel-on(type: 'show', callback: () => void): void--><!--Device-Panel-on(type: 'show', callback: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'show' | 是 | 监听当前面板的状态类型，固定取值为'show'。 |
| callback | () =&gt; void | 是 | 回调函数。 |

**示例：**

```TypeScript
panel.on('show', () => {
  console.info('Panel is showing.');
});
```

## on('hide')

```TypeScript
on(type: 'hide', callback: () => void): void
```

监听当前面板隐藏状态，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-Panel-on(type: 'hide', callback: () => void): void--><!--Device-Panel-on(type: 'hide', callback: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hide' | 是 | 监听当前面板的状态类型，固定取值为'hide'。 |
| callback | () =&gt; void | 是 | 回调函数。 |

**示例：**

```TypeScript
panel.on('hide', () => {
  console.info('Panel is hiding.');
});
```

## on('sizeChange')

```TypeScript
on(type: 'sizeChange', callback: SizeChangeCallback): void
```

监听当前面板大小变化，使用callback异步回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-Panel-on(type: 'sizeChange', callback: SizeChangeCallback): void--><!--Device-Panel-on(type: 'sizeChange', callback: SizeChangeCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sizeChange' | 是 | 监听当前面板的大小是否产生变化，固定值为'sizeChange'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调函数。返回当前软键盘面板的大小，包含宽度和高度值。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 15 |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';

// 监听面板大小变化事件
panel.on('sizeChange', (windowSize: window.Size) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});

// 监听面板大小变化事件（带键盘区域参数）
panel.on('sizeChange', (windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, windowSize: ${windowSize.width}, ${windowSize.height}, ` +
    `keyboardArea: ${keyboardArea.top}, ${keyboardArea.bottom}, ${keyboardArea.left}, ${keyboardArea.right}`);
});
```

## onHide

```TypeScript
onHide(callback: Callback<void>): void
```

监听当前面板隐藏状态，使用callback异步回调。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_“hide”事件在面板隐藏时触发。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Panel-onHide(callback: Callback<void>): void--><!--Device-Panel-onHide(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
panel!.onHide(() => {
  console.info('Panel is hide.');
});
```

## onShow

```TypeScript
onShow(callback: Callback<void>): void
```

监听当前面板显示状态，使用callback异步回调。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_“show”事件在面板显示时触发。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Panel-onShow(callback: Callback<void>): void--><!--Device-Panel-onShow(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
panel.onShow(() => {
  console.info('Panel is showing.');
});
```

## onSizeChange

```TypeScript
onSizeChange(callback: SizeChangeCallback): void
```

监听当前面板大小变化，使用callback异步回调。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_此接口仅支持固定或悬浮态的软键盘类型Panel。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Panel-onSizeChange(callback: SizeChangeCallback): void--><!--Device-Panel-onSizeChange(callback: SizeChangeCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调函数。返回当前软键盘面板的大小，包含宽度和高度值。 |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';

panel.onSizeChange((windowSize: window.Size) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
panel.onSizeChange((windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, windowSize: ${windowSize)}, keyboardArea: ${keyboardArea}`);
});
```

## resize

ArkTS-Dyn:
```TypeScript
resize(width: number, height: number, callback: AsyncCallback<void>): void
```

ArkTS-Sta:
```TypeScript
resize(width: long, height: long, callback: AsyncCallback<void>): void
```

改变当前输入法面板的大小，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-resize(width: long, height: long, callback: AsyncCallback<void>): void--><!--Device-Panel-resize(width: long, height: long, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 目标面板的宽度，单位为vp。该参数应为大于或等于0的整数，不超出屏幕宽度。超出范围时返回错误码401。 |
| height | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 目标面板的高度，单位为vp。该参数应为大于或等于0的整数，不高于屏幕高度的0.7倍。超出范围时返回错误码401。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当面板大小改变成功，err为undefined，否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 改变输入法面板大小
panel.resize(500, 1000, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to resize panel. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in changing the panel size.');
});
```

## resize

ArkTS-Dyn:
```TypeScript
resize(width: number, height: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
resize(width: long, height: long): Promise<void>
```

改变当前输入法面板的大小，使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-resize(width: long, height: long): Promise<void>--><!--Device-Panel-resize(width: long, height: long): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 目标面板的宽度，单位为vp。该参数应为大于或等于0的整数，不超出屏幕宽度。超出范围时返回错误码401。 |
| height | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 目标面板的高度，单位为vp。该参数应为大于或等于0的整数，不高于屏幕高度的0.7倍。超出范围时返回错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 改变输入法面板大小
panel.resize(500, 1000).then(() => {
  console.info('Succeeded in changing the panel size.');
}).catch((err: BusinessError) => {
  console.error(`Failed to resize panel. Code is ${err.code}, message is ${err.message}`);
});
```

## setImmersiveEffect

```TypeScript
setImmersiveEffect(effect: ImmersiveEffect): void
```

设置输入法应用的沉浸效果。 - 只有在[启用沉浸式模式]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_时，才能使用渐变模式和流光模式。 - 只有在启用渐变模式时，才能使用流光模式。 - 未启用渐变模式时，渐变高度必须为0px。 - 只有系统应用才能设置流光模式。 - 必须先调用以下任一接口，才能调用当前接口： - [adjustPanelRect]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_(支持API version 12) - [adjustPanelRect]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_(支持 API version 15) - [resize]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_(支持API version 10)

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-Panel-setImmersiveEffect(effect: ImmersiveEffect): void--><!--Device-Panel-setImmersiveEffect(effect: ImmersiveEffect): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 沉浸效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1. input method panel not created. 2. the input method application does not subscribe to related events. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |
| [12800020](../errorcode-inputmethod-framework.md#12800020-沉浸效果参数配置错误) | invalid immersive effect.1. The gradient mode and the fluid light mode can only be used when the immersive mode is enabled.2. The fluid light mode can only be used when the gradient mode is enabled.3. When the gradient mode is not enabled, the gradient height can only be 0. |
| [12800021](../errorcode-inputmethod-framework.md#12800021-调用顺序错误) | this operation is allowed only after adjustPanelRect or resize is called. |

**示例：**

```TypeScript
let effect: inputMethodEngine.ImmersiveEffect = {
  gradientHeight: 100,
  gradientMode: inputMethodEngine.GradientMode.LINEAR_GRADIENT
}
panel.setImmersiveEffect(effect);
```

## setImmersiveMode

```TypeScript
setImmersiveMode(mode: ImmersiveMode): void
```

设置输入法应用的沉浸模式。只能设置为不使用沉浸模式(NONE\_IMMERSIVE)、浅色沉浸模式(LIGHT\_IMMERSIVE)或深色沉浸模式(DARK\_IMMERSIVE)。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-Panel-setImmersiveMode(mode: ImmersiveMode): void--><!--Device-Panel-setImmersiveMode(mode: ImmersiveMode): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 沉浸模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types; 2.Parameter verification failed. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |

**示例：**

```TypeScript
panel.setImmersiveMode(inputMethodEngine.ImmersiveMode.LIGHT_IMMERSIVE);
```

## setKeepScreenOn

```TypeScript
setKeepScreenOn(isKeepScreenOn: boolean): Promise<void>
```

设置屏幕常亮。使用Promise异步回调。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-Panel-setKeepScreenOn(isKeepScreenOn: boolean): Promise<void>--><!--Device-Panel-setKeepScreenOn(isKeepScreenOn: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isKeepScreenOn | boolean | 是 | 是否设置屏幕常亮。true表示打开屏幕常亮，false表示关闭屏幕常亮。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.setKeepScreenOn(true).then(() => {
  console.info(`setKeepScreenOn success.`);
}).catch((error: BusinessError) => {
  console.error(`setKeepScreenOn failed, code: ${error.code}, message: ${error.message}`);
})
```

## setPrivacyMode

```TypeScript
setPrivacyMode(isPrivacyMode: boolean): void
```

将输入法应用的面板设置为隐私模式，隐私模式不可被录屏、截屏。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.PRIVACY_WINDOW

<!--Device-Panel-setPrivacyMode(isPrivacyMode: boolean): void--><!--Device-Panel-setPrivacyMode(isPrivacyMode: boolean): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isPrivacyMode | boolean | 是 | 是否设置隐私模式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- 值为true，表示将设置为隐私模式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- 值为false，表示将设置为非隐私模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
let isPrivacyMode: boolean = true;
panel.setPrivacyMode(isPrivacyMode);
```

## setSystemPanelButtonColor

```TypeScript
setSystemPanelButtonColor(fillColor: string | undefined, backgroundColor: string | undefined): Promise<void>
```

设置当前面板功能键颜色和功能键的背景颜色。使用Promise异步回调。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-Panel-setSystemPanelButtonColor(fillColor: string | undefined, backgroundColor: string | undefined): Promise<void>--><!--Device-Panel-setSystemPanelButtonColor(fillColor: string | undefined, backgroundColor: string | undefined): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillColor | string \| undefined | 是 | 功能键的颜色，取值范围为[#01000000, #FFFFFFFF] 或 [#000000, #FFFFFF]，不支持具有完全透明Alpha通道（#00xxxxxx）的值。 |
| backgroundColor | string \| undefined | 是 | 功能键的背景颜色，取值范围为[#01000000, #FFFFFFFF] 或 [#000000, #FFFFFF]，不支持具有完全透明Alpha通道（#00xxxxxx）的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 确保有panel实例，可以使用inputMethodEngine.getInputMethodAbility().createPanel(...)创建panel实例
try {
  let fillColor = "#FFFF00";
  let backgroundColor = "#0000FF";
  panel.setSystemPanelButtonColor(fillColor, backgroundColor).then(() => {
    console.info(`setSystemPanelButtonColor success.`);
  }).catch((error: BusinessError) => {
    console.error(`setSystemPanelButtonColor failed, code: ${error.code}, message: ${error.message}`);
  })
} catch (err) {
  let error = err as BusinessError;
  console.error(`setSystemPanelButtonColor failed, code: ${error.code}, message: ${error.message}`);
}
```

## setUiContent

```TypeScript
setUiContent(path: string, callback: AsyncCallback<void>): void
```

为当前的输入法面板加载具体页面内容，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-setUiContent(path: string, callback: AsyncCallback<void>): void--><!--Device-Panel-setUiContent(path: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 具体页面的路径。路径长度建议不超过1024字符。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当面板页面内容加载成功，err为undefined，否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 设置输入法面板内容
// panel对象通过createPanel接口获取，详见createPanel示例
panel.setUiContent('pages/page2/page2', (err: BusinessError) => {
  if (err) {
    console.error(`Failed to setUiContent. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the content.');
});
```

## setUiContent

```TypeScript
setUiContent(path: string): Promise<void>
```

为当前的输入法面板加载具体页面内容，使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-setUiContent(path: string): Promise<void>--><!--Device-Panel-setUiContent(path: string): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 具体页面的路径。路径长度建议不超过1024字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.setUiContent('pages/page2/page2').then(() => {
  console.info('Succeeded in setting the content.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setUiContent. Code is ${err.code}, message is ${err.message}`);
});
```

## setUiContent

```TypeScript
setUiContent(path: string, storage: LocalStorage, callback: AsyncCallback<void>): void
```

为当前的输入法面板加载与LocalStorage相关联的具体页面内容，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-setUiContent(path: string, storage: LocalStorage, callback: AsyncCallback<void>): void--><!--Device-Panel-setUiContent(path: string, storage: LocalStorage, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | LocalStorage相关联的具体页面的路径。路径长度建议不超过1024字符。 |
| storage | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 存储单元，为应用程序范围内的可变和不可变状态属性提供存储。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当面板页面内容加载成功，err为undefined，否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 创建并初始化LocalStorage对象
let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('storageSimpleProp', 121);
panel.setUiContent('pages/page2/page2', storage, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to setUiContent. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the content.');
});
```

## setUiContent

```TypeScript
setUiContent(path: string, storage: LocalStorage): Promise<void>
```

为当前面板加载与LocalStorage相关联的具体页面内容，使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-setUiContent(path: string, storage: LocalStorage): Promise<void>--><!--Device-Panel-setUiContent(path: string, storage: LocalStorage): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 具体页面的路径。路径长度建议不超过1024字符。 |
| storage | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 存储单元，为应用程序范围内的可变状态属性和非可变状态属性提供存储。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 创建并初始化LocalStorage对象
let storage: LocalStorage = new LocalStorage();
storage.setOrCreate('storageSimpleProp', 121);
panel.setUiContent('pages/page2/page2', storage).then(() => {
  console.info('Succeeded in setting the content.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setUiContent. Code is ${err.code}, message is ${err.message}`);
});
```

## show

```TypeScript
show(callback: AsyncCallback<void>): void
```

显示当前输入法面板，使用callback异步回调。输入法应用与编辑框绑定成功后可正常调用。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-show(callback: AsyncCallback<void>): void--><!--Device-Panel-show(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当面板显示成功，err为undefined，否则err为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.show((err: BusinessError) => {
  if (err) {
    console.error(`Failed to show panel. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in showing the panel.');
});
```

## show

```TypeScript
show(): Promise<void>
```

显示当前输入法面板，使用promise异步回调。输入法应用与编辑框绑定成功后可正常调用。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-Panel-show(): Promise<void>--><!--Device-Panel-show(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

panel.show().then(() => {
  console.info('Succeeded in showing the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show panel. Code is ${err.code}, message is ${err.message}`);
});
```

## startMoving

```TypeScript
startMoving(): void
```

发送移动命令给窗口，不产生实际移动效果（仅在鼠标点击作用才可以移动）。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-Panel-startMoving(): void--><!--Device-Panel-startMoving(): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-无效的面板类型或面板状态) | invalid panel type or panel flag. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 18+ |

**示例：**

```TypeScript
panel.startMoving();
```

## updatePanelRect

```TypeScript
updatePanelRect(flag: PanelFlag, rect: PanelRect): Promise<void>
```

预设置输入法应用横竖屏大小。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-updatePanelRect(flag: PanelFlag, rect: PanelRect): Promise<void>--><!--Device-Panel-updatePanelRect(flag: PanelFlag, rect: PanelRect): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flag | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板状态类型。类型为FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FIXED或FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FLOATING。 |
| rect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板横屏状态及竖屏状态的横坐标，纵坐标，宽度以及高度。固定态：高度不能超过屏幕高度的70%，宽度不能超过屏幕宽度；悬浮态：高度不能超过屏幕高度，宽度不能超过屏幕宽度。超出范围时返回错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';

let landscapeRect: window.Rect = {
  left: 100,
  top: 100,
  width: 400,
  height: 400
};

let portraitRect: window.Rect = {
  left: 200,
  top: 200,
  width: 300,
  height: 300
};

// 目标面板状态类型
let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
// 目标面板横屏状态及竖屏状态的横坐标，纵坐标，宽度以及高度
let panelRect: inputMethodEngine.PanelRect = {
  landscapeRect: landscapeRect,
  portraitRect: portraitRect
};
panel.updatePanelRect(panelFlag, panelRect);
```

## updatePanelRect

```TypeScript
updatePanelRect(flag: PanelFlag, rect: EnhancedPanelRect): Promise<void>
```

预设置输入法应用横竖屏大小、位置、自定义避让区域以及热区。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-updatePanelRect(flag: PanelFlag, rect: EnhancedPanelRect): Promise<void>--><!--Device-Panel-updatePanelRect(flag: PanelFlag, rect: EnhancedPanelRect): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flag | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板状态类型。类型为FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FIXED或FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FLOATING。 |
| rect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板横屏状态及竖屏状态的位置、大小、避让区域以及热区。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-无效的面板类型或面板状态) | invalid panel type or panel flag. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';

let landscapeRect1: window.Rect = {
  left: 300,
  top: 650,
  width: 2000,
  height: 500
};
let landscapeInputRegion: Array<window.Rect> = [landscapeRect1];

let portraitRect1: window.Rect = {
  left: 0,
  top: 1800,
  width: 1200,
  height: 800
}
let portraitInputRegion: Array<window.Rect> = [portraitRect1];
// 目标面板状态类型。
let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
// 目标面板横屏状态及竖屏状态的位置、大小、避让区域以及热区。
let panelRect: inputMethodEngine.EnhancedPanelRect = {
  landscapeAvoidY: 650,
  landscapeInputRegion: landscapeInputRegion,
  portraitAvoidY: 1800,
  portraitInputRegion: portraitInputRegion,
  fullScreenMode: true
};
panel.updatePanelRect(panelFlag, panelRect);
```

## updatePanelRectSync

```TypeScript
updatePanelRectSync(flag: PanelFlag, rect: PanelRect): void
```

预设置输入法应用横竖屏大小。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-updatePanelRectSync(flag: PanelFlag, rect: PanelRect): void--><!--Device-Panel-updatePanelRectSync(flag: PanelFlag, rect: PanelRect): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flag | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板状态类型。类型为FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FIXED或FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FLOATING。 |
| rect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板横屏状态及竖屏状态的横坐标，纵坐标，宽度以及高度。固定态：高度不能超过屏幕高度的70%，宽度不能超过屏幕宽度；悬浮态：高度不能超过屏幕高度，宽度不能超过屏幕宽度。超出范围时返回错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';

let landscapeRect: window.Rect = {
  left: 100,
  top: 100,
  width: 400,
  height: 400
};

let portraitRect: window.Rect = {
  left: 200,
  top: 200,
  width: 300,
  height: 300
};

// 目标面板状态类型
let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
// 目标面板横屏状态及竖屏状态的横坐标，纵坐标，宽度以及高度
let panelRect: inputMethodEngine.PanelRect = {
  landscapeRect: landscapeRect,
  portraitRect: portraitRect
};
panel.updatePanelRectSync(panelFlag, panelRect);
```

## updatePanelRectSync

```TypeScript
updatePanelRectSync(flag: PanelFlag, rect: EnhancedPanelRect): void
```

预设置输入法应用横竖屏大小、位置、自定义避让区域以及热区。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-updatePanelRectSync(flag: PanelFlag, rect: EnhancedPanelRect): void--><!--Device-Panel-updatePanelRectSync(flag: PanelFlag, rect: EnhancedPanelRect): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flag | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板状态类型。类型为FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FIXED或FLG\_\_\_ESCAPED\_UNDERSCORE\_\_\_FLOATING。 |
| rect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标面板横屏状态及竖屏状态的位置、大小、避让区域以及热区。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-无效的面板类型或面板状态) | invalid panel type or panel flag. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';

let landscapeRect1: window.Rect = {
  left: 300,
  top: 650,
  width: 2000,
  height: 500
};
let landscapeInputRegion: Array<window.Rect> = [landscapeRect1];

let portraitRect1: window.Rect = {
  left: 0,
  top: 1800,
  width: 1200,
  height: 800
}
let portraitInputRegion: Array<window.Rect> = [portraitRect1];
// 目标面板状态类型。
let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
// 目标面板横屏状态及竖屏状态的位置、大小、避让区域以及热区。
let panelRect: inputMethodEngine.EnhancedPanelRect = {
  landscapeAvoidY: 650,
  landscapeInputRegion: landscapeInputRegion,
  portraitAvoidY: 1800,
  portraitInputRegion: portraitInputRegion,
  fullScreenMode: true
};
panel.updatePanelRectSync(panelFlag, panelRect);
```

## updateRegion

```TypeScript
updateRegion(inputRegion: Array<window.Rect>): void
```

更新当前状态下输入法面板内的热区。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-Panel-updateRegion(inputRegion: Array<window.Rect>): void--><!--Device-Panel-updateRegion(inputRegion: Array<window.Rect>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputRegion | Array&lt;window.Rect&gt; | 是 | 面板内接收输入事件的区域。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- 数组大小限制为[1, 4]。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- 传入的热区位置是相对于输入法面板窗口左顶点的位置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |
| [12800017](../errorcode-inputmethod-framework.md#12800017-无效的面板类型或面板状态) | invalid panel type or panel flag. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let inputRegion: Array<window.Rect> = [{
  left: 300,
  top: 650,
  width: 2000,
  height: 500
}];
panel.updateRegion(inputRegion);
```

