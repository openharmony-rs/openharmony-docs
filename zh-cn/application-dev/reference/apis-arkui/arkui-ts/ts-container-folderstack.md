# FolderStack

FolderStack继承于Stack(层叠布局)控件，新增了<!--RP1-->折叠屏悬停<!--RP1End-->能力，通过在配置项[FolderStackOptions](#folderstackoptions18对象说明)的upperItems数组上设置子组件id，使相应子组件自动避让折叠屏折痕区后移到上半屏。

>  **说明：**
>
>  该组件从API version 11开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
>  该组件的悬停态能力针对<!--RP2-->双折叠<!--RP2End-->设计，只在双折叠设备生效。
>
>  当该组件的父组件为[if/else条件渲染节点](../../../ui/state-management/arkts-rendering-control-ifelse.md)时，折叠屏悬停能力将会失效。

## 子组件

可以包含多个子组件。


## 接口

FolderStack(options?: FolderStackOptions)

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名       | 类型                                    | 必填 | 说明                                                                 |
| ------------ | ------------------------------------------- | ---- |----------------------------------------------------------------------|
| options |  [FolderStackOptions](#folderstackoptions18对象说明) | 否   | FolderStack的配置项。 |

## FolderStackOptions<sup>18+</sup>对象说明

> **说明：**
>
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称       | 类型         | 必填 | 说明                       |
| ------------ | -------------------------- | ---- |----------------------------|
| upperItems<sup>11+</sup> |    Array<string\>  | 否   | FolderStack的配置项。<br/>upperItems：定义悬停态会被移到上半屏的子组件的id，组件id在此数组中的子组件悬停触发时自动避让折叠屏折痕区后移到上半屏，其它组件堆叠在下半屏区域。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |

## 属性

>  **说明：**
>
>  设置offset和margin属性，可能会导致上下半屏遮挡折痕区，不建议开发者使用。

除支持[通用属性](ts-component-general-attributes.md)外，还支持以下属性：

### alignContent

alignContent(value: Alignment)

设置子组件在容器内的对齐方式。该属性与[通用属性align](ts-universal-attributes-location.md)同时设置时，后设置的属性生效。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                        | 必填 | 说明                                                    |
| ------ | ------------------------------------------- | ---- | ------------------------------------------------------- |
| value  | [Alignment](ts-appendix-enums.md#alignment) | 是   | 子组件在容器内的对齐方式。<br/>默认值：Alignment.Center <br />非法值：按默认值处理。 |

### enableAnimation

enableAnimation(value: boolean)

设置是否使用默认动效。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                        | 必填 | 说明                                |
| ------ | ------------------------------------------- | ---- | ----------------------------------- |
| value  | boolean | 是   | 是否使用默认动效。<br/>默认值：true，设置true表示使用默认动效，设置false表示不使用默认动效。<br />非法值：按默认值处理。 |

### autoHalfFold

autoHalfFold(value: boolean)

设置是否开启自动旋转，仅在系统自动旋转关闭时该属性生效。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型    | 必填 | 说明                                |
| ------ | ------- | ---- | ----------------------------------- |
| value  | boolean | 是   | 是否开启自动旋转。<br/>默认值：true，设置true表示开启自动旋转，设置false表示关闭自动旋转。<br />非法值：按默认值处理。 |

## 事件

除支持[通用事件](ts-component-general-events.md)外，还支持以下事件：

### onFolderStateChange

onFolderStateChange(callback: OnFoldStatusChangeCallback)

当折叠状态改变的时候回调，仅在横屏状态下生效。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                            | 必填 | 说明                 |
| ---------- | ----------------------------------------------- | ---- | -------------------- |
| callback | [OnFoldStatusChangeCallback](#onfoldstatuschangecallback18) | 是   | 当前设备的折叠状态。 |


### onHoverStatusChange<sup>12+</sup>

onHoverStatusChange(handler: OnHoverStatusChangeCallback)

当悬停状态改变的时候回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                            | 必填 | 说明                 |
| ---------- | ----------------------------------------------- | ---- | -------------------- |
| handler | [OnHoverStatusChangeCallback](#onhoverstatuschangecallback18) | 是   | 当悬停状态改变的时候触发回调。 |

## OnHoverStatusChangeCallback<sup>18+</sup>

type OnHoverStatusChangeCallback = (param: HoverEventParam) => void

当悬停状态改变的时候触发回调。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名     | 类型                                            | 必填 | 说明                 |
| ---------- | ----------------------------------------------- | ---- | -------------------- |
| param | [HoverEventParam](#hovereventparam12对象说明) | 是   | 当悬停状态改变的时候触发回调。 |

## OnFoldStatusChangeCallback<sup>18+</sup>

type OnFoldStatusChangeCallback = (event: OnFoldStatusChangeInfo) => void

当前设备的折叠状态。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名     | 类型                                            | 必填 | 说明                 |
| ---------- | ----------------------------------------------- | ---- | -------------------- |
| callback | [OnFoldStatusChangeInfo](#onfoldstatuschangeinfo18) | 是   | 当前设备的折叠状态。 |


## OnFoldStatusChangeInfo<sup>18+</sup>

当折叠状态改变的时候回调，仅在横屏状态下生效。

> **说明：**
>
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| foldStatus<sup>11+</sup> | [FoldStatus](ts-appendix-enums.md#foldstatus11) | 否 | 否   | 当前设备的折叠状态。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |

## HoverEventParam<sup>12+</sup>对象说明

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| foldStatus       | [FoldStatus](ts-appendix-enums.md#foldstatus11)             | 否 | 否   | 当前设备的折叠状态。 |
| isHoverMode      | boolean                                                     | 否 | 否   | 当前是否为悬停态。设置为true时表示当前为悬停态，设置为false时表示当前为非悬停态。  |
| appRotation      | [AppRotation](ts-appendix-enums.md#approtation12)           | 否 | 否   | 当前应用方向。    |
| windowStatusType | [WindowStatusType](#windowstatustype12) | 否 | 否   | 窗口模式枚举。    |

## WindowStatusType<sup>12+</sup>

type WindowStatusType = WindowStatusType

窗口模式枚举。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型        | 说明                 |
| ---------- | ---------------------|
| [WindowStatusType](../js-apis-window.md#windowstatustype11)  | 窗口模式枚举。 |


## 示例

该示例实现了折叠屏悬停能力。

```ts
@Entry
@Component
struct Index {
  @State len_wid: number = 480
  @State w: string = "40%"

  build() {
    Column() {
      // upperItems将所需要的悬停到上半屏的id放入upperItems传入，其余组件会堆叠在下半屏区域
      FolderStack({ upperItems: ["upperitemsId"] }) {
        // 此Column会自动上移到上半屏
        Column() {
          Text("video zone").height("100%").width("100%").textAlign(TextAlign.Center).fontSize(25)
        }.backgroundColor('rgb(0, 74, 175)').width("100%").height("100%").id("upperitemsId")

        // 下列两个Column堆叠在下半屏区域
        Column() {
          Text("video title")
            .width("100%")
            .height(50)
            .textAlign(TextAlign.Center)
            .backgroundColor('rgb(213, 213, 213)')
            .fontSize(25)
        }.width("100%").height("100%").justifyContent(FlexAlign.Start)

        Column() {
          Text("video bar ")
            .width("100%")
            .height(50)
            .textAlign(TextAlign.Center)
            .backgroundColor('rgb(213, 213, 213)')
            .fontSize(25)
        }.width("100%").height("100%").justifyContent(FlexAlign.End)
      }
      .backgroundColor('rgb(39, 135, 217)')
      // 是否启动动效
      .enableAnimation(true)
      // 是否自动旋转
      .autoHalfFold(true)
      // folderStack回调 当折叠状态改变时回调
      .onFolderStateChange((msg) => {
        if (msg.foldStatus === FoldStatus.FOLD_STATUS_EXPANDED) {
          console.info("The device is currently in the expanded state")
        } else if (msg.foldStatus === FoldStatus.FOLD_STATUS_HALF_FOLDED) {
          console.info("The device is currently in the half folded state")
        } else {
          // .............
        }
      })
      // hoverStatusChange回调 当悬停状态改变时回调
      .onHoverStatusChange((msg) => {
        console.log('this foldStatus:' + msg.foldStatus);
        console.log('this isHoverMode:' + msg.isHoverMode);
        console.log('this appRotation:' + msg.appRotation);
        console.log('this windowStatusType:' + msg.windowStatusType);
      })
      // folderStack如果不撑满页面全屏，作为普通Stack使用
      .alignContent(Alignment.Bottom)
      .height("100%")
      .width("100%")
      .backgroundColor('rgb(39, 135, 217)')

    }
    .height("100%")
    .width("100%")
    .borderWidth(1)
    .borderColor('rgb(213, 213, 213)')
    .backgroundColor('rgb(0, 74, 175)')
    .expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.BOTTOM])
  }
}
```
**图1** 横屏展开
</br> ![FolderStack01.png](figures/FolderStack01.png)
</br> **图2** 横屏半折叠
</br> ![FolderStack02.png](figures/FolderStack02.png)