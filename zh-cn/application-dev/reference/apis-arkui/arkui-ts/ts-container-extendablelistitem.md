# ExtendableListItem (可扩展的ListItem)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

[ListItem](./ts-container-listitem.md)的扩展组件的基类。开发者可以自定义扩展组件继承ExtendableListItem，支持重写ListItem中的[属性](./ts-container-listitem.md#属性)和[通用属性](./ts-component-general-attributes.md)，同时支持自定义属性。在阅读本文档前，建议提前阅读[ListItem](./ts-container-listitem.md)。开发指南请参考[内置组件扩展](../../../ui/state-management-static/arkts-static-extendable-inner-component.md)。

**起始版本：** 26.0.0

>  **说明：**
>
>  本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { ExtendableListItem } from '@kit.ArkUI';
```

## 子组件

可以包含子组件。

## 属性

自定义的ListItem扩展组件类支持重写ListItem的[属性](./ts-container-listitem.md#属性)和[通用属性](./ts-component-general-attributes.md)，若不重写，则遵循对应属性的默认行为。此外，扩展组件类支持以下属性和自定义属性。

### setListItemOptions

setListItemOptions(value?: ListItemOptions): this

设置ListItem配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型                                    | 必填 | 说明                 |
| ------- | --------------------------------------- | ---- | -------------------- |
| value | [ListItemOptions](./ts-container-listitem.md#listitemoptions10对象说明) | 否   | 为ListItem提供可选参数，该对象内含有[ListItemStyle](./ts-container-listitem.md#listitemstyle10枚举说明)枚举类型的style参数。<br/>默认值：{ style: ListItemStyle.NONE } |

## 事件

支持ListItem的[事件](./ts-container-listitem.md#事件)。

## 示例

```ts
'use static'

import { ExtendableListItem, ListItemOptions, Length, LayoutPolicy, ListDividerOptions, List, Entry, Component, Text, State, ForEach, TextAlign, ListItem, Color } from '@kit.ArkUI';

class MyListItem extends ExtendableListItem {
  // 通用属性
  width(): this {
    super.width('100%');
    return this;
  }
  
  height(): this {
    super.height('100%');
    return this;
  }

  // 自定义属性
  newAttribute(): this {
    super.margin(10);
    super.borderRadius(10);
    return this;
  }
}

@Entry
@Component
struct Index {
  @State arr: Array<string> = new Array<string>();

  aboutToAppear(): void {
    for (let i = 0; i < 100; i++) {
      this.arr.push(i.toString());
    }
  }

  build() {
    List({ space: 10 }) {
      ForEach(this.arr, (item: string) => {
        // 调用扩展组件
        MyListItem() {
          Text(item.toString())
            .fontSize(16)
            .textAlign(TextAlign.Center)
            .size({ height: 100, width: '100%' })
            .onClick(() => {
              this.arr[0] += 'a';
            })
        }
        .width() // 调用重写属性
        .newAttribute() // 调用自定义属性
      }, (item: string) => item)
    }
    .width('100%')
    .height('100%')
    .divider({ strokeWidth: 1, color: Color.Blue } as ListDividerOptions)
  }
}
```

