# Interfaces (其他)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin; @liyi0903; @huangxiaolinabc-->
<!--Designer: @piggyguy; @liyi0903; @fangzhiyuan1-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。

## TargetInfo<sup>18+</sup>

指定组件绑定的目标节点。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| id | ArkTS-Dyn: string&nbsp;\|&nbsp;number <br>ArkTS-Sta: string&nbsp;\|&nbsp;int | 否 | 否 | 指定popup或menu绑定的目标节点。<br/>**说明：** <br/>1. 当id是number时，对应组件实例的UniqueID，此id由系统保证唯一性。<br/>2. 当id是string时，对应[通用属性id](arkui-ts/ts-universal-attributes-component-id.md#id)所指定的组件，此id的唯一性需由开发者确保，但实际可能会有多个。 |
| componentId | ArkTS-Dyn: number <br>ArkTS-Sta: int | 否 | 是 | 目标节点所在的自定义组件的UniqueID。当上述id指定为string类型时，可通过此属性圈定范围。方便开发者在一定范围内保证id: string的唯一性。 |

## PageInfo<sup>12+</sup>

Router和NavDestination等页面信息，若无对应的Router或NavDestination页面信息，则对应属性为undefined。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- |-------- | -------- |
| routerPageInfo | observer.[RouterPageInfo](js-apis-arkui-observer.md#routerpageinfo) | 否 |是 | Router信息。 |
| navDestinationInfo | observer.[NavDestinationInfo](js-apis-arkui-observer.md#navdestinationinfo) | 否 |是| NavDestination信息。 |

## OverlayManagerOptions<sup>15+</sup>

初始化[OverlayManager](arkts-apis-uicontext-overlaymanager.md)时所用参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称             | 类型                | 只读 | 可选   | 说明                     |
| --------------- | ---------------------- | ------------ | --------------------- | --------------------- |
| renderRootOverlay   | boolean | 否 | 是 | 是否渲染overlay根节点，true表示渲染overlay根节点，false表示不渲染overlay根节点，默认值为true。通过将该参数设置为false，可以解决[OverlayManager](arkts-apis-uicontext-overlaymanager.md)显示在[PhotoPickerComponent](../apis-media-library-kit/ohos-file-PhotoPickerComponent.md)上层时，PhotoPickerComponent无法选中照片的问题。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 15开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 15<br/>**ArkTS-Sta起始版本：** 23|
| enableBackPressedEvent<sup>19+</sup>   | boolean | 否 | 是 | 是否支持通过侧滑手势关闭OverlayManager下的ComponentContent，true表示可以通过侧滑关闭，false表示不可以通过侧滑关闭，默认值为false。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 19<br/>**ArkTS-Sta起始版本：** 23 |
| onBackPress   | [OnOverlayBackPressCallback](arkts-apis-uicontext-t.md#onoverlaybackpresscallback) | 否 | 是 | 拦截Overlay侧滑返回事件的回调。<br/>**说明：**<br/>1. 注册该回调且**enableBackPressedEvent**设置为true时，侧滑返回事件不会自动关闭Overlay，而是调用该回调决定事件是否向下层组件传递。<br/>2. 返回true表示拦截该事件（事件被消费，不会向下层传递）；返回false表示不拦截，事件将向下层组件透传。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API版本 26.0.0开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 26.0.0<br/>**ArkTS-Sta起始版本：** 26.0.0|

## GestureTriggerInfo<sup>20+</sup>

特定手势回调函数触发时的信息。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 24

| 名称   | 类型   | 只读   |   可选    |说明       |
| ------ | ---- | ---------- |---------- |---------- |
| event | [GestureEvent](../apis-arkui/arkui-ts/ts-gesture-common.md#gestureevent对象说明)   |否  |  否       |手势事件对象。 |
| current | [GestureRecognizer](arkui-ts/ts-gesture-common.md#gesturerecognizer12)    |否  |  否      |手势识别器对象。可从中获取手势的详细信息，但请勿在本地保留此对象，因为当节点释放后该对象可能失效。 |
| currentPhase  | [GestureActionPhase](arkts-apis-uicontext-e.md#gestureactionphase20) |否  |  否      | 手势动作回调阶段。|
| node  | [FrameNode](js-apis-arkui-frameNode.md) |否   |  是   |触发手势的节点。默认值为null，表示没有触发手势的节点。 |

## GestureObserverConfigs<sup>20+</sup>

该参数用于指定需要监听的手势回调阶段（传入空数组将无效），仅当手势触发指定阶段时才会发送通知。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 24

| 名称   | 类型   | 只读  |  可选       |说明       |
| ------ | ---- | ---------- |---------- |---------- |
|  actionPhases | Array\<[GestureActionPhase](arkts-apis-uicontext-e.md#gestureactionphase20)\>    |否  |  否       |手势事件对象。 |

## SwiperContentInfo<sup>22+</sup>

Swiper组件的内容区信息。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

| 名称      | 类型 | 只读  | 可选 | 说明                    |
| --------- | ---- | ----- | ---- | ----------------------- |
| id        | string  | 否 | 否 | Swiper组件的id。 |
| uniqueId  | ArkTS-Dyn: number <br>ArkTS-Sta: int  | 否 | 否 | Swiper组件的唯一标识符。 |
| swiperItemInfos   | Array\<[SwiperItemInfo](#swiperiteminfo22)\> | 否 | 否 | 当前处于显示状态的Swiper子组件的信息。 |

## SwiperItemInfo<sup>22+</sup>

Swiper子组件的信息。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

| 名称      | 类型 | 只读  | 可选 | 说明                    |
| --------- | ---- | ----- | ---- | -----------------------|
| uniqueId  | ArkTS-Dyn: number <br>ArkTS-Sta: int | 否 | 否 | Swiper子组件的唯一标识符。   |
| index     | ArkTS-Dyn: number <br>ArkTS-Sta: int | 否 | 否 | Swiper子组件在Swiper中的索引。 |
