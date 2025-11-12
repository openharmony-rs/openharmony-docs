# applyStyles：定义组件重用样式（ArkTS-Sta）

方法applyStyles将多条样式设置提炼成一个Styles方法，直接在组件声明的位置调用。通过applyStyles可以快速定义并复用自定义样式。开发指南见[applyStyles：定义组件重用样式（ArkTS-Sta）](../../../ui/state-management/arkts-apply-styles.md)。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 20开始支持。
>
> - 后续版本的新增接口，采用上角标单独标记接口的起始版本。

## applyStyles

applyStyles\<T extends CommonMethod\>(this: T, customStyles: CustomStyles): T

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名         | 类型                                    | 必填 | 说明                                                         |
| -------------- | -------------------------------------- | ---- | ----  |
| this           | T                                      | 是   | UI组件。 |
| customStyles   | [CustomStyles](./ts-universal-attributes-polymorphic-style.md#customstyles) | 是   | 给UI组件添加样式的回调函数。 |

**返回值：**

| 类型                  | 说明                       |
| --------------------- | -------------------------- |
| T                     | 返回添加样式后的UI组件。      |

**示例：**

```ts
'use static'
import { Color, Column, CommonMethod, Component, Entry, Text, applyStyles } from '@ohos.arkui.component';

// 定义在全局的Styles方法
function globalFancy(instance: CommonMethod) {
  instance.width(150);
  instance.height(100);
  instance.backgroundColor(Color.Pink);
}

@Entry
@Component
struct FancyUse {
  build() {
    Column() {
      // 使用全局的Styles方法
      Text('FancyA')
        .applyStyles(globalFancy)
        .fontSize(30)
    }
  }
}
```