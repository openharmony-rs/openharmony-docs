# 属性操作工具
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sunbees-->
<!--Designer: @sunbees-->
<!--Tester: @khq-->
<!--Adviser: @Brilliantry_Rui-->

## ModifierUtils

ModifierUtils提供用于属性修改器和属性操作的工具方法。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

### isInstanceOf\<T extends CommonMethod\<T>>

isInstanceOf\<T extends CommonMethod\<T>>(instance: T, componentName: string): boolean

检查给定的实例是否为指定组件类型。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                        | 必填 | 说明                                                         |
| ------------ | --------------------------- | ---- | ------------------------------------------------------------ |
| instance     | T  | 是   | 要检查的实例，T为继承自[通用属性](./ts-component-general-attributes.md)（CommonMethod）的组件类型。               |
| componentName | string                      | 是   | 要检查的组件类型名称。                                        |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 返回该实例是否为指定的组件类型，如果实例是指定的组件类型，则返回true；否则返回false。 |

**示例：**  

```ts
// xxx.ets
// 点击按钮，并检查日志，判断组件是否进入了自己的独有分支
import { ModifierUtils } from '@kit.ArkUI';

class MyModifier implements AttributeModifier<TextAttribute | ButtonAttribute> {
  isDark: boolean = false

  constructor(dark?: boolean) {
    this.isDark = dark ?? false;
  }

  applyNormalAttribute(instance: TextAttribute | ButtonAttribute): void {
    if (ModifierUtils.isInstanceOf(instance, 'Text')) {
      console.info('This is TextAttribute')
      const textInstance = instance as TextAttribute
      if (this.isDark) {
        textInstance.backgroundColor(Color.Blue)
      } else {
        textInstance.backgroundColor(Color.Green)
      }
    } else if (ModifierUtils.isInstanceOf(instance, 'Button')) {
      console.info('This is ButtonAttribute')
      const buttonInstance = instance as ButtonAttribute
      if (this.isDark) {
        buttonInstance.type(ButtonType.Circle)
        buttonInstance.backgroundColor(Color.Blue)
      } else {
        buttonInstance.type(ButtonType.Normal)
        buttonInstance.backgroundColor(Color.Green)
      }
    }
  }
}

@Entry
@Component
struct MultiComponentAttributeDemo {
  @State myModifier: MyModifier = new MyModifier();

  build() {
    Column() {
      Text('Text')
        .fontSize(50)
        .attributeModifier(this.myModifier)
        .onClick(() => {
          this.myModifier.isDark = !this.myModifier.isDark;
        })
      Button('Button')
        .attributeModifier(this.myModifier)
        .onClick(() => {
          this.myModifier.isDark = !this.myModifier.isDark;
        })
    }
    .justifyContent(FlexAlign.SpaceEvenly)
    .width('100%')
    .height('50%')
  }
}
```