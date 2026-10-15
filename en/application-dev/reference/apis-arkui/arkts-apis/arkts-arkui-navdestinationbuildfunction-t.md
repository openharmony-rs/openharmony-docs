# NavDestinationBuildFunction

```TypeScript
declare type NavDestinationBuildFunction = (name: string, param?: object) => void
```

Represents the function used by the **MultiNavigation** component to load navigation destination pages.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-unnamed-declare type NavDestinationBuildFunction = (name: string, param?: object) => void--><!--Device-unnamed-declare type NavDestinationBuildFunction = (name: string, param?: object) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | ID of the navigation destination page. |
| param | object | No | Parameter passed when creating a page through route navigation. Default: no parameter is passed when not provided. |
