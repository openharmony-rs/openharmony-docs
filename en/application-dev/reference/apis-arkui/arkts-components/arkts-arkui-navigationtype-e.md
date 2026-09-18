# NavigationType

Navigation type.

**Since:** 7

**Deprecated since:** 13

**Substitutes:** Navigation

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Push

```TypeScript
Push
```

Navigates to the specified page in the application.

**NOTE:** 

This API is supported since API version 7 and deprecated since API version 13. You are advised to use pushPath instead.

**Since:** 7

**Deprecated since:** 13

**Substitutes:** pushPath

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Back

```TypeScript
Back
```

Returns to the specified page. If the specified page does not exist in the stack, no response is returned. If no page is specified, the previous page is returned to.

**NOTE:** 

This API is supported since API version 7 and deprecated since API version 13. You are advised to use pop instead.

**Since:** 7

**Deprecated since:** 13

**Substitutes:** pop

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Replace

```TypeScript
Replace
```

Replaces the current page with another one in the application and destroys the current page.

**NOTE:** 

This API is supported since API version 7 and deprecated since API version 13. You are advised to use replacePath instead.

**Since:** 7

**Deprecated since:** 13

**Substitutes:** replacePath

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
