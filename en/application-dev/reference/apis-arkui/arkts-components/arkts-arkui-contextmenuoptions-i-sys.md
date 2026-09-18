# ContextMenuOptions

Configures menu item information.

**Table 1: Menu offset when both offset and placement are set**

| Value of placement | Menu Offset |  
| ------------------------------------------------------------ | ------------------------------------------------------------ |  
| Placement.TopLeft, Placement.Top, or Placement.TopRight | If the value of **x** is a positive number for **offset**, the menu shifts to the right relative to the component. If the value of **y** is a positive number, the menu shifts upward relative to the component.|
| Placement.BottomLeft, Placement.Bottom, or Placement.BottomRight| If the value of **x** is a positive number for **offset**, the menu shifts to the left relative to the component. If the value of **y** is a positive number, the menu shifts downward relative to the component.|
| Placement.RightTop, Placement.Right, or Placement.RightBottom | If the value of **x** is a positive number for **offset**, the menu shifts to the right relative to the component. If the value of **y** is a positive number, the menu shifts downward relative to the component.|

**Table 2: Default position of the menu arrow when both arrowOffset and placement are set**

| Value of placement | Menu Arrow Position |  
| ------------------------------------------- | ------------------------------------------------------------ |  
| Placement.Top or Placement.Bottom | The arrow is displayed horizontally and centered by default, with a distance from the left edge of the menu equal to the arrow's safe distance.|
| Placement.Left or Placement.Right | The arrow is displayed vertically and centered by default, with a distance from the top edge of the menu equal to the arrow's safe distance.|
| Placement.TopLeft or Placement.BottomLeft | The arrow is displayed horizontally by default, with a distance from the left edge of the menu equal to the arrow's safe distance.|
| Placement.TopRight or Placement.BottomRight | The arrow is displayed horizontally by default, with a distance from the right edge of the menu equal to the arrow's safe distance. |
| Placement.LeftTop or Placement.RightTop | The arrow is displayed vertically by default, with a distance from the top edge of the menu equal to the arrow's safe distance. |
| Placement.LeftBottom or Placement.RightBottom| The arrow is displayed vertically by default, with a distance from the bottom edge of the menu equal to the arrow's safe distance. |

**Table 3 Default menu position when enableArrow is set to true and placement is not set or set to an invalid value**

| API| Default Menu Position|  
|------|-------------|  
| [bindMenu](arkts-arkui-commonmethod-c.md#bindmenu) | [Placement.BottomLeft](../arkts-apis/arkts-arkui-placement-e.md) |
| [bindMenu&lt;sup&gt;11+&lt;/sup&gt;](arkts-arkui-commonmethod-c.md#bindmenu) | [Placement.BottomLeft](../arkts-apis/arkts-arkui-placement-e.md) |
| [bindContextMenu&lt;sup&gt;8+&lt;/sup&gt;](arkts-arkui-commonmethod-c.md#bindcontextmenu) | Placement.Top |
| [bindContextMenu&lt;sup&gt;12+&lt;/sup&gt;](arkts-arkui-commonmethod-c.md#bindcontextmenu) | [Placement.BottomLeft](../arkts-apis/arkts-arkui-placement-e.md) |
| [bindContextMenuWithResponse&lt;sup&gt;23+&lt;/sup&gt;](arkts-arkui-commonmethod-c.md#bindcontextmenuwithresponse) | Placement.Top |

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

Sets the distortion animation Mode of the menu.

**Type:** [DistortionMode](arkts-arkui-distortionmode-e-sys.md)

**Default:** DistortionMode.DISTORTION_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

Sets the edgeLight animation Mode of the menu.

**Type:** [EdgeLightMode](arkts-arkui-edgelightmode-e-sys.md)

**Default:** EdgeLightMode.EDGELIGHT_DISABLED

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
