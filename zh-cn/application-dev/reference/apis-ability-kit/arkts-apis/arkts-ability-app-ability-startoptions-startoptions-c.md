# StartOptions

StartOptions可以作为启动UIAbility接口（例如[startAbility()](arkts-ability-uiabilitycontext-c.md#startability-1)）的入参，用于指定目标UIAbility启动时的选项，包括但不局限于窗口模式、目标UIAbility启动时所在的屏幕等。

**起始版本：** 9

<!--Device-unnamed-declare class StartOptions--><!--Device-unnamed-declare class StartOptions-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { StartOptions } from '@kit.AbilityKit';
```

## completionHandler

```TypeScript
completionHandler?: CompletionHandler
```

拉起应用结果的操作类，用于处理拉起应用的结果。

**类型：** CompletionHandler

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-StartOptions-completionHandler?: CompletionHandler--><!--Device-StartOptions-completionHandler?: CompletionHandler-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## displayId

```TypeScript
displayId?: number
```

屏幕ID，取值为大于等于-1的整数。

- 取值为-1，表示当前屏幕。  
- 取值为0，表示主屏幕。  
- 取值为正整数，表示指定ID的屏幕。

**说明**：

从API version 14开始，默认值是-1，即当前屏幕。

在API version 14之前版本，默认值为0，即主屏幕。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-StartOptions-displayId?: long--><!--Device-StartOptions-displayId?: long-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## hideStartWindow

```TypeScript
hideStartWindow?: boolean
```

启动当前应用的UIAbility时，控制是否隐藏窗口的启动页，true表示隐藏启动页，false表示不隐藏启动页。启动页介绍和规格详见[StartWindow](docroot://quick-start/module-configuration-file.md#startwindow标签)。

**约束：**

1.该功能仅在2in1设备和自由多窗模式下的Tablet设备上生效。

2.该功能仅在启动当前应用的UIAbility时生效。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-hideStartWindow?: boolean--><!--Device-StartOptions-hideStartWindow?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## maxWindowHeight

```TypeScript
maxWindowHeight?: number
```

窗口最大的高度，单位为vp，可以通过[getWindowLimitsVP](@ohos.window.d.ts:window.getWindowLimitsVP)获得当前窗口的尺寸限制。

**约束：**

该功能仅在[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态下生效。

**类型：** number

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-maxWindowHeight?: int--><!--Device-StartOptions-maxWindowHeight?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## maxWindowWidth

```TypeScript
maxWindowWidth?: number
```

窗口最大的宽度，单位为vp，可以通过[getWindowLimitsVP](@ohos.window.d.ts:window.getWindowLimitsVP)获得当前窗口的尺寸限制。

**约束：**

该功能仅在[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态下生效。

**类型：** number

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-maxWindowWidth?: int--><!--Device-StartOptions-maxWindowWidth?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## minWindowHeight

```TypeScript
minWindowHeight?: number
```

窗口最小的高度，单位为vp，可以通过[getWindowLimitsVP](@ohos.window.d.ts:window.getWindowLimitsVP)获得当前窗口的尺寸限制。

**约束：**

该功能仅在[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态下生效。

**类型：** number

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-minWindowHeight?: int--><!--Device-StartOptions-minWindowHeight?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## minWindowWidth

```TypeScript
minWindowWidth?: number
```

窗口最小的宽度，单位为vp，可以通过[getWindowLimitsVP](@ohos.window.d.ts:window.getWindowLimitsVP)获得当前窗口的尺寸限制。

**约束：**

该功能仅在[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态下生效。

**类型：** number

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-minWindowWidth?: int--><!--Device-StartOptions-minWindowWidth?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## processMode

```TypeScript
processMode?: contextConstant.ProcessMode
```

UIAbility启动后的进程模式。

**约束：**

1.该功能仅在2in1和Tablet设备上生效。

2.仅在[UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability-1)中生效。

3.processMode和startupVisibility必须同时设置。

**类型：** contextConstant.ProcessMode

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-processMode?: contextConstant.ProcessMode--><!--Device-StartOptions-processMode?: contextConstant.ProcessMode-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## splitRatio

```TypeScript
splitRatio?: window.SplitRatioPreference
```

分屏比首选项的类型。

**类型：** window.SplitRatioPreference

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-splitRatio?: window.SplitRatioPreference--><!--Device-StartOptions-splitRatio?: window.SplitRatioPreference-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## startWindowBackgroundColor

```TypeScript
startWindowBackgroundColor?: string
```

启动当前应用的UIAbility时，启动页所显示的背景颜色。固定为ARGB格式, 如：`#E5FFFFFF`。如果未配置该字段，则默认采用module.json5文件中startWindowBackground字段的配置。

**约束：**

- 启动其他应用的UIAbility时，该字段不生效。  
- 该功能仅在2in1和Tablet设备上生效。  
- 仅在[UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability-1)中生效。

**类型：** string

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-startWindowBackgroundColor?: string--><!--Device-StartOptions-startWindowBackgroundColor?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## startWindowIcon

```TypeScript
startWindowIcon?: image.PixelMap
```

启动当前应用的UIAbility时，启动页所显示的图标。如果未配置该字段，则默认采用module.json5文件中startWindowIcon字段的配置。

**约束：**

- 启动其他应用的UIAbility时，该字段不生效。  
- 该功能仅在2in1和Tablet设备上生效。  
- 仅在[UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability-1)中生效。  
- 图片数据大小限制为600MB。

**类型：** image.PixelMap

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-startWindowIcon?: image.PixelMap--><!--Device-StartOptions-startWindowIcon?: image.PixelMap-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## startupVisibility

```TypeScript
startupVisibility?: contextConstant.StartupVisibility
```

UIAbility启动后的可见性。当用户设置目标UIAbility为不可见时，目标UIAbility的窗口不会显示在前台，dock栏也不会有图标，同时目标UIAbility的onForeground生命周期不会被调用。

**约束：**

1.该功能仅在2in1和Tablet设备上生效。

2.仅在[UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability-1)中生效。

3.processMode和startupVisibility必须同时设置。

**类型：** contextConstant.StartupVisibility

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-startupVisibility?: contextConstant.StartupVisibility--><!--Device-StartOptions-startupVisibility?: contextConstant.StartupVisibility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## supportWindowModes

```TypeScript
supportWindowModes?: Array<bundleManager.SupportWindowMode>
```

启动UIAbility时，指定窗口是否显示最大化/窗口化/分屏按键。如果未配置该字段，则默认采用该UIAbility对应的[module.json5配置文件](docroot://quick-start/module-configuration-file.md)中[abilities标签](docroot://quick-start/module-configuration-file.md#abilities标签)的supportWindowMode字段取值。

- FULL_SCREEN：支持全屏模式。  
- FLOATING：支持悬浮窗模式。  
- SPLIT：支持分屏模式。通常需要配合FULL_SCREEN或FLOATING一起使用，不建议只配置SPLIT。当仅配置SPLIT时，2in1设备上的窗口默认为悬浮窗模式，支持进入分屏模式；Tablet设备上的窗口默认为全屏模式，支持进入分屏模式。

在[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态下同时配置FULL_SCREEN和SPLIT时，如果应用的[targetAPIVersion](docroot://quick-start/app-configuration-file.md#配置文件标签)小于15，窗口将以悬浮窗模式启动；如果应用的[targetAPIVersion](docroot://quick-start/app-configuration-file.md#配置文件标签)大于等于15，窗口将以全屏模式启动。

**约束：**

<!--RP1-->该功能仅在2in1和Tablet设备上生效。<!--RP1End-->

**类型：** Array&lt;bundleManager.SupportWindowMode&gt;

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-supportWindowModes?: Array<bundleManager.SupportWindowMode>--><!--Device-StartOptions-supportWindowModes?: Array<bundleManager.SupportWindowMode>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## windowCreateParams

```TypeScript
windowCreateParams?: window.WindowCreateParams
```

启动UIAbility时的窗口参数。

**类型：** window.WindowCreateParams

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-windowCreateParams?: window.WindowCreateParams--><!--Device-StartOptions-windowCreateParams?: window.WindowCreateParams-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## windowHeight

```TypeScript
windowHeight?: number
```

窗口的高度，单位为px。

取值范围为[minWindowHeight, maxWindowHeight]，取值范围单位为vp，可参考[vp2px](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#vp2px-1)换算为对应的px值。

**约束：**

该功能仅在[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态下生效。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-windowHeight?: int--><!--Device-StartOptions-windowHeight?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## windowLeft

```TypeScript
windowLeft?: number
```

以指定displayId的屏幕的左顶点为原点，窗口在x轴方向偏移量，单位为px，值为正表示在原点右侧，值为负表示在原点左侧。该参数为整数，非整数将向下取整。当窗口左顶点超出指定displayId的屏幕区域时，限制窗口在指定displayId的屏幕范围内可见。配置该字段时，建议同时配置windowTop。

**约束：**

该功能仅在[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态下生效。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-windowLeft?: int--><!--Device-StartOptions-windowLeft?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## windowMode

```TypeScript
windowMode?: number
```

启动UIAbility时的窗口模式，详见[WindowMode](arkts-ability-abilityconstant-windowmode-e.md)。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-windowMode?: int--><!--Device-StartOptions-windowMode?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## windowTop

```TypeScript
windowTop?: number
```

以指定displayId的屏幕的左顶点为原点，窗口在y轴方向偏移量，单位为px，值为正表示在原点下方，值为负表示在原点上方。该参数为整数，非整数将向下取整。当窗口顶部超出指定displayId的屏幕区域时，限制窗口在指定displayId的屏幕范围内可见。配置该字段时，建议同时配置windowLeft。

**约束：**

该功能仅在[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态下生效。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-windowTop?: int--><!--Device-StartOptions-windowTop?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## windowWidth

```TypeScript
windowWidth?: number
```

窗口的宽度，单位为px。

取值范围为[minWindowWidth, maxWindowWidth]，取值范围单位为vp，可参考[vp2px](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#vp2px-1)换算为对应的px值。

**约束：**

该功能仅在[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态下生效。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-windowWidth?: int--><!--Device-StartOptions-windowWidth?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## withAnimation

```TypeScript
withAnimation?: boolean
```

启动UIAbility时是否具有动画效果。

传入true时，跟随系统默认动画效果。传入false时，表示关闭启动UIAbility动画效果，仅在[自由窗口状态](docroot://windowmanager/window-terminology.md#自由窗口)的情况下生效。

此参数不填时，默认为undefined，跟随系统默认动画效果。

从<!--RP2-->OpenHarmony 6.1<!--RP2End-->开始支持。

**类型：** boolean

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-withAnimation?: boolean--><!--Device-StartOptions-withAnimation?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

