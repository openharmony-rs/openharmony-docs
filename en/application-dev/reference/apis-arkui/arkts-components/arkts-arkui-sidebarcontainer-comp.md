# SideBarContainer

The **SideBarContainer** component contains a sidebar and content area as its child components. The sidebar is the first child component and can be shown or hidden as needed. The content area is the second child component.

> **NOTE**

> The APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate > their

## Child Components

Supported

> **NOTE:** 
> 
> - Allowed child component types: built-in and custom components, excluding rendering control types ([if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), and [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)).
> 
> - This component must contain two child components.
> 
> - If there are three or more child components, only the first and second child components are displayed. If there is only one child component, the sidebar is displayed, and the content area is blank.
> 
> - The focus navigation is performed in the content area and then in the sidebar of the **SideBarContainer**component.

## SideBarContainer

```TypeScript
SideBarContainer(type?: SideBarContainerType)
```

Creates a sidebar container.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SideBarContainerType](arkts-arkui-sidebarcontainer-comp-sidebarcontainertype-e.md) | No | Display type of the sidebar.<br>Default value: **SideBarContainerType.Embed** |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ButtonIconOptions](arkts-arkui-sidebarcontainer-comp-buttoniconoptions-i.md) | Describes the icons of the sidebar control button. |
| [ButtonStyle](arkts-arkui-sidebarcontainer-comp-buttonstyle-i.md) | Describes the style of the sidebar control button. |
| [DividerStyle](arkts-arkui-sidebarcontainer-comp-dividerstyle-i.md) | Sets the divider style. |

### Enums

| Name | Description |
| --- | --- |
| [SideBarContainerType](arkts-arkui-sidebarcontainer-comp-sidebarcontainertype-e.md) | Enumerates the types of sidebar containers. |
| [SideBarPosition](arkts-arkui-sidebarcontainer-comp-sidebarposition-e.md) | Enumerates the positions of the sidebar. |

## Examples

This example demonstrates how to use the SideBarContainer component and implement the page layout.

```TypeScript
// xxx.ets
@Entry
@Component
struct SideBarContainerExample {
  // Replace $r('app.media.icon') with the image resource file required.
  normalIcon: Resource = $r('app.media.icon');
  selectedIcon: Resource = $r('app.media.icon');
  @State menuItems: number[] = [1, 2, 3];
  @State selectedItemId: number = 1;

  build() {
    SideBarContainer(SideBarContainerType.Embed) {
      Column() {
        ForEach(this.menuItems, (item: number) => {
          Column({ space: 5 }) {
            Image(this.selectedItemId === item ? this.selectedIcon : this.normalIcon).width(64).height(64)
            Text('Index0' + item)
              .fontSize(25)
              .fontColor(this.selectedItemId === item ? '#0A59F7' : '#999')
              .fontFamily('source-sans-pro,cursive,sans-serif')
          }
          .onClick(() => {
            this.selectedItemId = item;
          })
        }, (item: number) => item.toString())
      }.width('100%')
      .justifyContent(FlexAlign.SpaceEvenly)
      .backgroundColor('#19000000')

      Column() {
        Text('SideBarContainer content text1').fontSize(25)
        Text('SideBarContainer content text2').fontSize(25)
      }
      .margin({ top: 50, left: 20, right: 30 })
    }
    .controlButton({
      icons: {
        // Replace $r('app.media.drawer') with the image resource file you use.
        hidden: $r('app.media.drawer'),
        shown: $r('app.media.drawer'),
        switching: $r('app.media.drawer')
      }
    })
    .sideBarWidth(150)
    .minSideBarWidth(50)
    .maxSideBarWidth(300)
    .minContentWidth(0)
    .onChange((value: boolean) => {
      console.info('status:' + value);
    })
    .divider({ strokeWidth: '1vp', color: Color.Gray, startMargin: '4vp', endMargin: '4vp' })
  }
}
```
