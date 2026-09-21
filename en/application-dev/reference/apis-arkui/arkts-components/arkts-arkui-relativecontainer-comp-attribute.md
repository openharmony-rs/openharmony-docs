# RelativeContainer properties/events

```TypeScript
declare class RelativeContainerAttribute extends CommonMethod<RelativeContainerAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported.

> **NOTE:** 
> 
> The **margin** attribute of a child component in **RelativeContainer** has special effective conditions. For
> details, see the description above.

The [universal events](arkts-arkui-common-comp-commonmethod-c.md) are supported.

**Inheritance/Implementation:** RelativeContainerAttribute extends CommonMethod<RelativeContainerAttribute>

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## barrier

```TypeScript
barrier(value: Array<BarrierStyle>)
```

Sets the [barriers](../../../ui/arkts-layout-development-relative-layout.md#setting-barriers-for-multiple-components) in the **RelativeContainer** component. Child components can use barriers as anchors for alignment and positioning. Each element in the array represents a barrier. Typical usage scenarios: preventing child components from overlapping, creating virtual boundaries based on component edges, and implementing automatic spacing between components.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[BarrierStyle](arkts-arkui-relativecontainer-comp-barrierstyle-i.md)&gt; | Yes | Barrier in the **RelativeContainer** container, used to define the ID, direction, and dependent components of the barrier. Child components can use the barrier as an anchor for alignment and positioning. |

<a id="barrier-1"></a>

## barrier

```TypeScript
barrier(barrierStyle: Array<LocalizedBarrierStyle>)
```

Sets barriers in the **RelativeContainer**. Child components can use a barrier as an anchor for alignment and positioning, and barrier lines in mirror mode are supported. Each element in the array represents a barrier. Typical usage: RTL language layout adaptation, mirrored UI design, and automatic adjustment of barrier positions based on the reading direction.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| barrierStyle | Array&lt;[LocalizedBarrierStyle](arkts-arkui-relativecontainer-comp-localizedbarrierstyle-i.md)&gt; | Yes | Barrier in the **RelativeContainer** container, which supports defining barrier lines in mirror mode. |

## guideLine

```TypeScript
guideLine(value: Array<GuideLineStyle>)
```

Sets the [guidelines](../../../ui/arkts-layout-development-relative-layout.md#positioning-child-components-using-guidelines) in the **RelativeContainer** component. Each element in the array represents a guideline. Typical usage aligning child components based on virtual reference lines, creating flexibly adjustable reference lines for positioning, and laying out multiple child components based on the same baseline.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[GuideLineStyle](arkts-arkui-relativecontainer-comp-guidelinestyle-i.md)&gt; | Yes | Guideline inside the **RelativeContainer**, which defines the ID, direction, and position of the **guideLine** and is used to assist in positioning child components. |
