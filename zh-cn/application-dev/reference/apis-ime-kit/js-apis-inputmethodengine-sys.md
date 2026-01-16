# @ohos.inputMethodEngine (输入法服务)(系统接口)

本模块为系统输入法应用提供管理能力，包括创建软键盘窗口、插入/删除字符、选中文本、监听物理键盘按键事件等。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { inputMethodEngine } from '@kit.IMEKit';
```

## SizeUpdateCallback<sup>14+</sup>

type SizeUpdateCallback = (size: window.Size, keyboardArea: KeyboardArea) => void

当输入法面板大小变化时触发的回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

| 参数名       | 类型                                                 | 必填 | 说明                             |
| ------------ | ---------------------------------------------------- | ---- | -------------------------------- |
| size         | [window.Size](../apis-arkui/arkts-apis-window-i.md#size7) | 是   | 当前面板大小。                   |
| keyboardArea | [KeyboardArea](./js-apis-inputmethodengine.md#keyboardarea15)    | 是   | 当前面板中可作为键盘区域的大小。 |

## Panel<sup>10+</sup>

下列API均需使用[createPanel](./js-apis-inputmethodengine.md#createpanel10)获取到Panel实例后，通过实例调用。

### on('sizeUpdate')<sup>14+</sup>

on(type: 'sizeUpdate', callback: SizeUpdateCallback): void

监听当前面板大小变化。使用callback异步回调。

> **说明:**
>
> 仅用于SOFT_KEYBOARD类型，状态为FLG_FIXED或FLG_FLOATING的面板。输入法通过[adjustPanelRect](./js-apis-inputmethodengine.md#adjustpanelrect15)等接口对面板大小进行调节时，系统会根据一定规则校验计算出最终的数值（例如：超出屏幕等场景）。输入法应用可通过该回调获取的真实面板大小，完成最终的面板布局刷新。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSizeUpdate](#onSizeUpdate23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 14

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                   |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------ |
| type     | string                                      | 是   | 监听当前面板的大小是否产生变化，固定值为'sizeUpdate'。 |
| callback | [SizeUpdateCallback](#sizeupdatecallback14) | 是   | 回调函数。返回当前软键盘面板的大小，包含宽度和高度值。 |

**示例：**

```ts
import { window } from '@kit.ArkUI';

panel.on('sizeUpdate', (windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, windowSize: ${windowSize}, keyboardArea: ${keyboardArea}`);
});
```

### off('sizeUpdate')<sup>14+</sup>

off(type: 'sizeUpdate', callback?: SizeUpdateCallback): void

取消监听当前面板大小变化。使用callback异步回调。

> **说明:**
>
> 仅用于SOFT_KEYBOARD类型，状态为FLG_FIXED或FLG_FLOATING的面板。输入法通过[adjustPanelRect](./js-apis-inputmethodengine.md#adjustpanelrect15)等接口对面板大小进行调节时，系统会根据一定规则校验计算出最终的数值（例如：超出屏幕等场景）。输入法应用可通过该回调获取的真实面板大小，完成最终的面板布局刷新。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSizeUpdate](#offSizeUpdate23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 14

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                     |
| -------- | ------------------------------------------- | ---- | -------------------------------------------------------- |
| type     | string                                      | 是   | 监听当前面板的大小是否产生变化，固定取值为'sizeUpdate'。 |
| callback | [SizeUpdateCallback](#sizeupdatecallback14) | 否   | 回调函数。返回当前软键盘面板的大小，包含宽度和高度值。   |

**示例：**

```ts
import { window } from '@kit.ArkUI';

panel.off('sizeUpdate', (windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
```

### onSizeUpdate<sup>23+</sup>

onSizeUpdate(callback: SizeUpdateCallback): void

订阅面板尺寸更新（sizeUpdate）事件，当输入法面板尺寸发生变更时触发该事件，并执行指定的回调函数, 使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('sizeUpdate')](#onsizeUpdate14)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | [SizeUpdateCallback](#sizeupdatecallback14) | 是 | 面板尺寸更新时触发的回调函数，入参为面板尺寸信息对象。 |

**示例：**

```ts
import { window } from '@kit.ArkUI';

panel.onSizeUpdate((windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, windowSize: ${windowSize}, keyboardArea: ${keyboardArea}`);
});

```

### offSizeUpdate<sup>23+</sup>

offSizeUpdate(callback?: SizeUpdateCallback): void

取消订阅面板尺寸更新（sizeUpdate）事件，停止监听输入法面板尺寸的变更动作, 使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('sizeUpdate')](#offsizeUpdate14)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | [SizeUpdateCallback](#sizeupdatecallback14) | 否 | 可选参数，需取消的目标回调函数：传入指定回调函数实例时，仅取消该回调的订阅；不传入时，取消所有sizeUpdate事件的订阅。 |

**示例：**

```ts
import { window } from '@kit.ArkUI';

panel.offSizeUpdate((windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
```

## FluidLightMode<sup>20+</sup>

枚举，输入法流光模式。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

| 名称         | 值 | 说明               |
| ------------ | -- | ------------------ |
| NONE | 0 | 不使用流光模式。 |
| BACKGROUND_FLUID_LIGHT  | 1 | 背景流光。 |

## EditorAttribute

编辑框属性值。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

| 名称         | 类型 | 只读 | 可选 | 说明               |
| ------------ | -------- | ---- | ---- | ------------------ |
| fluidLightMode<sup>20+</sup> | [FluidLightMode](#fluidlightmode20) | 是 | 是 | 流光模式。如果没有设置或设置非法值，默认不使用流光模式。<br>该属性仅系统应用可以使用。|

## ImmersiveEffect<sup>20+</sup>

沉浸效果。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

| 名称   | 类型                                  | 只读 | 可选 | 说明           |
| ------ | ------------------------------------ | ---- | ---- | -------------- |
| fluidLightMode | [FluidLightMode](#fluidlightmode20) | 否   | 是   | 流光模式，如果不填充，则默认为NONE。<br>该属性仅系统应用可以使用。 |
<!--no_check-->