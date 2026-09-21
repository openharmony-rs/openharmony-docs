# WaterFlowSections

```TypeScript
declare class WaterFlowSections
```

Describes the water flow item sections.

> **NOTE:** 
> 
> After the section information is modified using **splice**, **push**, and **update**, ensure that the total number
> of child nodes in all sections matches the actual total number of child nodes in the **WaterFlow** component. Any
> failure to do so may result in layout issues that prevent the **WaterFlow** component from scrolling properly.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create a **WaterFlowSections** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## length

```TypeScript
length(): number
```

Obtains the number of sections in the **WaterFlow** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of sections in the **WaterFlow** component. |

## push

```TypeScript
push(section: SectionOptions): boolean
```

Adds the specified sections to the end of the **WaterFlow** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| section | [SectionOptions](arkts-arkui-waterflow-comp-sectionoptions-c.md) | Yes | Sections to add to the end of the **WaterFlow** component. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the section is successfully added; returns **false** if the addition fails (**itemsCount** of the new section is not a non-negative number). |

## splice

```TypeScript
splice(start: number, deleteCount?: number, sections?: Array<SectionOptions>): boolean
```

Changes sections by removing or replacing an existing section and/or adding a section.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Zero-based index at which the changing starts. The value is converted to an integer.<br> **NOTE:** <br>1. A negative index counts back from the end of the section list. **start + WaterFlowSections.length()** is used.<br>2. If **start** &lt; -**WaterFlowSections.length()**, **0** is used.<br>3. If **start** &gt;= **WaterFlowSections.length()**, a new section is added at the end. |
| deleteCount | number | No | Number of sections to be deleted from the position specified by **start**.<br> **NOTE:** <br>1. If **deleteCount** is omitted, or if its value is greater than or equal to the number of sections from the position specified by **start** to the end of the **WaterFlowSections**, then all sections from the position specified by **start** to the end of the **WaterFlowSections** will be deleted.<br>2. If **deleteCount** is **0** or a negative number, no sections are deleted. |
| sections | Array&lt;[SectionOptions](arkts-arkui-waterflow-comp-sectionoptions-c.md)&gt; | No | Sections to add to the section list, beginning from the position specified by **start**. If no section is specified, **splice()** will only delete sections from the **WaterFlow** component. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the sections are successfully modified and returns **false** if the modification fails (**itemsCount** of any section to be added is not a non-negative number). |

## update

```TypeScript
update(sectionIndex:number, section: SectionOptions): boolean
```

Updates the configuration of a specified water flow item section.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sectionIndex | number | Yes | Zero-based index of the water flow item section to update. The value is converted to an integer.<br>**NOTE:** <br>1. A negative index counts back from the end of the section list. **sectionIndex + WaterFlowSections.length()** is used.<br>2. If **sectionIndex** &lt; - **WaterFlowSections.length()**, **0** is used.<br>3. If **sectionIndex** &gt;= **WaterFlowSections.length()**, a new section is added at the end. |
| section | [SectionOptions](arkts-arkui-waterflow-comp-sectionoptions-c.md) | Yes | New section configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns whether the update is successful. If the value of **itemsCount** in any section to add is not a non-negative integer, **false** is returned. |

## values

```TypeScript
values(): Array<SectionOptions>
```

Obtains the configuration of all sections in the **WaterFlow** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[SectionOptions](arkts-arkui-waterflow-comp-sectionoptions-c.md)&gt; | Configuration of all sections in the **WaterFlow** component. |
