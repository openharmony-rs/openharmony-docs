# RouterMode

```TypeScript
export enum RouterMode
```

Enumerates the routing modes.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Standard

```TypeScript
Standard
```

Multi-instance mode. It is the default routing mode.

The target page is added to the top of the page stack, regardless of whether a page with the same URL exists in the stack.

**NOTE:** 

If no routing mode is used, the navigation will be carried out according to the default multi-instance mode.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Single

```TypeScript
Single
```

Singleton mode.

If the URL of the target page already exists in the page stack, the page is moved to the top of the stack.

If the URL of the target page does not exist in the page stack, the page is redirected to in multi-instance mode.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
