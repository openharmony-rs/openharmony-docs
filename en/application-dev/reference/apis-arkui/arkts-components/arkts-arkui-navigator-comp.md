# Navigator

The **Navigator** component provides redirection.

## Child Components

Supported

## Navigator

```TypeScript
Navigator(value?: { target: string; type?: NavigationType })
```

Called when the route jumps.

**Since:** 7

**Deprecated since:** 13

**Substitutes:** [NavPathInfo](arkts-arkui-navpathinfo-c.md)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { target: string; type?: NavigationType } | No | Information about the page to be redirected to.<br>target: Path of the target page to be redirected to. <br>type: Navigation type.<br>Default value: **NavigationType.Push** |

## Navigator

```TypeScript
Navigator()
```

Called when using the navigator.

**Since:** 7

**Deprecated since:** 13

**Substitutes:** [NavigationAttribute](arkts-arkui-navigation-comp-attribute.md#navigationattribute)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Enums

| Name | Description |
| --- | --- |
| [NavigationType](arkts-arkui-navigationtype-e.md) | Navigation type. |

## Examples

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
      }.params(new TextObject(this.name)) // Pass parameters to the Detail page.

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
  // Receive the input parameters of Navigator.ets.
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
