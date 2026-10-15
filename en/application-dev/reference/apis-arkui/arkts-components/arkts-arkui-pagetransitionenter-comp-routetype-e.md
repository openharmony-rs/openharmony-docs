# RouteType

```TypeScript
declare enum RouteType
```

Sets the type of page transition.

**Since:** 7

<!--Device-unnamed-declare enum RouteType--><!--Device-unnamed-declare enum RouteType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None = 0
```

The page is not redirected. For example, when **RouteType** is **None** as described in **Push** and **Pop**, the transition effect of **PageTransitionEnter** takes effect when the page enters, and the transition effect of **PageTransitionExit** takes effect when the page exits.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RouteType-None = 0--><!--Device-RouteType-None = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Pop

```TypeScript
Pop = 2
```

Returns to the previous page, for example, from PageB to PageA. For PageB, the component style of **PageTransitionExit** with **RouteType** set to **None** or **Pop** takes effect; for PageA, the component style of **PageTransitionEnter** with **RouteType** set to **None** or **Pop** takes effect.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RouteType-Pop = 2--><!--Device-RouteType-Pop = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Push

```TypeScript
Push = 1
```

Jumps to the next page, for example, from PageA to PageB. For PageA, the component style of **PageTransitionExit** with **RouteType** set to **None** or **Push** takes effect; for PageB, the component style of **PageTransitionEnter** with **RouteType** set to **None** or **Push** takes effect.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RouteType-Push = 1--><!--Device-RouteType-Push = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
