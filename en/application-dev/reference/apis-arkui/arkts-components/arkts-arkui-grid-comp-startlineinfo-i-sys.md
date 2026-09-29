# StartLineInfo (System API)

```TypeScript
declare interface StartLineInfo
```

Records the position of the start line in the grid.

**Since:** 23

<!--Device-unnamed-declare interface StartLineInfo--><!--Device-unnamed-declare interface StartLineInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## startIndex

```TypeScript
startIndex: number
```

In **OnGetStartIndexByOffsetCallback**, indicates the start index of the row where the scroll offset is located; in **OnGetStartIndexByIndexCallback**, indicates the start index of the row where the target index is located.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-StartLineInfo-startIndex: int--><!--Device-StartLineInfo-startIndex: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## startLine

```TypeScript
startLine: number
```

Start row number of the **GridItem** corresponding to **startIndex** in the grid layout. If the **GridItem** spans multiple rows and the current viewport starts displaying from the middle of the **GridItem**, **startLine** still indicates the actual first row number occupied by the **GridItem** in the complete grid layout.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-StartLineInfo-startLine: int--><!--Device-StartLineInfo-startLine: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## startOffset

```TypeScript
startOffset: number
```

Offset between the top of the **GridItem** corresponding to **startIndex** and the top of the **Grid**. <br>Unit: vp

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-StartLineInfo-startOffset: double--><!--Device-StartLineInfo-startOffset: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## totalOffset

```TypeScript
totalOffset: number
```

Total scrolling offset, that is, the offset between the top of the first **GridItem** in the **Grid** component and the top of the **Grid** component. <br>Unit: vp

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-StartLineInfo-totalOffset: double--><!--Device-StartLineInfo-totalOffset: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
