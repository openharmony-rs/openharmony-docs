# 自定义属性设置

当开发者希望在组件上设置自定义的属性时，可以使用自定义属性设置功能，在组件上设置自定义的属性。而这些自定义属性可以在其对应的FrameNode上获取，从而实现更自由的组件管理。

>  **说明：** 
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 从API version 12开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## customProperty

ArkTS-Dyn: customProperty(name: string, value: Optional\<Object>): T

ArkTS-Sta: customProperty(name: string, value: CustomProperty): this

设置组件的自定义属性。[自定义组件](../../../ui/state-management/arkts-create-custom-components.md)不支持设置自定义属性。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**参数：** 

| 参数名 | 类型                                                 | 必填 | 说明                                                         |
| ------ | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| name  | string | 是   | 自定义属性的名称。 |
| value  | ArkTS-Dyn: Optional\<Object> <br/>ArkTS-Sta: [CustomProperty](#customproperty23-1)| 是   | 自定义属性的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前组件。 |

## CustomProperty<sup>23+</sup>

type CustomProperty = undefined | null | Object | Record<string, CustomProperty> | Array\<CustomProperty>

自定义属性的值。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

| 类型 |说明   |
| ------ | ------------------- |
| Object | 自定义属性Object类型。|
| undefined | 自定义属性值为undefined。|
| Record<string, CustomProperty> \| Array\<CustomProperty>| 自定义属性类型为`Record<string, CustomProperty>`，表示键为字符串、值为CustomProperty类型的对象。|

## Optional<sup>12+</sup>

type Optional\<T> = T | undefined

定义可选类型，其值可以是undefined。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

## 示例

在Column组件上设置自定义属性，并在其对应的FrameNode上获取所设置的自定义属性。

| 类型 | 说明 |
| --- | --- |
| T | 自定义属性的值。 |

ArkTS1.1示例：

```ts
// xxx.ets
import { FrameNode, UIContext } from '@kit.ArkUI';

@Entry
@Component
struct CustomPropertyExample {
  build() {
    Column() {
      Text('text')
      Button('print').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        if (uiContext) {
          const node: FrameNode | null = uiContext.getFrameNodeById("Test_Column") || null;
          if (node) {
            for (let i = 1; i < 4; i++) {
              const key = 'customProperty' + i;
              const property = node.getCustomProperty(key);
              console.log(key, JSON.stringify(property));
            }
          }
        }
      })
    }
    .id('Test_Column')
    .customProperty('customProperty1', {
      'number': 10,
      'string': 'this is a string',
      'bool': true,
      'object': {
        'name': 'name',
        'value': 100
      }
    })
    .customProperty('customProperty2', {})
    .customProperty('customProperty2', undefined)
    .width('100%')
    .height('100%')
  }
}
```

ArkTS1.2示例：
```ts
// xxx.ets
import { Entry, Text, Column, Component, Button, ClickEvent, CustomProperty  } from '@ohos.arkui.component';
import { FrameNode, UIContext } from '@ohos.arkui.UIContext';

@Entry
@Component
struct CustomPropertyExample {
  build() {
    Column() {
      Text('text')
      Button('print').onClick((e: ClickEvent) => {
        const uiContext: UIContext = this.getUIContext();
        if (uiContext) {
          const node: FrameNode | null = uiContext.getFrameNodeById("Test_Column") || null;
          if (node) {
            for (let i = 1; i < 4; i++) {
              const key = 'customProperty' + i;
              const property = node.getCustomProperty(key);
              console.log(key, JSON.stringify(property));
            }
          }
        }
      })
    }
    .id('Test_Column')
    .customProperty('customProperty1', {
      'number': 10,
      'string': 'this is a string',
      'bool': true,
      'object': {
        'name': 'name',
        'value': 100
      } as Record<string, CustomProperty>
    } as Record<string, CustomProperty>)
    .customProperty('customProperty2', {})
    .customProperty('customProperty2', undefined)
    .width('100%')
    .height('100%')
  }
}
```