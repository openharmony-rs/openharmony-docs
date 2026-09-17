# layout.h

## Overview

Defines the layout-related types for the native module.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md) | ArkUI_PixelRoundPolicy | Defines the PixelRound policy of a component's four edges. |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md) | ArkUI_PositionEdges | Define the Edges describing the position of a component by distances to the container's four edges. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_Alignment](#arkui_alignment) | ArkUI_Alignment | Enumerates the alignment modes. |
| [ArkUI_ItemAlignment](#arkui_itemalignment) | ArkUI_ItemAlignment | Enumerates the modes in which components are laid out along the cross axis of the container. |
| [ArkUI_FlexAlignment](#arkui_flexalignment) | ArkUI_FlexAlignment | Enumerates the vertical alignment modes. |
| [ArkUI_FlexDirection](#arkui_flexdirection) | ArkUI_FlexDirection | Enumerates the directions of the main axis in the flex container. |
| [ArkUI_FlexWrap](#arkui_flexwrap) | ArkUI_FlexWrap | Defines whether the flex container has a single line or multiple lines. |
| [ArkUI_Direction](#arkui_direction) | ArkUI_Direction | Enumerates the modes in which components are laid out along the main axis of the container. |
| [ArkUI_Axis](#arkui_axis) | ArkUI_Axis | Enumerates the scroll directions for the <b><List></b> component. |
| [ArkUI_VerticalAlignment](#arkui_verticalalignment) | ArkUI_VerticalAlignment | Enumerates the vertical alignment modes. |
| [ArkUI_HorizontalAlignment](#arkui_horizontalalignment) | ArkUI_HorizontalAlignment | Enumerates the alignment mode in the horizontal direction. |
| [ArkUI_SafeAreaEdge](#arkui_safeareaedge) | ArkUI_SafeAreaEdge | defines the enumerated value of the direction of the extended security zone. |
| [ArkUI_LayoutSafeAreaType](#arkui_layoutsafeareatype) | ArkUI_LayoutSafeAreaType | Define the types for expanding the safe area in layout. |
| [ArkUI_LayoutSafeAreaEdge](#arkui_layoutsafeareaedge) | ArkUI_LayoutSafeAreaEdge | Define the edges for expanding the safe area in layout. |
| [ArkUI_LocalizedAlignment](#arkui_localizedalignment) | ArkUI_LocalizedAlignment | Enumerates the localizedAlignment modes. |
| [ArkUI_LayoutPolicy](#arkui_layoutpolicy) | ArkUI_LayoutPolicy | Enumerates the LayoutPolicy. |
| [ArkUI_PixelRoundCalcPolicy](#arkui_pixelroundcalcpolicy) | ArkUI_PixelRoundCalcPolicy | Enumerates the PixelRoundPolicy. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_GuidelineOption* OH_ArkUI_GuidelineOption_Create(int32_t size)](#oh_arkui_guidelineoption_create) | Create auxiliary line information in the RelativeContaine container. |
| [void OH_ArkUI_GuidelineOption_Dispose(ArkUI_GuidelineOption* guideline)](#oh_arkui_guidelineoption_dispose) | Destroy auxiliary line information. |
| [void OH_ArkUI_GuidelineOption_SetId(ArkUI_GuidelineOption* guideline, const char* value, int32_t index)](#oh_arkui_guidelineoption_setid) | Set the Id of the auxiliary line. |
| [void OH_ArkUI_GuidelineOption_SetDirection(ArkUI_GuidelineOption* guideline, ArkUI_Axis value, int32_t index)](#oh_arkui_guidelineoption_setdirection) | Set the direction of the auxiliary line. |
| [void OH_ArkUI_GuidelineOption_SetPositionStart(ArkUI_GuidelineOption* guideline, float value, int32_t index)](#oh_arkui_guidelineoption_setpositionstart) | Set the distance from the left or top of the container. |
| [void OH_ArkUI_GuidelineOption_SetPositionEnd(ArkUI_GuidelineOption* guideline, float value, int32_t index)](#oh_arkui_guidelineoption_setpositionend) | Set the distance from the right or bottom of the container. |
| [const char* OH_ArkUI_GuidelineOption_GetId(ArkUI_GuidelineOption* guideline, int32_t index)](#oh_arkui_guidelineoption_getid) | Get the Id of the auxiliary line. |
| [ArkUI_Axis OH_ArkUI_GuidelineOption_GetDirection(ArkUI_GuidelineOption* guideline, int32_t index)](#oh_arkui_guidelineoption_getdirection) | Get the direction of the auxiliary line. |
| [float OH_ArkUI_GuidelineOption_GetPositionStart(ArkUI_GuidelineOption* guideline, int32_t index)](#oh_arkui_guidelineoption_getpositionstart) | Get the distance from the left or top of the container. |
| [float OH_ArkUI_GuidelineOption_GetPositionEnd(ArkUI_GuidelineOption* guideline, int32_t index)](#oh_arkui_guidelineoption_getpositionend) | Get the distance from the right side or bottom of the container. |
| [ArkUI_BarrierOption* OH_ArkUI_BarrierOption_Create(int32_t size)](#oh_arkui_barrieroption_create) | creates barrier information within the RelativeContaine container. |
| [void OH_ArkUI_BarrierOption_Dispose(ArkUI_BarrierOption* barrierStyle)](#oh_arkui_barrieroption_dispose) | Destroy barrier information. |
| [void OH_ArkUI_BarrierOption_SetId(ArkUI_BarrierOption* barrierStyle, const char* value, int32_t index)](#oh_arkui_barrieroption_setid) | Set the Id of the barrier. |
| [void OH_ArkUI_BarrierOption_SetDirection(ArkUI_BarrierOption* barrierStyle, ArkUI_BarrierDirection value, int32_t index)](#oh_arkui_barrieroption_setdirection) | Set the direction of the barrier. |
| [void OH_ArkUI_BarrierOption_SetReferencedId(ArkUI_BarrierOption* barrierStyle, const char* value, int32_t index)](#oh_arkui_barrieroption_setreferencedid) | Sets the dependent component of the barrier. |
| [const char* OH_ArkUI_BarrierOption_GetId(ArkUI_BarrierOption* barrierStyle, int32_t index)](#oh_arkui_barrieroption_getid) | Get the Id of the barrier. |
| [ArkUI_BarrierDirection OH_ArkUI_BarrierOption_GetDirection(ArkUI_BarrierOption* barrierStyle, int32_t index)](#oh_arkui_barrieroption_getdirection) | Gets the direction of the barrier. |
| [const char* OH_ArkUI_BarrierOption_GetReferencedId(ArkUI_BarrierOption* barrierStyle, int32_t index, int32_t referencedIndex)](#oh_arkui_barrieroption_getreferencedid) | Get the dependent components of the barrier. |
| [int32_t OH_ArkUI_BarrierOption_GetReferencedIdSize(ArkUI_BarrierOption* barrierStyle, int32_t index)](#oh_arkui_barrieroption_getreferencedidsize) | Gets the number of dependent components of the barrier. |
| [ArkUI_AlignmentRuleOption* OH_ArkUI_AlignmentRuleOption_Create()](#oh_arkui_alignmentruleoption_create) | creates alignment rule information for subcomponents in relative containers. |
| [void OH_ArkUI_AlignmentRuleOption_Dispose(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_dispose) | Destroys the alignment rule information of subcomponents in relative containers. |
| [void OH_ArkUI_AlignmentRuleOption_SetStart(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)](#oh_arkui_alignmentruleoption_setstart) | Set the start alignment parameter. |
| [void OH_ArkUI_AlignmentRuleOption_SetEnd(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)](#oh_arkui_alignmentruleoption_setend) | Set the end alignment parameter. |
| [void OH_ArkUI_AlignmentRuleOption_SetCenterHorizontal(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)](#oh_arkui_alignmentruleoption_setcenterhorizontal) | Set the parameters for horizontal center alignment. |
| [void OH_ArkUI_AlignmentRuleOption_SetTop(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)](#oh_arkui_alignmentruleoption_settop) | Set the parameters for top alignment. |
| [void OH_ArkUI_AlignmentRuleOption_SetBottom(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)](#oh_arkui_alignmentruleoption_setbottom) | Set the bottom alignment parameters. |
| [void OH_ArkUI_AlignmentRuleOption_SetCenterVertical(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)](#oh_arkui_alignmentruleoption_setcentervertical) | Set the parameters for vertical center alignment. |
| [void OH_ArkUI_AlignmentRuleOption_SetBiasHorizontal(ArkUI_AlignmentRuleOption* option, float horizontal)](#oh_arkui_alignmentruleoption_setbiashorizontal) | Sets the horizontal offset parameter of the component under the anchor point constraint. |
| [void OH_ArkUI_AlignmentRuleOption_SetBiasVertical(ArkUI_AlignmentRuleOption* option, float vertical)](#oh_arkui_alignmentruleoption_setbiasvertical) | Set the vertical offset parameter of the component under the anchor point constraint. |
| [const char* OH_ArkUI_AlignmentRuleOption_GetStartId(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getstartid) | Get the Id of the start-aligned parameter. |
| [ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetStartAlignment(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getstartalignment) | Gets the alignment of the start-aligned parameter. |
| [const char* OH_ArkUI_AlignmentRuleOption_GetEndId(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getendid) | Get the end alignment parameter. |
| [ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetEndAlignment(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getendalignment) | Get the end alignment parameter. |
| [const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdHorizontal(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getcenteridhorizontal) | Gets the parameters of horizontal center alignment. |
| [ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentHorizontal(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getcenteralignmenthorizontal) | Gets the parameters of horizontal center alignment. |
| [const char* OH_ArkUI_AlignmentRuleOption_GetTopId(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_gettopid) | Get the top-aligned parameters. |
| [ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetTopAlignment(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_gettopalignment) | Get the top-aligned parameters. |
| [const char* OH_ArkUI_AlignmentRuleOption_GetBottomId(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getbottomid) | Get the bottom alignment parameters. |
| [ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetBottomAlignment(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getbottomalignment) | Get the bottom alignment parameters. |
| [const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdVertical(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getcenteridvertical) | Gets the parameters of vertical center alignment. |
| [ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentVertical(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getcenteralignmentvertical) | Gets the parameters of vertical center alignment. |
| [float OH_ArkUI_AlignmentRuleOption_GetBiasHorizontal(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getbiashorizontal) | Get the bias value in the horizontal direction. |
| [float OH_ArkUI_AlignmentRuleOption_GetBiasVertical(ArkUI_AlignmentRuleOption* option)](#oh_arkui_alignmentruleoption_getbiasvertical) | Get the bias value in the vertical direction. |
| [ArkUI_PositionEdges* OH_ArkUI_PositionEdges_Create()](#oh_arkui_positionedges_create) | Create an edge object for position attribute. |
| [ArkUI_PositionEdges* OH_ArkUI_PositionEdges_Copy(const ArkUI_PositionEdges* edges)](#oh_arkui_positionedges_copy) | Creates a deep copy of an edge object for position attribute. |
| [void OH_ArkUI_PositionEdges_Dispose(ArkUI_PositionEdges* edges)](#oh_arkui_positionedges_dispose) | Dispose an edge object for position attribute. |
| [void OH_ArkUI_PositionEdges_SetTop(ArkUI_PositionEdges* edges, float value)](#oh_arkui_positionedges_settop) | Sets the top edge of an edge object for position attribute. |
| [int32_t OH_ArkUI_PositionEdges_GetTop(ArkUI_PositionEdges* edges, float* value)](#oh_arkui_positionedges_gettop) | Gets the top edge of an edge object for position attribute. |
| [void OH_ArkUI_PositionEdges_SetLeft(ArkUI_PositionEdges* edges, float value)](#oh_arkui_positionedges_setleft) | Sets the left edge of an edge object for position attribute. |
| [int32_t OH_ArkUI_PositionEdges_GetLeft(ArkUI_PositionEdges* edges, float* value)](#oh_arkui_positionedges_getleft) | Gets the left edge of an edge object for position attribute. |
| [void OH_ArkUI_PositionEdges_SetBottom(ArkUI_PositionEdges* edges, float value)](#oh_arkui_positionedges_setbottom) | Sets the bottom edge of an edge object for position attribute. |
| [int32_t OH_ArkUI_PositionEdges_GetBottom(ArkUI_PositionEdges* edges, float* value)](#oh_arkui_positionedges_getbottom) | Gets the bottom edge of an edge object for position attribute. |
| [void OH_ArkUI_PositionEdges_SetRight(ArkUI_PositionEdges* edges, float value)](#oh_arkui_positionedges_setright) | Sets the right edge of an edge object for position attribute. |
| [int32_t OH_ArkUI_PositionEdges_GetRight(ArkUI_PositionEdges* edges, float* value)](#oh_arkui_positionedges_getright) | Gets the right edge of an edge object for position attribute. |
| [ArkUI_PixelRoundPolicy* OH_ArkUI_PixelRoundPolicy_Create()](#oh_arkui_pixelroundpolicy_create) | Create a policy object for PixelRound attribute. |
| [void OH_ArkUI_PixelRoundPolicy_Dispose(ArkUI_PixelRoundPolicy* policy)](#oh_arkui_pixelroundpolicy_dispose) | Dispose a policy object for PixelRound attribute. |
| [void OH_ArkUI_PixelRoundPolicy_SetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)](#oh_arkui_pixelroundpolicy_settop) | Sets the top edge of a policy object for PixelRound attribute. |
| [int32_t OH_ArkUI_PixelRoundPolicy_GetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)](#oh_arkui_pixelroundpolicy_gettop) | Gets the top edge of a policy object for PixelRound attribute. |
| [void OH_ArkUI_PixelRoundPolicy_SetStart(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)](#oh_arkui_pixelroundpolicy_setstart) | Sets the start edge of a policy object for PixelRound attribute. |
| [int32_t OH_ArkUI_PixelRoundPolicy_GetStart(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)](#oh_arkui_pixelroundpolicy_getstart) | Gets the start edge of a policy object for PixelRound attribute. |
| [void OH_ArkUI_PixelRoundPolicy_SetBottom(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)](#oh_arkui_pixelroundpolicy_setbottom) | Sets the bottom edge of a policy object for PixelRound attribute. |
| [int32_t OH_ArkUI_PixelRoundPolicy_GetBottom(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)](#oh_arkui_pixelroundpolicy_getbottom) | Gets the bottom edge of a policy object for PixelRound attribute. |
| [void OH_ArkUI_PixelRoundPolicy_SetEnd(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)](#oh_arkui_pixelroundpolicy_setend) | Sets the end edge of a policy object for PixelRound attribute. |
| [int32_t OH_ArkUI_PixelRoundPolicy_GetEnd(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)](#oh_arkui_pixelroundpolicy_getend) | Gets the end edge of a policy object for PixelRound attribute. |

## Enum type description

### ArkUI_Alignment

```c
enum ArkUI_Alignment
```

**Description**

Enumerates the alignment modes.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_ALIGNMENT_TOP_START = 0 | Top start. |
| ARKUI_ALIGNMENT_TOP | Top center. |
| ARKUI_ALIGNMENT_TOP_END | Top end. |
| ARKUI_ALIGNMENT_START | Vertically centered start. |
| ARKUI_ALIGNMENT_CENTER | Horizontally and vertically centered. |
| ARKUI_ALIGNMENT_END | Vertically centered end. |
| ARKUI_ALIGNMENT_BOTTOM_START | Bottom start. |
| ARKUI_ALIGNMENT_BOTTOM | Horizontally centered on the bottom. |
| ARKUI_ALIGNMENT_BOTTOM_END | Bottom end. |

### ArkUI_ItemAlignment

```c
enum ArkUI_ItemAlignment
```

**Description**

Enumerates the modes in which components are laid out along the cross axis of the container.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_ITEM_ALIGNMENT_AUTO = 0 | The default configuration in the container is used. |
| ARKUI_ITEM_ALIGNMENT_START | The items in the container are aligned with the cross-start edge. |
| ARKUI_ITEM_ALIGNMENT_CENTER | The items in the container are centered along the cross axis. |
| ARKUI_ITEM_ALIGNMENT_END | The items in the container are aligned with the cross-end edge. |
| ARKUI_ITEM_ALIGNMENT_STRETCH | The items in the container are stretched and padded along the cross axis. |
| ARKUI_ITEM_ALIGNMENT_BASELINE | The items in the container are aligned in such a manner that their text baselines are aligned along the |

### ArkUI_FlexAlignment

```c
enum ArkUI_FlexAlignment
```

**Description**

Enumerates the vertical alignment modes.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_FLEX_ALIGNMENT_START = 1 | The child components are aligned with the start edge of the main axis. |
| ARKUI_FLEX_ALIGNMENT_CENTER = 2 | The child components are aligned in the center of the main axis. |
| ARKUI_FLEX_ALIGNMENT_END = 3 | The child components are aligned with the end edge of the main axis. |
| ARKUI_FLEX_ALIGNMENT_SPACE_BETWEEN = 6 | The child components are evenly distributed along the main axis. The space between any two adjacent components is the same. The first component is aligned with the main-start, and the last component is aligned with |
| ARKUI_FLEX_ALIGNMENT_SPACE_AROUND = 7 | The child components are evenly distributed along the main axis. The space between any two adjacent components is the same. The space between the first component and main-start, and that between the last component and |
| ARKUI_FLEX_ALIGNMENT_SPACE_EVENLY = 8 | The child components are evenly distributed along the main axis. The space between the first component and main-start, the space between the last component and main-end, and the space between any two adjacent |

### ArkUI_FlexDirection

```c
enum ArkUI_FlexDirection
```

**Description**

Enumerates the directions of the main axis in the flex container.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_FLEX_DIRECTION_ROW = 0 | The child components are arranged in the same direction as the main axis runs along the rows. |
| ARKUI_FLEX_DIRECTION_COLUMN | The child components are arranged in the same direction as the main axis runs down the columns. |
| ARKUI_FLEX_DIRECTION_ROW_REVERSE | The child components are arranged opposite to the <b>ROW</b> direction. |
| ARKUI_FLEX_DIRECTION_COLUMN_REVERSE | The child components are arranged opposite to the <b>COLUMN</b> direction. |

### ArkUI_FlexWrap

```c
enum ArkUI_FlexWrap
```

**Description**

Defines whether the flex container has a single line or multiple lines.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_FLEX_WRAP_NO_WRAP = 0 | The child components in the flex container are arranged in a single line, and they cannot overflow. |
| ARKUI_FLEX_WRAP_WRAP | The child components in the flex container are arranged in multiple lines, and they may overflow. |
| ARKUI_FLEX_WRAP_WRAP_REVERSE | The child components in the flex container are reversely arranged in multiple lines, and they may overflow. |

### ArkUI_Direction

```c
enum ArkUI_Direction
```

**Description**

Enumerates the modes in which components are laid out along the main axis of the container.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_DIRECTION_LTR = 0 | Components are arranged from left to right. |
| ARKUI_DIRECTION_RTL | Components are arranged from right to left. |
| ARKUI_DIRECTION_AUTO = 3 | The default layout direction is used. |

### ArkUI_Axis

```c
enum ArkUI_Axis
```

**Description**

Enumerates the scroll directions for the <b><List></b> component.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_AXIS_VERTICAL = 0 | Only vertical scrolling is supported. |
| ARKUI_AXIS_HORIZONTAL | Only horizontal scrolling is supported. |

### ArkUI_VerticalAlignment

```c
enum ArkUI_VerticalAlignment
```

**Description**

Enumerates the vertical alignment modes.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_VERTICAL_ALIGNMENT_TOP = 0 | Top aligned. |
| ARKUI_VERTICAL_ALIGNMENT_CENTER | Center aligned. This is the default alignment mode. |
| ARKUI_VERTICAL_ALIGNMENT_BOTTOM | Bottom aligned. |

### ArkUI_HorizontalAlignment

```c
enum ArkUI_HorizontalAlignment
```

**Description**

Enumerates the alignment mode in the horizontal direction.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_HORIZONTAL_ALIGNMENT_START = 0 | Aligned with the start edge in the same direction as the language in use. |
| ARKUI_HORIZONTAL_ALIGNMENT_CENTER | Center aligned. This is the default alignment mode. |
| ARKUI_HORIZONTAL_ALIGNMENT_END | Aligned with the end edge in the same direction as the language in use. |

### ArkUI_SafeAreaEdge

```c
enum ArkUI_SafeAreaEdge
```

**Description**

defines the enumerated value of the direction of the extended security zone.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SAFE_AREA_EDGE_TOP = 1 | Upper area. |
| ARKUI_SAFE_AREA_EDGE_BOTTOM = 1 << 1 | Lower area. |
| ARKUI_SAFE_AREA_EDGE_START = 1 << 2 | Front area. |
| ARKUI_SAFE_AREA_EDGE_END = 1 << 3 | Tail area. |

### ArkUI_LayoutSafeAreaType

```c
enum ArkUI_LayoutSafeAreaType
```

**Description**

Define the types for expanding the safe area in layout.

**Since**: 23

| Enum item | Description |
| -- | -- |
| ARKUI_LAYOUT_SAFE_AREA_TYPE_SYSTEM = 1 | Default non-safe area of the system, including the status bar and navigation bar. |

### ArkUI_LayoutSafeAreaEdge

```c
enum ArkUI_LayoutSafeAreaEdge
```

**Description**

Define the edges for expanding the safe area in layout.

**Since**: 23

| Enum item | Description |
| -- | -- |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP = 1 | Top edge of the safe area. |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_BOTTOM = 1 << 1 | Bottom edge of the safe area. |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_START = 1 << 2 | Start edge of the safe area. |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_END = 1 << 3 | End edge of the safe area. |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_VERTICAL = ARKUI_LAYOUT_SAFE_AREA_EDGE_TOP \| ARKUI_LAYOUT_SAFE_AREA_EDGE_BOTTOM | Vertical edge of the safe area. |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_HORIZONTAL = ARKUI_LAYOUT_SAFE_AREA_EDGE_START \| ARKUI_LAYOUT_SAFE_AREA_EDGE_END | Horizontal edge of the safe area. |
| ARKUI_LAYOUT_SAFE_AREA_EDGE_ALL = ARKUI_LAYOUT_SAFE_AREA_EDGE_VERTICAL \| ARKUI_LAYOUT_SAFE_AREA_EDGE_HORIZONTAL | All edges of the safe area. |

### ArkUI_LocalizedAlignment

```c
enum ArkUI_LocalizedAlignment
```

**Description**

Enumerates the localizedAlignment modes.

**Since**: 23

| Enum item | Description |
| -- | -- |
| ARKUI_LOCALIZED_ALIGNMENT_TOP_START = 0 | Top start. |
| ARKUI_LOCALIZED_ALIGNMENT_TOP | Top center. |
| ARKUI_LOCALIZED_ALIGNMENT_TOP_END | Top end. |
| ARKUI_LOCALIZED_ALIGNMENT_START | Vertically centered start. |
| ARKUI_LOCALIZED_ALIGNMENT_CENTER | Horizontally and vertically centered. |
| ARKUI_LOCALIZED_ALIGNMENT_END | Vertically centered end. |
| ARKUI_LOCALIZED_ALIGNMENT_BOTTOM_START | Bottom start. |
| ARKUI_LOCALIZED_ALIGNMENT_BOTTOM | Horizontally centered on the bottom. |
| ARKUI_LOCALIZED_ALIGNMENT_BOTTOM_END | Bottom end. |

### ArkUI_LayoutPolicy

```c
enum ArkUI_LayoutPolicy
```

**Description**

Enumerates the LayoutPolicy.

**Since**: 21

| Enum item | Description |
| -- | -- |
| ARKUI_LAYOUTPOLICY_MATCHPARENT = 0 | The component fills its parent, which means its size is as large as its parent |
| ARKUI_LAYOUTPOLICY_WRAPCONTENT | The component fills its content, which means its size is as large as its children but it is constrained by its parent. |
| ARKUI_LAYOUTPOLICY_FIXATIDEALSIZE | The component fills its content which means its size is as large as its children. |

### ArkUI_PixelRoundCalcPolicy

```c
enum ArkUI_PixelRoundCalcPolicy
```

**Description**

Enumerates the PixelRoundPolicy.

**Since**: 21

| Enum item | Description |
| -- | -- |
| ARKUI_PIXELROUNDCALCPOLICY_NOFORCEROUND = 0 | No Force round the component boundary coordinates to integer pixel. |
| ARKUI_PIXELROUNDCALCPOLICY_FORCECEIL | Force ceil the component boundary coordinates to integer pixel. |
| ARKUI_PIXELROUNDCALCPOLICY_FORCEFLOOR | Force floor the component boundary coordinates to integer pixel. |


## Function description

### OH_ArkUI_GuidelineOption_Create()

```c
ArkUI_GuidelineOption* OH_ArkUI_GuidelineOption_Create(int32_t size)
```

**Description**

Create auxiliary line information in the RelativeContaine container.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t size | The number of auxiliary lines. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_GuidelineOption* | auxiliary line information. |

### OH_ArkUI_GuidelineOption_Dispose()

```c
void OH_ArkUI_GuidelineOption_Dispose(ArkUI_GuidelineOption* guideline)
```

**Description**

Destroy auxiliary line information.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |

### OH_ArkUI_GuidelineOption_SetId()

```c
void OH_ArkUI_GuidelineOption_SetId(ArkUI_GuidelineOption* guideline, const char* value, int32_t index)
```

**Description**

Set the Id of the auxiliary line.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| const char* value | id, must be unique and cannot have the same name as the component in the container. |
| int32_t index | auxiliary line index value. |

### OH_ArkUI_GuidelineOption_SetDirection()

```c
void OH_ArkUI_GuidelineOption_SetDirection(ArkUI_GuidelineOption* guideline, ArkUI_Axis value, int32_t index)
```

**Description**

Set the direction of the auxiliary line.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| [ArkUI_Axis](capi-layout-h.md#arkui_axis) value | direction. |
| int32_t index | auxiliary line index value. |

### OH_ArkUI_GuidelineOption_SetPositionStart()

```c
void OH_ArkUI_GuidelineOption_SetPositionStart(ArkUI_GuidelineOption* guideline, float value, int32_t index)
```

**Description**

Set the distance from the left or top of the container.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| float value | The distance from the left or top of the container. |
| int32_t index | auxiliary line index value. |

### OH_ArkUI_GuidelineOption_SetPositionEnd()

```c
void OH_ArkUI_GuidelineOption_SetPositionEnd(ArkUI_GuidelineOption* guideline, float value, int32_t index)
```

**Description**

Set the distance from the right or bottom of the container.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| float value | The distance from the right side or bottom of the container. |
| int32_t index | auxiliary line index value. |

### OH_ArkUI_GuidelineOption_GetId()

```c
const char* OH_ArkUI_GuidelineOption_GetId(ArkUI_GuidelineOption* guideline, int32_t index)
```

**Description**

Get the Id of the auxiliary line.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Id. |

### OH_ArkUI_GuidelineOption_GetDirection()

```c
ArkUI_Axis OH_ArkUI_GuidelineOption_GetDirection(ArkUI_GuidelineOption* guideline, int32_t index)
```

**Description**

Get the direction of the auxiliary line.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_Axis](capi-layout-h.md#arkui_axis) | direction. |

### OH_ArkUI_GuidelineOption_GetPositionStart()

```c
float OH_ArkUI_GuidelineOption_GetPositionStart(ArkUI_GuidelineOption* guideline, int32_t index)
```

**Description**

Get the distance from the left or top of the container.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**Returns**:

| Type | Description |
| -- | -- |
| float | The distance from the left or top of the container. |

### OH_ArkUI_GuidelineOption_GetPositionEnd()

```c
float OH_ArkUI_GuidelineOption_GetPositionEnd(ArkUI_GuidelineOption* guideline, int32_t index)
```

**Description**

Get the distance from the right side or bottom of the container.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_GuidelineOption* guideline | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**Returns**:

| Type | Description |
| -- | -- |
| float | The distance from the right side or bottom of the container. |

### OH_ArkUI_BarrierOption_Create()

```c
ArkUI_BarrierOption* OH_ArkUI_BarrierOption_Create(int32_t size)
```

**Description**

creates barrier information within the RelativeContaine container.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t size | Number of barriers. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_BarrierOption* | barrier information. |

### OH_ArkUI_BarrierOption_Dispose()

```c
void OH_ArkUI_BarrierOption_Dispose(ArkUI_BarrierOption* barrierStyle)
```

**Description**

Destroy barrier information.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | barrier information. |

### OH_ArkUI_BarrierOption_SetId()

```c
void OH_ArkUI_BarrierOption_SetId(ArkUI_BarrierOption* barrierStyle, const char* value, int32_t index)
```

**Description**

Set the Id of the barrier.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | barrier information. |
| const char* value | id, must be unique and cannot have the same name as the component in the container. |
| int32_t index | Barrier index value. |

### OH_ArkUI_BarrierOption_SetDirection()

```c
void OH_ArkUI_BarrierOption_SetDirection(ArkUI_BarrierOption* barrierStyle, ArkUI_BarrierDirection value, int32_t index)
```

**Description**

Set the direction of the barrier.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | barrier information. |
| ArkUI_BarrierDirection value | direction. |
| int32_t index | Barrier index value. |

### OH_ArkUI_BarrierOption_SetReferencedId()

```c
void OH_ArkUI_BarrierOption_SetReferencedId(ArkUI_BarrierOption* barrierStyle, const char* value, int32_t index)
```

**Description**

Sets the dependent component of the barrier.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | barrier information. |
| const char* value | The ID of the dependent component. |
| int32_t index | Barrier index value. |

### OH_ArkUI_BarrierOption_GetId()

```c
const char* OH_ArkUI_BarrierOption_GetId(ArkUI_BarrierOption* barrierStyle, int32_t index)
```

**Description**

Get the Id of the barrier.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | The Id of the barrier. |

### OH_ArkUI_BarrierOption_GetDirection()

```c
ArkUI_BarrierDirection OH_ArkUI_BarrierOption_GetDirection(ArkUI_BarrierOption* barrierStyle, int32_t index)
```

**Description**

Gets the direction of the barrier.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_BarrierDirection | The direction of the barrier. |

### OH_ArkUI_BarrierOption_GetReferencedId()

```c
const char* OH_ArkUI_BarrierOption_GetReferencedId(ArkUI_BarrierOption* barrierStyle, int32_t index, int32_t referencedIndex)
```

**Description**

Get the dependent components of the barrier.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | auxiliary line information. |
| int32_t index | auxiliary line index value. |
| int32_t referencedIndex | dependent component Id index value. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | The barrier's dependent components. |

### OH_ArkUI_BarrierOption_GetReferencedIdSize()

```c
int32_t OH_ArkUI_BarrierOption_GetReferencedIdSize(ArkUI_BarrierOption* barrierStyle, int32_t index)
```

**Description**

Gets the number of dependent components of the barrier.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_BarrierOption* barrierStyle | auxiliary line information. |
| int32_t index | auxiliary line index value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | The number of dependent components of the barrier. |

### OH_ArkUI_AlignmentRuleOption_Create()

```c
ArkUI_AlignmentRuleOption* OH_ArkUI_AlignmentRuleOption_Create()
```

**Description**

creates alignment rule information for subcomponents in relative containers.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* | Alignment rule information. |

### OH_ArkUI_AlignmentRuleOption_Dispose()

```c
void OH_ArkUI_AlignmentRuleOption_Dispose(ArkUI_AlignmentRuleOption* option)
```

**Description**

Destroys the alignment rule information of subcomponents in relative containers.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

### OH_ArkUI_AlignmentRuleOption_SetStart()

```c
void OH_ArkUI_AlignmentRuleOption_SetStart(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)
```

**Description**

Set the start alignment parameter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| const char* id | The id value of the anchor component. |
| [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment) alignment | Alignment relative to the anchor component. |

### OH_ArkUI_AlignmentRuleOption_SetEnd()

```c
void OH_ArkUI_AlignmentRuleOption_SetEnd(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)
```

**Description**

Set the end alignment parameter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| const char* id | The id value of the anchor component. |
| [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment) alignment | Alignment relative to the anchor component. |

### OH_ArkUI_AlignmentRuleOption_SetCenterHorizontal()

```c
void OH_ArkUI_AlignmentRuleOption_SetCenterHorizontal(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_HorizontalAlignment alignment)
```

**Description**

Set the parameters for horizontal center alignment.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| const char* id | The id value of the anchor component. |
| [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment) alignment | Alignment relative to anchor component |

### OH_ArkUI_AlignmentRuleOption_SetTop()

```c
void OH_ArkUI_AlignmentRuleOption_SetTop(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)
```

**Description**

Set the parameters for top alignment.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| const char* id | The id value of the anchor component. |
| [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment) alignment | Alignment relative to anchor component |

### OH_ArkUI_AlignmentRuleOption_SetBottom()

```c
void OH_ArkUI_AlignmentRuleOption_SetBottom(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)
```

**Description**

Set the bottom alignment parameters.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| const char* id | The id value of the anchor component. |
| [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment) alignment | Alignment relative to anchor component |

### OH_ArkUI_AlignmentRuleOption_SetCenterVertical()

```c
void OH_ArkUI_AlignmentRuleOption_SetCenterVertical(ArkUI_AlignmentRuleOption* option, const char* id, ArkUI_VerticalAlignment alignment)
```

**Description**

Set the parameters for vertical center alignment.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| const char* id | The id value of the anchor component. |
| [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment) alignment | Alignment relative to the anchor component. |

### OH_ArkUI_AlignmentRuleOption_SetBiasHorizontal()

```c
void OH_ArkUI_AlignmentRuleOption_SetBiasHorizontal(ArkUI_AlignmentRuleOption* option, float horizontal)
```

**Description**

Sets the horizontal offset parameter of the component under the anchor point constraint.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| float horizontal | bias value in the horizontal direction. |

### OH_ArkUI_AlignmentRuleOption_SetBiasVertical()

```c
void OH_ArkUI_AlignmentRuleOption_SetBiasVertical(ArkUI_AlignmentRuleOption* option, float vertical)
```

**Description**

Set the vertical offset parameter of the component under the anchor point constraint.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |
| float vertical | bias value in the vertical direction. |

### OH_ArkUI_AlignmentRuleOption_GetStartId()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetStartId(ArkUI_AlignmentRuleOption* option)
```

**Description**

Get the Id of the start-aligned parameter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | The id value of the anchor component. |

### OH_ArkUI_AlignmentRuleOption_GetStartAlignment()

```c
ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetStartAlignment(ArkUI_AlignmentRuleOption* option)
```

**Description**

Gets the alignment of the start-aligned parameter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment) | The alignment of the parameters. |

### OH_ArkUI_AlignmentRuleOption_GetEndId()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetEndId(ArkUI_AlignmentRuleOption* option)
```

**Description**

Get the end alignment parameter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | End-aligned parameter id. |

### OH_ArkUI_AlignmentRuleOption_GetEndAlignment()

```c
ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetEndAlignment(ArkUI_AlignmentRuleOption* option)
```

**Description**

Get the end alignment parameter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment) | The alignment of the end-aligned parameter. |

### OH_ArkUI_AlignmentRuleOption_GetCenterIdHorizontal()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdHorizontal(ArkUI_AlignmentRuleOption* option)
```

**Description**

Gets the parameters of horizontal center alignment.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | The id of the parameter of horizontal center alignment. |

### OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentHorizontal()

```c
ArkUI_HorizontalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentHorizontal(ArkUI_AlignmentRuleOption* option)
```

**Description**

Gets the parameters of horizontal center alignment.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_HorizontalAlignment](capi-layout-h.md#arkui_horizontalalignment) | The alignment of the horizontally centered alignment parameter. |

### OH_ArkUI_AlignmentRuleOption_GetTopId()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetTopId(ArkUI_AlignmentRuleOption* option)
```

**Description**

Get the top-aligned parameters.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Top aligned parameter id. |

### OH_ArkUI_AlignmentRuleOption_GetTopAlignment()

```c
ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetTopAlignment(ArkUI_AlignmentRuleOption* option)
```

**Description**

Get the top-aligned parameters.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment) | The alignment of the top-aligned parameter. |

### OH_ArkUI_AlignmentRuleOption_GetBottomId()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetBottomId(ArkUI_AlignmentRuleOption* option)
```

**Description**

Get the bottom alignment parameters.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | The id of the bottom-aligned parameter. |

### OH_ArkUI_AlignmentRuleOption_GetBottomAlignment()

```c
ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetBottomAlignment(ArkUI_AlignmentRuleOption* option)
```

**Description**

Get the bottom alignment parameters.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment) | The alignment of the bottom-aligned parameter. |

### OH_ArkUI_AlignmentRuleOption_GetCenterIdVertical()

```c
const char* OH_ArkUI_AlignmentRuleOption_GetCenterIdVertical(ArkUI_AlignmentRuleOption* option)
```

**Description**

Gets the parameters of vertical center alignment.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | The id of the vertical center alignment parameter. |

### OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentVertical()

```c
ArkUI_VerticalAlignment OH_ArkUI_AlignmentRuleOption_GetCenterAlignmentVertical(ArkUI_AlignmentRuleOption* option)
```

**Description**

Gets the parameters of vertical center alignment.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_VerticalAlignment](capi-layout-h.md#arkui_verticalalignment) | The alignment of the vertical center alignment parameter. |

### OH_ArkUI_AlignmentRuleOption_GetBiasHorizontal()

```c
float OH_ArkUI_AlignmentRuleOption_GetBiasHorizontal(ArkUI_AlignmentRuleOption* option)
```

**Description**

Get the bias value in the horizontal direction.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| float | The bias value in the horizontal direction. |

### OH_ArkUI_AlignmentRuleOption_GetBiasVertical()

```c
float OH_ArkUI_AlignmentRuleOption_GetBiasVertical(ArkUI_AlignmentRuleOption* option)
```

**Description**

Get the bias value in the vertical direction.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AlignmentRuleOption* option | Alignment rule information of subcomponents in the relative container. |

**Returns**:

| Type | Description |
| -- | -- |
| float | bias value in vertical direction. |

### OH_ArkUI_PositionEdges_Create()

```c
ArkUI_PositionEdges* OH_ArkUI_PositionEdges_Create()
```

**Description**

Create an edge object for position attribute.

**Since**: 21

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_PositionEdges*](capi-arkui-nativemodule-arkui-positionedges.md) | A pointer to the edge object. |

### OH_ArkUI_PositionEdges_Copy()

```c
ArkUI_PositionEdges* OH_ArkUI_PositionEdges_Copy(const ArkUI_PositionEdges* edges)
```

**Description**

Creates a deep copy of an edge object for position attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | A pointer to an edge object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_PositionEdges*](capi-arkui-nativemodule-arkui-positionedges.md) | A pointer to the new edge object. |

### OH_ArkUI_PositionEdges_Dispose()

```c
void OH_ArkUI_PositionEdges_Dispose(ArkUI_PositionEdges* edges)
```

**Description**

Dispose an edge object for position attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object to be disposed. |

### OH_ArkUI_PositionEdges_SetTop()

```c
void OH_ArkUI_PositionEdges_SetTop(ArkUI_PositionEdges* edges, float value)
```

**Description**

Sets the top edge of an edge object for position attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float value | The distance of top edge to the corresponding edge of parent container, in vp. |

### OH_ArkUI_PositionEdges_GetTop()

```c
int32_t OH_ArkUI_PositionEdges_GetTop(ArkUI_PositionEdges* edges, float* value)
```

**Description**

Gets the top edge of an edge object for position attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float* value | The distance of top edge to the corresponding edge of parent container, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.       Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>     Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if the parameter is invalid. |

### OH_ArkUI_PositionEdges_SetLeft()

```c
void OH_ArkUI_PositionEdges_SetLeft(ArkUI_PositionEdges* edges, float value)
```

**Description**

Sets the left edge of an edge object for position attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float value | The distance of left edge to the corresponding edge of parent container, in vp. |

### OH_ArkUI_PositionEdges_GetLeft()

```c
int32_t OH_ArkUI_PositionEdges_GetLeft(ArkUI_PositionEdges* edges, float* value)
```

**Description**

Gets the left edge of an edge object for position attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float* value | The distance of left edge to the corresponding edge of parent container, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.       Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>     Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if the parameter is invalid. |

### OH_ArkUI_PositionEdges_SetBottom()

```c
void OH_ArkUI_PositionEdges_SetBottom(ArkUI_PositionEdges* edges, float value)
```

**Description**

Sets the bottom edge of an edge object for position attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float value | The distance of bottom edge to the corresponding edge of parent container, in vp. |

### OH_ArkUI_PositionEdges_GetBottom()

```c
int32_t OH_ArkUI_PositionEdges_GetBottom(ArkUI_PositionEdges* edges, float* value)
```

**Description**

Gets the bottom edge of an edge object for position attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float* value | The distance of bottom edge to the corresponding edge of parent container, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.       Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>     Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if the parameter is invalid. |

### OH_ArkUI_PositionEdges_SetRight()

```c
void OH_ArkUI_PositionEdges_SetRight(ArkUI_PositionEdges* edges, float value)
```

**Description**

Sets the right edge of an edge object for position attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float value | The distance of right edge to the corresponding edge of parent container, in vp. |

### OH_ArkUI_PositionEdges_GetRight()

```c
int32_t OH_ArkUI_PositionEdges_GetRight(ArkUI_PositionEdges* edges, float* value)
```

**Description**

Gets the right edge of an edge object for position attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PositionEdges](capi-arkui-nativemodule-arkui-positionedges.md)* edges | Pointer to the edge object. |
| float* value | The distance of right edge to the corresponding edge of parent container, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.       Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>     Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if the parameter is invalid. |

### OH_ArkUI_PixelRoundPolicy_Create()

```c
ArkUI_PixelRoundPolicy* OH_ArkUI_PixelRoundPolicy_Create()
```

**Description**

Create a policy object for PixelRound attribute.

**Since**: 21

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_PixelRoundPolicy*](capi-arkui-nativemodule-arkui-pixelroundpolicy.md) | A pointer to the policy object. |

### OH_ArkUI_PixelRoundPolicy_Dispose()

```c
void OH_ArkUI_PixelRoundPolicy_Dispose(ArkUI_PixelRoundPolicy* policy)
```

**Description**

Dispose a policy object for PixelRound attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object to be disposed. |

### OH_ArkUI_PixelRoundPolicy_SetTop()

```c
void OH_ArkUI_PixelRoundPolicy_SetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)
```

**Description**

Sets the top edge of a policy object for PixelRound attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-layout-h.md#arkui_pixelroundcalcpolicy) value | The CalcPolicy of top edge. |

### OH_ArkUI_PixelRoundPolicy_GetTop()

```c
int32_t OH_ArkUI_PixelRoundPolicy_GetTop(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)
```

**Description**

Gets the top edge of a policy object for PixelRound attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-layout-h.md#arkui_pixelroundcalcpolicy)* value | The CalcPolicy of top edge. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.       Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>     Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if the parameter is invalid. |

### OH_ArkUI_PixelRoundPolicy_SetStart()

```c
void OH_ArkUI_PixelRoundPolicy_SetStart(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)
```

**Description**

Sets the start edge of a policy object for PixelRound attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-layout-h.md#arkui_pixelroundcalcpolicy) value | The CalcPolicy of start edge. |

### OH_ArkUI_PixelRoundPolicy_GetStart()

```c
int32_t OH_ArkUI_PixelRoundPolicy_GetStart(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)
```

**Description**

Gets the start edge of a policy object for PixelRound attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-layout-h.md#arkui_pixelroundcalcpolicy)* value | The CalcPolicy of start edge. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.       Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>     Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if the parameter is invalid. |

### OH_ArkUI_PixelRoundPolicy_SetBottom()

```c
void OH_ArkUI_PixelRoundPolicy_SetBottom(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)
```

**Description**

Sets the bottom edge of a policy object for PixelRound attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-layout-h.md#arkui_pixelroundcalcpolicy) value | The CalcPolicy of bottom edge. |

### OH_ArkUI_PixelRoundPolicy_GetBottom()

```c
int32_t OH_ArkUI_PixelRoundPolicy_GetBottom(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)
```

**Description**

Gets the bottom edge of a policy object for PixelRound attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-layout-h.md#arkui_pixelroundcalcpolicy)* value | The CalcPolicy of bottom edge. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.       Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>     Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if the parameter is invalid. |

### OH_ArkUI_PixelRoundPolicy_SetEnd()

```c
void OH_ArkUI_PixelRoundPolicy_SetEnd(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy value)
```

**Description**

Sets the end edge of a policy object for PixelRound attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-layout-h.md#arkui_pixelroundcalcpolicy) value | The CalcPolicy of end edge. |

### OH_ArkUI_PixelRoundPolicy_GetEnd()

```c
int32_t OH_ArkUI_PixelRoundPolicy_GetEnd(ArkUI_PixelRoundPolicy* policy, ArkUI_PixelRoundCalcPolicy* value)
```

**Description**

Gets the end edge of a policy object for PixelRound attribute.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PixelRoundPolicy](capi-arkui-nativemodule-arkui-pixelroundpolicy.md)* policy | Pointer to the policy object. |
| [ArkUI_PixelRoundCalcPolicy](capi-layout-h.md#arkui_pixelroundcalcpolicy)* value | The CalcPolicy of end edge. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.       Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>     Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if the parameter is invalid. |


