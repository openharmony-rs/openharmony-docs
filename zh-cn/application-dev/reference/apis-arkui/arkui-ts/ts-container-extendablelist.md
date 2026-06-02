# ExtendableList (可扩展的List)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

[List](./ts-container-list.md)的扩展组件的基类。开发者可以自定义扩展组件继承ExtendableList，支持重写List中的[属性](./ts-container-list.md#属性)和[通用属性](./ts-component-general-attributes.md)，同时支持自定义属性。在阅读本文档前，建议提前阅读[List](./ts-container-list.md)。开发指南请参考[内置组件扩展](../../../ui/state-management-static/arkts-static-extendable-inner-component.md)。

**起始版本：** 26.0.0

>  **说明：**
>
>  本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { ExtendableList } from '@kit.ArkUI';
```

## 子组件

仅支持[ListItem](ts-container-listitem.md)、[ListItemGroup](ts-container-listitemgroup.md)子组件和自定义组件。自定义组件在List下使用时，建议使用ListItem或ListItemGroup作为自定义组件的顶层组件，不建议给自定义组件设置属性和事件方法。

## 属性

自定义的List扩展组件类支持重写List的[属性](./ts-container-list.md#属性)和[通用属性](./ts-component-general-attributes.md)，若不重写，则遵循对应属性的默认行为。此外，扩展组件类支持以下属性和自定义属性。

### setListOptions

setListOptions(options?: ListOptions): this;

设置列表配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型                                    | 必填 | 说明                 |
| ------- | --------------------------------------- | ---- | -------------------- |
| options | [ListOptions](./ts-container-list.md#listoptions18对象说明) | 否   | List配置参数。<br/> 未设置时，则按照ListOptions中各参数的默认值配置。 |

## 事件

支持List的[事件](./ts-container-list.md#事件)、[滚动组件通用事件](ts-container-scrollable-common.md#事件)[通用事件](ts-component-general-events.md)。

## 示例

```ts
'use static'

import { ExtendableList, ListOptions, Length, ListDividerOptions, List, Entry, Component, Text, State, ForEach, TextAlign, ListItem, Color } from '@kit.ArkUI';

class MyList extends ExtendableList {
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
    this.height();
    this.width();
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
    // 调用扩展组件
    MyList({ space: 10 } as ListOptions) {
      ForEach(this.arr, (item: string) => {
        ListItem() {
          Text(item.toString())
            .fontSize(16)
            .textAlign(TextAlign.Center)
            .size({ height: 100, width: '100%' })
            .onClick(() => {
              this.arr[0] += 'a';
            })
        }
        .margin(10)
        .borderRadius(10)
        .backgroundColor('#FFFFFFFF')
      }, (item: string) => item)
    }
    .newAttribute() // 调用自定义属性
    .divider({ strokeWidth: 1, color: Color.Blue } as ListDividerOptions)
  }
}
```

