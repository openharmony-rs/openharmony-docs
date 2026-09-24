# 菜单控制（系统接口）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

为组件绑定弹出式菜单，支持长按、点击或鼠标右键来触发菜单的弹出，菜单项以垂直列表形式显示。

> **说明：**
>
> - 该组件从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本文仅介绍当前模块的系统接口，其他公开接口参见[菜单控制](./ts-universal-attributes-menu.md)。

## ContextMenuOptions<sup>10+</sup>

配置系统菜单的视觉表现选项，支持设置新材质下菜单的非线性动画模式（扭曲效果）及流光动画模式，提升菜单展示的交互体验与视觉质感。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<!--Table: 20%; 20%; 10%; 10%; 40%-->
| 名称                  | 类型                                                         | 只读 | 可选 | 说明                                                         |
| --------------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| distortionMode | [DistortionMode](./ts-appendix-enums-sys.md#distortionmode) | 否 | 是 | 设置系统材质下菜单的非线性动画模式。<br />**默认值：** DistortionMode.DISTORTION_AUTO <br/>**起始版本：** 26.0.0 <br />**系统接口：** 此接口为系统接口。|
| edgeLightMode | [EdgeLightMode](./ts-appendix-enums-sys.md#edgelightmode)| 否 | 是 | 设置系统材质下菜单的流光动画模式。<br />**默认值：** EdgeLightMode.EDGELIGHT_DISABLED <br/>**起始版本：** 26.0.0 <br />**系统接口：** 此接口为系统接口。|

## 示例

### 示例1（菜单设置沉浸式材质、非线性形变与流光）

该示例通过[bindContextMenu](./ts-universal-attributes-menu.md#bindcontextmenu8)为组件绑定菜单（长按或右键触发），并通过[ContextMenuOptions](#contextmenuoptions10)设置系统材质[systemMaterial](./ts-universal-attributes-menu.md#contextmenuoptions10)，以及非线性形变[distortionMode](#contextmenuoptions10)和流光[edgeLightMode](#contextmenuoptions10)，两者均设置为AUTO模式（依据设备算力档位和系统设置中的沉浸光感配置自适应生效）。

从API版本26.0.0开始，[ContextMenuOptions](#contextmenuoptions10)新增distortionMode和edgeLightMode属性。

```ts
// xxx.ets
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct MenuMaterialExample {
  // 沉浸式材质对象
  @State myMaterial: SystemUiMaterial | undefined = new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.THICK,
  });

  @Builder MenuBuilder() {
    Menu() {
      MenuItem({ content: 'Menu1' })
        .onClick(() => {
          console.info('handle Menu1 select');
        })
      MenuItem({ content: 'Menu2' })
        .onClick(() => {
          console.info('handle Menu2 select');
        })
    }
  }

  build() {
    Stack() {
      Column() {
        Text('click to show Menu')
          .fontSize(20)
          .margin({ top: 20 })
          .bindMenu(this.MenuBuilder, {
            // 设置沉浸式材质
            systemMaterial: this.myMaterial,
            // 非线性形变自适应
            distortionMode: DistortionMode.DISTORTION_AUTO,
            // 流光自适应
            edgeLightMode: EdgeLightMode.EDGELIGHT_AUTO,
          })
      }
      .width('100%')
      .height('100%')
      .justifyContent(FlexAlign.Center)
    }
    .backgroundColor(Color.Gray)
  }
}
```

该示例配图为设置沉浸式材质、非线性形变与流光的高算力设备强档效果。

![MenuMaterialExample](figures/menu_material.gif)

该示例配图为未设置沉浸式材质、非线性形变与流光的高算力设备强档效果。

![MenuNoMaterialExample](figures/menu_nomaterial.gif)