# 组件预览

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xin11112-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

组件预览支持以自定义组件为最小单位进行预览，方便开发者查看单个自定义组件UI效果。

>  **说明：**
>
>  本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>  组件预览详情，请查看[组件预览特性文档](../../../ui/ui-ide-previewer.md#组件预览)。

## @Preview装饰器

@Preview装饰器用来装饰自定义组件，从而实现组件预览。

>  **说明：**
>
>  该接口支持在ArkTS卡片中使用，但是ArkTS卡片中暂不支持组件预览。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PreviewParams<sup>9+</sup>

@Preview参数对象。

设置@Preview的参数，指定预览设备的相关属性，如不同设备、不同屏幕状态等。

>  **说明：**
>
>  PreviewParams中只支持使用与定义参数类型相匹配的入参，否则所有的@Preview的参数都将被置为默认值。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型   | 只读 | 可选 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| title | string | 否 | 是 | 组件预览模块名，默认为自定义组件名称。仅支持英文和数字，不支持中文和特殊字符。|
| width | number | 否 | 是 | 预览设备的宽度，单位：px，默认为1080px。取值范围为[20, 3000]内的整数。 |
| height | number | 否 | 是 | 预览设备的高度，单位：px，默认为2340px。取值范围为[20, 3000]内的整数。 |
| locale| string | 否 | 是 |  预览设备的语言，如zh_CN、en_US等，默认为zh_CN。 |
| colorMode | string | 否 | 是 | 显示的亮暗模式，取值为light或dark，tv设备默认为dark，其他设备默认为light，wearable设备仅支持dark。 |
| deviceType | string | 否 | 是 | 组件预览渲染的设备类型，默认为Phone。设备类型枚举值参考[deviceTypes标签](./../../../quick-start/module-configuration-file.md#devicetypes标签)。 |
| dpi | number | 否 | 是 | 预览设备的屏幕DPI值，默认为480。取值范围为[120, 640]内的整数。 |
| orientation | string | 否 | 是 | 预览设备的横竖屏状态，取值为portrait或landscape，默认为portrait。 |
| roundScreen | boolean | 否 | 是 | 预览的屏幕形状是否为圆形，默认为false。true为圆形，false为非圆形。 |

## 示例

该示例分别使用了不传参@Preview和传参的@Preview。

```ts
@Entry
@Preview
@Component
struct Index {
  @State message: string = 'default Preview';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
    }
    .height('100%')
    .width('100%')
  }
}

@Preview({
  title: 'PreviewParams',
  width: 540,
  height: 1170
})
@Component
struct Test {
  @State message: string = 'PreviewParams';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontSize(40)
        .fontWeight(FontWeight.Bold)
    }
    .height('100%')
    .width('100%')
  }
}
```
