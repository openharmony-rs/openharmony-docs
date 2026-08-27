# LuminanceSampler（系统接口）

设置背景亮度取色参数、注册亮度变化监听回调、取消注册监听回调。

> **说明：**
> 
> 以下API需先使用UIContext中的[getLuminanceSampler](arkts-arkui-arkui-uicontext-uicontext-c-sys.md#getluminancesampler)方法获取到LuminanceSampler对象，再通过该对象调用对应方法。

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## offBackgroundLuminanceChange

```TypeScript
offBackgroundLuminanceChange(samplingCallback?: Callback<number>): void
```

取消注册取色监听回调。未指定回调时，取消所有监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| samplingCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 监听回调。 |

**示例**

从API version 23开始，新增支持[setBackgroundLuminanceSamplingConfigs](#setbackgroundluminancesamplingconfigs)、[onBackgroundLuminanceChange](#onbackgroundluminancechange)、[offBackgroundLuminanceChange](#offbackgroundluminancechange)接口，该示例通过调用这三个接口，展示了获取对应组件的取色器，并通过取色器给组件设置取色参数和取色回调，通过取色回调实现自定义的根据背景色反色效果。

```TypeScript
import { LengthMetrics } from '@kit.ArkUI';
import { Edges } from '@ohos.arkui.node';

@Entry
@Component
struct PagePicker {
  @State arr: string[] =
    ['#FFF7F7F7', '#FF004AAF', '#FF4169E1', '#FFA52A2A', '#FF008000', '#FFFFA500', '#FFFFC0CB', '#FF808080'];
  @State myButtonWidthStr: string = '400px';
  @State myButtonWidth: number = 400;
  @State myButtonHeightStr: string = '150px';
  @State myButtonHeight: number = 150;
  @State myColor: string = '#FFF7F7F7';
  @State myButtonFontColor: string = '#FF004AAF';

  build() {
    Row() {
      Stack() {
        Scroll() {
          Column() {
            ForEach(this.arr, (item: Color) => {
              Column()
                .width('100%')
                .height(200)
                .backgroundColor(item)
            })
            ForEach(this.arr, (item: Color) => {
              Column()
                .width('100%')
                .height(200)
                .backgroundColor(item)
            })
          }
          .width('100%')
        }
        .width('100%')
        .height('100%')

        Button('Button')
          .backgroundColor(this.myColor)
          .fontColor(this.myButtonFontColor)
          .margin({ bottom: 300 })
          .width(this.myButtonWidthStr)
          .height(this.myButtonHeightStr)
          .id("myButton")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let uniqueId = this.getUniqueId();
            // 获取取色器
            let luminanceSampler = uiContext.getLuminanceSampler({ id: "myButton", componentId: uniqueId });
            // 设置节点自身的取色范围
            let edges: Edges<LengthMetrics> = {
              top: LengthMetrics.px(0),
              bottom: LengthMetrics.px(this.myButtonHeight),
              left: LengthMetrics.px(0),
              right: LengthMetrics.px(this.myButtonWidth)
            };

            luminanceSampler?.setBackgroundLuminanceSamplingConfigs({
              samplingInterval: 300,
              brightThreshold: 200,
              darkThreshold: 100,
              region: edges
            });
            // 取色回调
            let luminanceChangeCallback = (luminance: number) => {
              if (luminance > 200) {
                this.myColor = '#FF004AAF';
                this.myButtonFontColor = '#FFF7F7F7';
              } else if (luminance < 100) {
                this.myColor = '#FFF7F7F7';
                this.myButtonFontColor = '#FF004AAF';
              }
            };
            luminanceSampler?.offBackgroundLuminanceChange();
            luminanceSampler?.onBackgroundLuminanceChange(luminanceChangeCallback);
          })
      }.width('100%')
      .height('100%')
      .alignContent(Alignment.Bottom)
    }
    .height('100%')
  }
}
```

## onBackgroundLuminanceChange

```TypeScript
onBackgroundLuminanceChange(samplingCallback: Callback<number>): void
```

设置取色监听回调。回调的触发条件：背景亮度根据[setBackgroundLuminanceSamplingConfigs](#setbackgroundluminancesamplingconfigs) 接口设置的亮阈值和暗阈值分为三个区间，[0，暗阈值)，[暗阈值，亮阈值]，(亮阈值，255]。背景亮度所在区间发生变化（或者首次注册监听回调），并且距离上次取色的时间间隔达到设置的取色时间间隔时触发取色回调，并返回当前背景亮度。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| samplingCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 监听回调。触发同时返回当前背景亮度。   **说明：**监听回调里不能调用 [offBackgroundLuminanceChange](#offbackgroundluminancechange)。 |

**示例**

参考[offBackgroundLuminanceChange](#offbackgroundluminancechange)的示例。

## setBackgroundLuminanceSamplingConfigs

```TypeScript
setBackgroundLuminanceSamplingConfigs(configs: BackgroundLuminanceSamplingConfigs): void
```

设置取色参数配置。当亮度阈值不在指定范围内或暗阈值大于亮阈值将抛出异常。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configs | [BackgroundLuminanceSamplingConfigs](arkts-arkui-arkui-uicontext-backgroundluminancesamplingconfigs-i-sys.md) | 是 | 取色参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error.   1. Incorrect parameter values.   2. Incorrect parameters types. |

**示例**

参考[offBackgroundLuminanceChange](#offbackgroundluminancechange)的示例。
