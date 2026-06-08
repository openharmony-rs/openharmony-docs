# 特效绘制合并
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

用于对背景模糊等特效进行绘制合并。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 从API version 12开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。

## useEffect

useEffect(value: boolean): T

用于对背景模糊等特效进行绘制合并。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[useEffect<sup>23+</sup>](#useeffect23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | boolean | 是 | 控制组件是否继承特效绘制合并组件的特效属性参数，从而合并绘制特效。<br/>useEffect为true时子组件继承特效绘制合并组件的特效属性参数，为false时子组件不继承特效绘制合并组件的特效属性参数。<br/>默认值：false|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

## useEffect<sup>14+</sup>

useEffect(useEffect: boolean, effectType: EffectType): T

用于设置组件是否应用<!--Del-->父级[EffectComponent](ts-container-effectcomponent-sys.md)或<!--DelEnd-->窗口定义的效果模板。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[useEffect<sup>23+</sup>](#useeffect23)。

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| useEffect  | boolean                                                      | 是   | 控制组件是否应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>useEffect为true时表示应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>默认值：false |
| effectType | [EffectType](ts-universal-attributes-use-effect.md#effecttype14) | 是   | 设置组件应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>默认值：EffectType.DEFAULT |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

## useEffect<sup>18+</sup>

useEffect(useEffect: Optional\<boolean>, effectType?: EffectType): T

用于设置组件是否应用<!--Del-->父级[EffectComponent](ts-container-effectcomponent-sys.md)或<!--DelEnd-->窗口定义的效果模板。与[useEffect<sup>14+</sup>](#useeffect14)相比，useEffect参数新增了对undefined类型的支持。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 18开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[useEffect<sup>23+</sup>](#useeffect23)。

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| useEffect | Optional\<boolean> | 是 | 控制组件是否应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>useEffect为true时表示应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>默认值：false<br/>当useEffect的值为undefined时，维持之前取值。 |
| effectType | [EffectType](ts-universal-attributes-use-effect.md#effecttype14) | 否 | 设置组件应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>默认值：EffectType.DEFAULT|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

## useEffect<sup>23+</sup>

useEffect(useEffect: boolean | undefined, effectType: EffectType | undefined)

用于设置组件是否应用<!--Del-->父级[EffectComponent](ts-container-effectcomponent-sys.md)或<!--DelEnd-->窗口定义的效果模板。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[useEffect](#useeffect)，[useEffect<sup>14+</sup>](#useeffect14)和[useEffect<sup>18+</sup>](#useeffect18)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| useEffect  | boolean \| undefined                                                      | 是   | 控制组件是否应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>useEffect为true时表示应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>默认值：false<br/>当useEffect的值为undefined时，恢复为无应用模板的效果。 |
| effectType | [EffectType](ts-universal-attributes-use-effect.md#effecttype14) \| undefined | 是   | 设置组件应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>默认值：EffectType.DEFAULT<br/>当effectType的值为undefined时，恢复为无应用模板的效果。 |

## useEffect<sup>23+</sup>

useEffect(value: boolean | undefined)

用于对背景模糊等特效进行绘制合并。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[useEffect](#useeffect)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | boolean \| undefined | 是 | 控制组件是否继承特效绘制合并组件的特效属性参数，从而合并绘制特效。<br/>useEffect为true时子组件继承特效绘制合并组件的特效属性参数，为false时子组件不继承特效绘制合并组件的特效属性参数。<br/>默认值：false<br/>当value的值为undefined时，恢复为无应用特效绘制合并的效果。 |

## EffectType<sup>14+</sup>

使用效果模板种类的枚举值。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 23

| 名称     | 值   | 说明                   |
| -------- | ---- | ---------------------- |
| DEFAULT  | 0   | 使用<!--Del-->父级EffectComponent定义的<!--DelEnd-->效果模板进行定义。 |
| WINDOW_EFFECT  | 1   | 使用窗口定义的效果模板进行定义。 |

效果模板

|  设备类型    | 模糊半径(单位: px)   | 饱和度                 |  亮度  |  颜色  |
| -------- | ---- | ---------------------- | -------- | -------- |
| 移动设备  | 0   | 0 | 0 | '#ffffffff'，显示为白色。 |
| 2in1设备：深色模式  | 80   | 1.5 | 1.0 | '#e52e3033'，显示为半透明的深灰色。 |
| 2in1设备：浅色模式  | 80   | 1.9 | 1.0 | '#e5ffffff'，显示为半透明的白色。 |
| Tablet设备  | 0   | 0 | 0 | '#ffffffff'，显示为白色。 |

<!--Del-->
## 示例

该示例主要通过背景模糊等特效进行绘制合并效果。

<!--code_no_check-->

```ts
//Index.ets
@Entry
@Component
struct Index {
  @State isUse: boolean = true;

  build() {
    Stack() {
      Image($r("app.media.mountain"))
        .autoResize(true)
      EffectComponent() {
        Column({ space: 20 }) {
           Column() {
           }
           .position({ x: 0, y: 0 })
           .width(150)
           .height(800)
           .useEffect(this.isUse, EffectType.WINDOW_EFFECT)
         
           Column() {
           }
           .position({ x: 200, y: 20 })
           .width(150)
           .height(300)
           .useEffect(this.isUse, EffectType.DEFAULT)

           Column() {
           }
           .position({ x: 400, y: 20 })
           .width(150)
           .height(300)
           .useEffect(this.isUse)
        }
        .width('100%')
        .height('100%')
      }
      .backgroundBlurStyle(BlurStyle.Thin)

       Column() {
       }
        .position({ x: 600, y: 0 })
        .width(150)
        .height(800)
        .useEffect(this.isUse, EffectType.WINDOW_EFFECT)

      Row() {
        Button('useEffect')
        .margin(30)
        .onClick(() => {
          this.isUse = !this.isUse;
        })
      }
      .position({ x: 300, y: 450 })
    }
    .backgroundColor(Color.Black)
    .width('100%')
  }
}
```

![zh_image_useeffect_effecttype](figures/zh_image_useeffect_effecttype.png)
<!--DelEnd-->