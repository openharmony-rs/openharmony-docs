# 列表选择弹窗 (ActionSheet) (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

创建列表选择弹窗。

> **说明：**
>
> 从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见[UIContext](../arkts-apis-uicontext-uicontext.md)说明。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[列表选择弹窗 (ActionSheet)](ts-methods-action-sheet.md)。

## ActionSheetOptions

列表选择弹窗的样式。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称      | 类型                    | 只读 | 可选 | 说明                          |
| ---------- | -------------------------- | ------- | ----------------------------- | ----------------------------- |
| distortionMode | [DistortionMode](./ts-appendix-enums-sys.md#distortionmode) | 否 | 是 | 设置系统材质下弹窗的非线性动画模式。<br/>**默认值：** DistortionMode.DISTORTION_AUTO <br/>**系统接口：** 此接口为系统接口。<br/>**起始版本：** 26.0.0<br/>**模型约束：** 此接口仅可在Stage模型下使用。|
| edgeLightMode | [EdgeLightMode](./ts-appendix-enums-sys.md#edgelightmode) | 否 | 是 | 设置系统材质下弹窗的流光动画模式。<br/>**默认值：** EdgeLightMode.EDGELIGHT_AUTO <br/>**系统接口：** 此接口为系统接口。<br/>**起始版本：** 26.0.0<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |

## 示例

### 示例1（列表选择弹窗设置沉浸式材质、非线性形变与流光）

该示例通过[showActionSheet](../arkts-apis-uicontext-uicontext.md#showactionsheet)设置[ActionSheetOptions](#actionsheetoptions)中的系统材质systemMaterial，以及非线性形变[distortionMode](#actionsheetoptions)和流光[edgeLightMode](#actionsheetoptions)，两者均设置为AUTO模式（依据设备算力档位和系统设置中的沉浸光感配置自适应生效）。

从API版本26.0.0开始，[ActionSheetOptions](#actionsheetoptions)新增distortionMode和edgeLightMode属性。

```ts
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct ActionSheetExample {
  build() {
    Stack({ alignContent: Alignment.Top }) {
      Column() {
        Button("ActionSheet")
          .margin(20)
          .onClick(() => {
            this.getUIContext().showActionSheet({
              title: 'ActionSheet Title',
              message: 'ActionSheet Text',
              sheets: [
                {
                  title: 'Apples',
                  action: () => {
                    console.info('apples');
                  }
                },
                {
                  title: 'Bananas',
                  action: () => {
                    console.info('bananas');
                  }
                },
                {
                  title: 'Pears',
                  action: () => {
                    console.info('pears');
                  }
                }
              ],
              alignment: DialogAlignment.Center,
              // 设置沉浸式材质
              systemMaterial: new uiMaterial.ImmersiveMaterial({ style: uiMaterial.ImmersiveStyle.ULTRA_THICK }),
              // 非线性形变自适应
              distortionMode: DistortionMode.DISTORTION_AUTO,
              // 流光自适应
              edgeLightMode: EdgeLightMode.EDGELIGHT_AUTO,
            });
          })
      }
      .height('100%')
      .width('100%')
      .backgroundColor(Color.Gray)
    }
  }
}
```

该示例配图为设置沉浸式材质、非线性形变与流光的高算力设备强档效果。

![ActionSheetExample](figures/ActionSheet_material.gif)

该示例配图为未设置沉浸式材质、非线性形变与流光的高算力设备强档效果。

![ActionSheetNoExample](figures/ActionSheet_nomaterial.gif)