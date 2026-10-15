# RouterMode

```TypeScript
export enum RouterMode
```

Enumerates the routing modes.

**Since:** 9

<!--Device-router-export enum RouterMode--><!--Device-router-export enum RouterMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Single

```TypeScript
Single
```

Singleton mode.

If the URL of the target page already exists in the page stack, the page with that URL is moved to the top of the stack.

If the URL of the target page has no matching page in the page stack, the default multi-instance mode is used for page navigation. This mode is suitable for scenarios where a unique page instance needs to be maintained, for example, pages such as the home page and login page that should not appear repeatedly in the stack.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RouterMode-Single--><!--Device-RouterMode-Single-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Standard

```TypeScript
Standard
```

Multi-instance mode, which is also the default page navigation mode.

The target page is added to the top of the page stack, regardless of whether a page with the same URL already exists in the stack. This mode is suitable for scenarios where multiple identical pages need to be retained, for example, when product detail pages are browsed, each product requires an independent page instance.

**NOTE:** 

If no routing mode is specified, the default multi-instance mode is used for page navigation.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RouterMode-Standard--><!--Device-RouterMode-Standard-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
