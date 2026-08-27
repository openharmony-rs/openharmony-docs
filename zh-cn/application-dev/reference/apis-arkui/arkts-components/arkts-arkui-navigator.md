# Navigator

路由容器组件，提供路由跳转能力。
> **说明：**

## 子组件

可以包含子组件。

## Navigator

```TypeScript
Navigator(value?: { target: string; type?: NavigationType })
```

在路由跳转时调用。

**起始版本：** 7

**废弃版本：** 13

**替代接口：** [NavPathInfo](arkts-arkui-navpathinfo-c.md)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { target: string; type?: NavigationType } | 否 | 跳转页面的信息。 target：指定跳转目标页面的路径。 type：指定路由方式。 默认值：NavigationType.Push |

## Navigator

```TypeScript
Navigator()
```

在使用Navigator时调用。NavigationAttribute为Navigation组件的属性。

**起始版本：** 7

**废弃版本：** 13

**替代接口：** [NavigationAttribute](arkts-arkui-navigation-attribute.md)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NavigationType](arkts-arkui-navigationtype-e.md) | 路由的跳转方式。 |

## 示例

```TypeScript
// code.ets
export interface NameObject {
  name: string;
}

export class TextObject {
  text: NameObject;

  constructor(text: NameObject) {
    this.text = text;
  }
}
```

```TypeScript
import { NameObject, TextObject } from '../../code';

@Entry
@Component
struct NavigatorExample {
  @State active: boolean = false
  @State name: NameObject = { name: 'news' }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start, justifyContent: FlexAlign.SpaceBetween }) {
      Navigator({ target: 'pages/container/navigator/Detail', type: NavigationType.Push }) {
        Text('Go to ' + this.name.name + ' page')
          .width('100%').textAlign(TextAlign.Center)
      }.params(new TextObject(this.name)) // 传参数到Detail页面

      Navigator() {
        Text('Back to previous page').width('100%').textAlign(TextAlign.Center)
      }.active(this.active)
      .onClick(() => {
        this.active = true
      })
    }.height(150).width(350).padding(35)
  }
}
```

```TypeScript
import { NameObject } from '../../code';

@Entry
@Component
struct DetailExample {
  // 接收Navigator.ets的传参
  params: Record<string, NameObject> = this.getUIContext().getRouter().getParams() as Record<string, NameObject>
  @State name: NameObject = this.params.text

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start, justifyContent: FlexAlign.SpaceBetween }) {
      Navigator({ target: 'pages/container/navigator/Back', type: NavigationType.Push }) {
        Text('Go to back page').width('100%').height(20)
      }

      Text('This is ' + this.name.name + ' page')
        .width('100%').textAlign(TextAlign.Center)
    }
    .width('100%').height(200).padding({ left: 35, right: 35, top: 35 })
  }
}
```

```TypeScript
// Back.ets
@Entry
@Component
struct BackExample {
  build() {
    Column() {
      Navigator({ target: 'pages/container/navigator/Navigator', type: NavigationType.Back }) {
        Text('Return to Navigator Page').width('100%').textAlign(TextAlign.Center)
      }
    }.width('100%').height(200).padding({ left: 35, right: 35, top: 35 })
  }
}
```
