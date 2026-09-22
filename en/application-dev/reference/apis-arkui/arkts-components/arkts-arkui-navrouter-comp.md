# NavRouter

The **NavRouter** component provides default processing logic for responding to clicks, eliminating the need for manual logic definition.

> **NOTE** > > This component is deprecated since API version 13. You are advised to use [NavPathStack](arkts-arkui-navigation-comp-navpathstack-c.md) in > conjunction with the **navDestination** attribute for page routing.

## Child Components

This component must contain two child components, the second of which must be NavDestination.

> **NOTE:** 
> 
> 1. If there is only one child component, the navigation to the **NavDestination** component does not work.
> 
> 2. If there is only the **NavDestination** child component, the navigation does not work.
> 
> 3. If there are more than two child components, the excess child components are not displayed.
> 
> 4. If the second child component is not **NavDestination**, the navigation does not work.

## NavRouter

```TypeScript
NavRouter()
```

Constructor.

**Since:** 9

**Deprecated since:** 13

**Substitutes:** [NavDestinationAttribute](arkts-arkui-navdestination-comp-attribute.md#navdestinationattribute)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NavRouter

```TypeScript
NavRouter(value: RouteInfo)
```

Provides route information so that clicking the **NavRouter** component redirects the user to the specified navigation destination page.

**Since:** 10

**Deprecated since:** 13

**Substitutes:** [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RouteInfo](arkts-arkui-navrouter-comp-routeinfo-i.md) | Yes | Route information. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [RouteInfo](arkts-arkui-navrouter-comp-routeinfo-i.md) | Route information. |

### Enums

| Name | Description |
| --- | --- |
| [NavRouteMode](arkts-arkui-navrouter-comp-navroutemode-e.md) | Defines the routing policy. |

## Examples

```TypeScript
// xxx.ets
@Entry
@Component
struct NavRouterExample {
  @State isActiveWLAN: boolean = false
  @State isActiveBluetooth: boolean = false

  build() {
    Navigation() {
      NavRouter() {
        Row() {
          Row()
            .width(30)
            .height(30)
            .borderRadius(30)
            .margin({ left: 3, right: 10 })
            .backgroundColor(Color.Pink)
          Text(`WLAN`)
            .fontSize(22)
            .fontWeight(500)
            .textAlign(TextAlign.Center)
        }
        .width('90%')
        .height(60)

        NavDestination() {
          Flex({ direction: FlexDirection.Row }) {
            Text('No WLAN available.').fontSize(30).padding({ left: 15 })
          }
        }.title("WLAN")
      }
      .margin({ top: 10, bottom: 10 })
      .backgroundColor(this.isActiveWLAN ? '#ccc' : '#fff')
      .borderRadius(20)
      .mode(NavRouteMode.PUSH_WITH_RECREATE)
      .onStateChange((isActivated: boolean) => {
        this.isActiveWLAN = isActivated
      })

      NavRouter() {
        Row() {
          Row()
            .width(30)
            .height(30)
            .borderRadius(30)
            .margin({ left: 3, right: 10 })
            .backgroundColor(Color.Pink)
          Text(`Bluetooth`)
            .fontSize(22)
            .fontWeight(500)
            .textAlign(TextAlign.Center)
        }
        .width('90%')
        .height(60)

        NavDestination() {
          Flex({ direction: FlexDirection.Row }) {
            Text('No Bluetooth device available.').fontSize(30).padding({ left: 15 })
          }
        }.title("Bluetooth")
      }
      .margin({ top: 10, bottom: 10 })
      .backgroundColor(this.isActiveBluetooth ? '#ccc' : '#fff')
      .borderRadius(20)
      .mode(NavRouteMode.REPLACE)
      .onStateChange((isActivated: boolean) => {
        this.isActiveBluetooth = isActivated
      })
    }
    .height('100%')
    .width('100%')
    .title('Settings')
    .backgroundColor("#F2F3F5")
    .titleMode(NavigationTitleMode.Free)
    .mode(NavigationMode.Auto)
  }
}
```
