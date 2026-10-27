# SafeAreaInsetAlignment (System API)

```TypeScript
declare enum SafeAreaInsetAlignment
```

Enumerates alignment positions for safe area inset content along its attachment edge. The alignment axis is horizontal for the top and bottom edges and vertical for the start and end edges.

**Since:** 26.1.0

<!--Device-unnamed-declare enum SafeAreaInsetAlignment--><!--Device-unnamed-declare enum SafeAreaInsetAlignment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## CENTER

```TypeScript
CENTER = 1
```

Centers content along the attachment edge.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SafeAreaInsetAlignment-CENTER = 1--><!--Device-SafeAreaInsetAlignment-CENTER = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## END

```TypeScript
END = 2
```

Aligns content to the end of the attachment edge. For the top and bottom edges, this is the right in a left-to-right layout and the left in a right-to-left layout. For the start and end edges, this is the bottom.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SafeAreaInsetAlignment-END = 2--><!--Device-SafeAreaInsetAlignment-END = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## START

```TypeScript
START = 0
```

Aligns content to the beginning of the attachment edge. For the top and bottom edges, this is the left in a left-to-right layout and the right in a right-to-left layout. For the start and end edges, this is the top.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-SafeAreaInsetAlignment-START = 0--><!--Device-SafeAreaInsetAlignment-START = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
