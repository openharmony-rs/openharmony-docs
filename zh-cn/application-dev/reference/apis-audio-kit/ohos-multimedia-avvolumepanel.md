# @ohos.multimedia.avVolumePanel (音量面板)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @liao_qian-->
<!--SE: @ccfriend-->
<!--TSE: @chenmingxi1_huawei-->

本模块提供创建音量面板AVVolumePanel的功能，提供展示和调节系统音量的统一面板。

应用无法直接调节系统音量，可以通过系统音量面板，让用户通过界面操作来调节音量。当用户通过应用内音量面板调节音量时，系统会展示音量提示界面，显性地提示用户系统音量发生改变。


> **说明：**
>
> - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 示例效果请以真机为准，当前DevEco Studio预览器无真实音量展示和调节功能。
> - **设备限制：** 
>   - 在穿戴设备上，可用于调节系统音量，但不显示UX界面，需开发者自行设计界面。

## 导入模块

```js
import { AVVolumePanel } from '@kit.AudioKit';
```

## 属性

支持[通用属性](../apis-arkui/arkui-ts/ts-component-general-attributes.md)。

## AVVolumePanel

AVVolumePanel({volumeLevel?: number, volumeParameter?: AVVolumePanelParameter})

音量面板，可用于在当前应用内展示音量调节面板。

**装饰器类型：** [@Component](../../ui/state-management/arkts-create-custom-components.md)

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

| 名称 | 类型 | 必填 | 装饰器类型  | 说明                                                                                                                                                                                                    |
| -------- | -------- | -------- |--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|volumeLevel | number | 否 | \@Prop | 通过音量面板设置的音量值。该值应介于当前设备音量的最小值和最大值之间。如果该值大于当前设备音量的最大值，则视为设置最大音量值；如果该值小于当前设备音量的最小值，则视为设置最小音量值。获取设备的最大值、最小值和当前值，可参考[AudioVolumeGroupManager](../apis-audio-kit/arkts-apis-audio-AudioVolumeGroupManager.md)。 |
|volumeParameter | [AVVolumePanelParameter](#avvolumepanelparameter)  | 否 | \@Prop | 设置音量面板的自定义参数。 如果不传入该参数，则调用系统音量条。                                                                                                                                                                      |

## AVVolumePanelParameter

音量面板参数设置。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
|position | [Position](../apis-arkui/arkui-ts/ts-types.md#position) | 否 | 设置音量面板的位置。如果不传入该参数，则为系统音量条位置。 |

## 事件

支持[通用事件](../apis-arkui/arkui-ts/ts-component-general-events.md)。

## 使用建议

1. 应用在实现自定义音量条的过程中，建议使用音频框架的音量变化监听接口，通过接口回调的音量类型volumeEvent.volumeType，音量等级volumeEvent.volume以及是否显示音量条volumeEvent.updateUi等信息，应用可以判断是否需要处理当前数据和显示自定义的音量条，具体可参考[音量变化回调接口](arkts-apis-audio-AudioVolumeManager.md#onstreamvolumechange20)介绍。
2. 为确保用户能感知音量变化，不允许应用后台调节音量，系统会做出对应的控制措施。

## 示例

音量面板功能的示例说明参考如下。

```ts
import { AVVolumePanel } from '@kit.AudioKit';

@Entry
@Component
struct Index {

  @State volume: number = 0;

  build() {
    Row() {
      Column() {
        AVVolumePanel({
          volumeLevel: this.volume,
          volumeParameter: {
            position: {
              x: 100,
              y: 200
            }
          }
        })
      }
    }.width('50%').height('50%')
  }
}
```
