# FormCallbackInfo (System API)

```TypeScript
interface FormCallbackInfo
```

Represents the parameters for obtaining a widget ID (**formId**) when querying or uninstalling a widget.

**Since:** 12

<!--Device-unnamed-interface FormCallbackInfo--><!--Device-unnamed-interface FormCallbackInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## id

```TypeScript
id: number
```

Widget ID of the number type.

**NOTE:** 

If the obtained ID is **-1**, the ID is greater than or equal to 2^53. In this case, you need to use **idString** to obtain the ID.

**Type:** number

**Since:** 12

<!--Device-FormCallbackInfo-id: number--><!--Device-FormCallbackInfo-id: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## idString

```TypeScript
idString: string
```

Widget ID of the string type.

**Type:** string

**Since:** 12

<!--Device-FormCallbackInfo-idString: string--><!--Device-FormCallbackInfo-idString: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## isLocked

```TypeScript
isLocked: boolean
```

Indicates whether the form is locked.

**Type:** boolean

**Since:** 22

<!--Device-FormCallbackInfo-isLocked: boolean--><!--Device-FormCallbackInfo-isLocked: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
