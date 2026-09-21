# Panel properties/events

```TypeScript
declare class PanelAttribute extends CommonMethod<PanelAttribute>
```

Pane Attribute.

**Inheritance/Implementation:** PanelAttribute extends CommonMethod<PanelAttribute>

**Since:** 7

**Deprecated since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundMask

```TypeScript
backgroundMask(color: ResourceColor)
```

Called when the panel background mask is requested.

**Since:** 9

**Deprecated since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes |  |

## customHeight

```TypeScript
customHeight(value: Dimension | PanelHeight)
```

Sets the height. It is valid only when PanelType is set to Custom.

**Since:** 10

**Deprecated since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; [PanelHeight](arkts-arkui-panel-comp-panelheight-e.md) | Yes | value - Content height to set. |

## dragBar

```TypeScript
dragBar(value: boolean)
```

Called when determining whether dragbar exists.

**Since:** 7

**Deprecated since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes |  |

## fullHeight

```TypeScript
fullHeight(value: number | string)
```

Called when the height in the full state is specified.

**Since:** 7

**Deprecated since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes |  |

## halfHeight

```TypeScript
halfHeight(value: number | string)
```

Called when the height in the half state is specified.

**Since:** 7

**Deprecated since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes |  |

## miniHeight

```TypeScript
miniHeight(value: number | string)
```

Called when the height in the mini state is specified.

**Since:** 7

**Deprecated since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes |  |

## mode

```TypeScript
mode(value: PanelMode)
```

Called when the initial state of the slidable panel is set.

**Since:** 7

**Deprecated since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PanelMode](arkts-arkui-panel-comp-panelmode-e.md) | Yes |  |

## onChange

```TypeScript
onChange(
    event: (
    /**
     * Width of content area.
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @FaAndStageModel
     * @atomicservice
     * @since 7 dynamiconly
     * @deprecated since 12
     */
      width: number,

    /**
     * Height of content area.
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @FaAndStageModel
     * @atomicservice
     * @since 7 dynamiconly
     * @deprecated since 12
     */
      height: number,

    /**
     * Initial state.
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @FaAndStageModel
     * @atomicservice
     * @since 7 dynamiconly
     * @deprecated since 12
     */
      mode: PanelMode,
    ) => void,
  )
```

Called when the state of the slidable panel changes.

**Since:** 7

**Deprecated since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (     /**      * Width of content area.      *      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @FaAndStageModel      * @atomicservice      * @since 7 dynamiconly      * @deprecated since 12      */       width: number,      /**      * Height of content area.      *      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @FaAndStageModel      * @atomicservice      * @since 7 dynamiconly      * @deprecated since 12      */       height: number,      /**      * Initial state.      *      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @FaAndStageModel      * @atomicservice      * @since 7 dynamiconly      * @deprecated since 12      */       mode: PanelMode,     ) =&gt; void | Yes |  |

## onHeightChange

```TypeScript
onHeightChange(callback: (value: number) => void)
```

Called when height of the panel is changed

**Since:** 9

**Deprecated since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: number) =&gt; void | Yes |  |

## show

```TypeScript
show(value: boolean)
```

Called when the panel slidable panel pops up.

**Since:** 7

**Deprecated since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes |  |

## showCloseIcon

```TypeScript
showCloseIcon(value: boolean)
```

Called when the panel show close icon.

**Since:** 10

**Deprecated since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | used to set whether to display the close icon. |

## type

```TypeScript
type(value: PanelType)
```

Called when the slidable panel type is set.

**Since:** 7

**Deprecated since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PanelType](arkts-arkui-panel-comp-paneltype-e.md) | Yes |  |
