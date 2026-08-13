# Panel

Panel是输入法面板对象，提供面板页面加载、显示/隐藏、尺寸调整、位置移动、模式切换等功能。Panel实例通过InputMethodAbility的 [createPanel](arkts-ime-inputmethodengine-inputmethodability-i.md#createPanel) 接口获取，使用完毕后需调用 [destroyPanel](arkts-ime-inputmethodengine-inputmethodability-i.md#destroyPanel) 销毁以释放资源。createPanel与destroyPanel必须配对调用。 **核心功能概述：** - **页面加载**：通过 [setUiContent](arkts-ime-inputmethodengine-panel-i.md#setUiContent)为面板加载键盘页面内容， 支持加载普通页面和与LocalStorage关联的页面。 - **显示与隐藏**：通过[show](arkts-ime-inputmethodengine-panel-i.md#show)显示面板，通过 [hide](arkts-ime-inputmethodengine-panel-i.md#hide)隐藏面板。面板的显示/隐藏也可通过订阅on('show')/on('hide')事件 监听状态变化。 - **尺寸与位置调整**：通过 [resize](arkts-ime-inputmethodengine-panel-i.md#resize)调整面板尺寸，通过 [moveTo](arkts-ime-inputmethodengine-panel-i.md#moveTo)移动面板位置，通过 [startMoving](arkts-ime-inputmethodengine-panel-i.md#startMoving)拖拽移动面板，通过 [adjustPanelRect](arkts-ime-inputmethodengine-panel-i.md#adjustPanelRect)/ [updatePanelRect](arkts-ime-inputmethodengine-panel-i.md#updatePanelRect)/ [updateRegion](arkts-ime-inputmethodengine-panel-i.md#updateRegion)调整面板区域。 - **模式设置**：通过[changeFlag](arkts-ime-inputmethodengine-panel-i.md#changeFlag)切换面板固定态/浮动态，通过 [setPrivacyMode](arkts-ime-inputmethodengine-panel-i.md#setPrivacyMode)设置隐私模式，通过 [setImmersiveMode](arkts-ime-inputmethodengine-panel-i.md#setImmersiveMode)/ [getImmersiveMode](arkts-ime-inputmethodengine-panel-i.md#getImmersiveMode)设置/获取沉浸模式。 - **事件监听**：通过on('show')/on('hide')/on('sizeChange')监听面板状态变化事件。 **面板生命周期：** 1. 在InputMethodAbility的[createPanel](arkts-ime-inputmethodengine-inputmethodability-i.md#createPanel)中创建Panel实例并指定面板类型和标志位。 2. 调用[setUiContent](arkts-ime-inputmethodengine-panel-i.md#setUiContent)加载键盘页面内容。 3. 调用[show](arkts-ime-inputmethodengine-panel-i.md#show)显示面板，用户可交互。 4. 根据需要调用resize、moveTo、changeFlag等接口动态调整面板。 5. 使用完毕后调用[destroyPanel](arkts-ime-inputmethodengine-inputmethodability-i.md#destroyPanel)销毁面板，释放资源。 下列API均需使用 [createPanel](arkts-ime-inputmethodengine-inputmethodability-i.md#createPanel) 获取到Panel实例后，通过实例调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputMethodEngine-interface Panel--><!--Device-inputMethodEngine-interface Panel-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## offSizeUpdate

```TypeScript
offSizeUpdate(callback?: SizeUpdateCallback): void
```

取消订阅面板尺寸更新（sizeUpdate）事件，停止监听输入法面板尺寸的变更动作, 使用callback异步回调。 &lt;p&gt;此接口仅支持固定或悬浮态的软键盘类型Panel。&lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Panel-offSizeUpdate(callback?: SizeUpdateCallback): void--><!--Device-Panel-offSizeUpdate(callback?: SizeUpdateCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [SizeUpdateCallback](arkts-ime-inputmethodengine-sizeupdatecallback-t-sys.md) | 否 | 回调函数。 可选参数，需取消的目标回调函数：传入指定回调函数实例时，仅取消该回调的订阅；不传入时，取消所有sizeUpdate事件的订阅。 |

## 示例

```TypeScript
import { window } from '@kit.ArkUI';

panel.offSizeUpdate((windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
```

## off_sizeUpdate

```TypeScript
off(type: 'sizeUpdate', callback?: SizeUpdateCallback): void
```

通过Panel实例取消监听当前面板大小变化，停止callback异步回调。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

<!--Device-Panel-off(type: 'sizeUpdate', callback?: SizeUpdateCallback): void--><!--Device-Panel-off(type: 'sizeUpdate', callback?: SizeUpdateCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sizeUpdate' | 是 | 监听当前面板的大小是否产生变化，固定值为'sizeUpdate'。 |
| callback | [SizeUpdateCallback](arkts-ime-inputmethodengine-sizeupdatecallback-t-sys.md) | 否 | 回调函数。用于指定要取消监听的回调函数，如果不填则取消所有sizeUpdate监听。 |

## 示例

```TypeScript
import { window } from '@kit.ArkUI';

// 取消监听面板大小变化
panel.off('sizeUpdate', (windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  // 打印面板宽度、高度信息
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
```

## onSizeUpdate

```TypeScript
onSizeUpdate(callback: SizeUpdateCallback): void
```

订阅面板尺寸更新（sizeUpdate）事件，当输入法面板尺寸发生变更时触发该事件，并执行指定的回调函数, 使用callback异步回调。 &lt;p&gt;此接口仅支持固定或悬浮态的软键盘类型Panel。&lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Panel-onSizeUpdate(callback: SizeUpdateCallback): void--><!--Device-Panel-onSizeUpdate(callback: SizeUpdateCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [SizeUpdateCallback](arkts-ime-inputmethodengine-sizeupdatecallback-t-sys.md) | 是 | 面板尺寸更新时触发的回调函数，入参为面板尺寸信息对象。 |

## 示例

```TypeScript
import { window } from '@kit.ArkUI';

panel.onSizeUpdate((windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, windowSize: ${windowSize}, keyboardArea: ${keyboardArea}`);
});
```

## on_sizeUpdate

```TypeScript
on(type: 'sizeUpdate', callback: SizeUpdateCallback): void
```

通过Panel实例监听当前面板大小变化，在变化发生时通过callback异步回调。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

<!--Device-Panel-on(type: 'sizeUpdate', callback: SizeUpdateCallback): void--><!--Device-Panel-on(type: 'sizeUpdate', callback: SizeUpdateCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sizeUpdate' | 是 | 监听当前面板的大小是否产生变化，固定取值为'sizeUpdate'。 |
| callback | [SizeUpdateCallback](arkts-ime-inputmethodengine-sizeupdatecallback-t-sys.md) | 是 | 面板大小变化时的回调，参数包含当前软键盘面板的宽度和高度。 |

## 示例

```TypeScript
import { window } from '@kit.ArkUI';

// 监听面板大小变化
panel.on('sizeUpdate', (windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  // 打印面板大小和键盘区域信息
  console.info(`panel size changed, windowSize: ${windowSize.width}, ${windowSize.height}, ` +
    `keyboardArea: ${keyboardArea.top}, ${keyboardArea.bottom}, ${keyboardArea.left}, ${keyboardArea.right}`);
});
```

## setShadow

```TypeScript
setShadow(radius: double, color: string, offsetX: double, offsetY: double): void
```

通过Panel实例设置输入法窗口阴影效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Panel-setShadow(radius: double, color: string, offsetX: double, offsetY: double): void--><!--Device-Panel-setShadow(radius: double, color: string, offsetX: double, offsetY: double): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | double | 是 | 窗口边缘阴影的模糊半径，单位px，取值范围[0.0, +∞)，0.0时关闭窗口边缘阴影。 |
| color | string | 是 | 窗口边缘阴影的颜色，十六进制RGB或ARGB格式，不区分大小写，例如`#000000`或`#FF000000`。 |
| offsetX | double | 是 | 窗口边缘阴影X轴的偏移量，单位px。正值向右偏移，负值向左偏移。 |
| offsetY | double | 是 | 窗口边缘阴影Y轴的偏移量，单位px。正值向下偏移，负值向上偏移。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800017](../errorcode-inputmethod-framework.md#12800017-无效的面板类型或面板状态) | invalid panel type or panel flag. Possible causes: Panel's flag is FLG_FIXED. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |

