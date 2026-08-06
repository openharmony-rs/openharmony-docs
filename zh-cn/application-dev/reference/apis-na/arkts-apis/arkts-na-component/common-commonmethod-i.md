# CommonMethod

CommonMethod

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface CommonMethod--><!--Device-unnamed-export declare interface CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityActionOptions

```TypeScript
default accessibilityActionOptions(option: AccessibilityActionOptions | undefined): this
```

Sets AccessibilityActionOptions that can affect operation under accessibility.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityActionOptions(option: AccessibilityActionOptions | undefined): this--><!--Device-CommonMethod-default accessibilityActionOptions(option: AccessibilityActionOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | set accessibility specific operation options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return component instance who call the method. |

## accessibilityChecked

```TypeScript
default accessibilityChecked(isCheck: boolean | undefined): this
```

Sets accessibilityChecked

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityChecked(isCheck: boolean | undefined): this--><!--Device-CommonMethod-default accessibilityChecked(isCheck: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isCheck | boolean \| undefined | 是 | set accessibility checked status |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilityCustomActions

```TypeScript
default accessibilityCustomActions(actions: Array<AccessibilityCustomAction> | undefined): this
```

Sets AccessibilityCustomActions that can be processed in custom action processing under accessibility.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityCustomActions(actions: Array<AccessibilityCustomAction> | undefined): this--><!--Device-CommonMethod-default accessibilityCustomActions(actions: Array<AccessibilityCustomAction> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actions | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| undefined | 是 | set accessibility custom action. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return component instance who call method. |

## accessibilityDefaultFocus

```TypeScript
default accessibilityDefaultFocus(focus: boolean | undefined): this
```

Sets the accessibility default foucs flag

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityDefaultFocus(focus: boolean | undefined): this--><!--Device-CommonMethod-default accessibilityDefaultFocus(focus: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| focus | boolean \| undefined | 是 | if the component is accessibility default focus,focus set true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilityDescription

```TypeScript
default accessibilityDescription(description: Resource | string | undefined): this
```

Sets accessibilityDescription with support for resource references using Resource. This property provides additional context or explanation for the component, helping users understand the action or function it performs. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_: \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_Reference resource of the accessibility description. You can specify further explanation \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_of the current component, for example, possible operation consequences, especially those that \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_cannot be learned from component attributes and accessibility text. If a component contains \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_both text information and the accessibility description, the text is read first and then the \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_accessibility description, when the component is selected.\_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityDescription(description: Resource | string | undefined): this--><!--Device-CommonMethod-default accessibilityDescription(description: Resource | string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| description | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| string \| undefined | 是 | set description of accessibility, default value is "". |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilityFocusDrawLevel

```TypeScript
default accessibilityFocusDrawLevel(drawLevel: FocusDrawLevel | undefined): this
```

Accessibility focus draw level, and the default value is FocusDrawLevel.SELF.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityFocusDrawLevel(drawLevel: FocusDrawLevel | undefined): this--><!--Device-CommonMethod-default accessibilityFocusDrawLevel(drawLevel: FocusDrawLevel | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawLevel | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | indicates accessibility focus draw level. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilityGroup

```TypeScript
default accessibilityGroup(isGroup: boolean | undefined, accessibilityOptions?: AccessibilityOptions): this
```

Sets whether to enable accessibility grouping. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_Whether to enable accessibility grouping. When accessibility grouping is enabled, \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_the component and all its children are treated as a single selectable unit, and the accessibility \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_service will no longer focus on the individual child components. \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_If accessibility grouping is enabled and the component does not contain a universal text attribute \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_or an accessibility text attribute, the system will concatenate the universal text attributes of \_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_its child components to form a merged text for the component. If a child component lacks a universal \_\_\_HTML\_TAG\_DESC\_USD\_9\_\_\_text attribute, it will be ignored in the concatenation process. \_\_\_HTML\_TAG\_DESC\_USD\_10\_\_\_When accessibilityPreferred is set to true, the system will prioritize concatenating the accessibility \_\_\_HTML\_TAG\_DESC\_USD\_11\_\_\_text attributes of the child components to form the merged text. If a child component lacks an \_\_\_HTML\_TAG\_DESC\_USD\_12\_\_\_accessibility text attribute, the system will continue to concatenate its universal text attribute. \_\_\_HTML\_TAG\_DESC\_USD\_13\_\_\_If a child component lacks both, it will be ignored.\_\_\_HTML\_TAG\_DESC\_USD\_14\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityGroup(isGroup: boolean | undefined, accessibilityOptions?: AccessibilityOptions): this--><!--Device-CommonMethod-default accessibilityGroup(isGroup: boolean | undefined, accessibilityOptions?: AccessibilityOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isGroup | boolean \| undefined | 是 | set group with accessibility, default value is false. |
| accessibilityOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | options for accessibility, default value is false. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilityLevel

```TypeScript
default accessibilityLevel(value: string | undefined): this
```

Sets the accessibility level. This property determines whether the component can be recognized by accessibility services. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ Accessibility level, which is used to decide whether a component can be identified by the accessibility service. \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_The options are as follows: \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_"auto": The component's recognizability is determined by the accessibility grouping service and ArkUI. \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_"yes": The component can be recognized by accessibility services. \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_"no": The component cannot be recognized by accessibility services. \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_"no-hide-descendants": Neither the component nor its child components can be recognized by accessibility services. \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_When accessibilityLevel is set to "auto", the component's recognizability depends on the following factors: \_\_\_HTML\_TAG\_DESC\_USD\_9\_\_\_1. The accessibility service internally determines whether the component can be recognized. \_\_\_HTML\_TAG\_DESC\_USD\_10\_\_\_2. If the parent component's accessibilityGroup property has isGroup set to true, the accessibility service will \_\_\_HTML\_TAG\_DESC\_USD\_11\_\_\_not focus on its child components, making them unrecognizable. \_\_\_HTML\_TAG\_DESC\_USD\_12\_\_\_3. If the parent component's accessibilityLevel is set to "no-hide-descendants", the component will not be \_\_\_HTML\_TAG\_DESC\_USD\_13\_\_\_recognized by accessibility services.\_\_\_HTML\_TAG\_DESC\_USD\_14\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityLevel(value: string | undefined): this--><!--Device-CommonMethod-default accessibilityLevel(value: string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| undefined | 是 | set accessibility level, default value is auto. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilityNextFocusId

```TypeScript
default accessibilityNextFocusId(nextId: string | undefined): this
```

Sets accessibility next focus id

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityNextFocusId(nextId: string | undefined): this--><!--Device-CommonMethod-default accessibilityNextFocusId(nextId: string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| nextId | string \| undefined | 是 | set component next accessibility focus id |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilityNextFocusId

```TypeScript
default accessibilityNextFocusId(nextId: string, nextFocusParams: AccessibilityNextFocusParams | undefined): this
```

Sets the next accessibility focus ID for the component, with optional detailed parameters. The detailed parameters can provide additional behavior for the accessibility focus transition.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityNextFocusId(nextId: string, nextFocusParams: AccessibilityNextFocusParams | undefined): this--><!--Device-CommonMethod-default accessibilityNextFocusId(nextId: string, nextFocusParams: AccessibilityNextFocusParams | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| nextId | string | 是 | set component next accessibility focus id. |
| nextFocusParams | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | the detailed parameters for accessibility next focus processing.Undefined indicates reverting to the default of the detailed parameters. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return component instance who call the method. |

## accessibilityRole

```TypeScript
default accessibilityRole(role: AccessibilityRoleType | undefined): this
```

Sets accessibility role,role indicates the custom type of the component

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityRole(role: AccessibilityRoleType | undefined): this--><!--Device-CommonMethod-default accessibilityRole(role: AccessibilityRoleType | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| role | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | set accessibility component type |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilityScrollTriggerable

```TypeScript
default accessibilityScrollTriggerable(isTriggerable: boolean | undefined): this
```

Sets accessibilityScrollTriggerable

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityScrollTriggerable(isTriggerable: boolean | undefined): this--><!--Device-CommonMethod-default accessibilityScrollTriggerable(isTriggerable: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isTriggerable | boolean \| undefined | 是 | set property of supporting scroll in accessibility |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilitySelected

```TypeScript
default accessibilitySelected(isSelect: boolean | undefined): this
```

Sets accessibilitySelected

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilitySelected(isSelect: boolean | undefined): this--><!--Device-CommonMethod-default accessibilitySelected(isSelect: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSelect | boolean \| undefined | 是 | set accessibility selected status |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilityStateDescription

```TypeScript
default accessibilityStateDescription(description: string | Resource | undefined): this
```

Sets the state anouncement text of the component under accessibility.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityStateDescription(description: string | Resource | undefined): this--><!--Device-CommonMethod-default accessibilityStateDescription(description: string | Resource | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| description | string \| Resource \| undefined | 是 | the state anouncement text of the component under accessibility. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return component instance who call the method. |

## accessibilityText

```TypeScript
default accessibilityText(text: Resource | string | undefined): this
```

Sets the accessibility text. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_When a component does not contain a text attribute, you can use this API to set an accessibility \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_text attribute, so that accessibility services can announce the specified content for the component. \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_If a component has both text content and accessibility text, only the accessibility text is announced. \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_If a component is grouped for accessibility purposes but lacks both text content and accessibility \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_text, the screen reader will concatenate text from its child components (depth-first traversal). \_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_To prioritize accessibility text concatenation, set accessibilityPreferred in accessibilityGroup. \_\_\_HTML\_TAG\_DESC\_USD\_9\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityText(text: Resource | string | undefined): this--><!--Device-CommonMethod-default accessibilityText(text: Resource | string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| string \| undefined | 是 | set accessibility text, default value is "". |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilityTextHint

```TypeScript
default accessibilityTextHint(value: string | undefined): this
```

Sets accessibilityTextHint

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityTextHint(value: string | undefined): this--><!--Device-CommonMethod-default accessibilityTextHint(value: string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| undefined | 是 | set accessibility text hint |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilityUseSamePage

```TypeScript
default accessibilityUseSamePage(pageMode: AccessibilitySamePageMode | undefined): this
```

Sets accessibility same page mode

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityUseSamePage(pageMode: AccessibilitySamePageMode | undefined): this--><!--Device-CommonMethod-default accessibilityUseSamePage(pageMode: AccessibilitySamePageMode | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pageMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | accessibility same page mode |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## accessibilityVirtualNode

```TypeScript
default accessibilityVirtualNode(builder: CustomBuilder | undefined): this
```

Sets accessibilityVirtualNode

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default accessibilityVirtualNode(builder: CustomBuilder | undefined): this--><!--Device-CommonMethod-default accessibilityVirtualNode(builder: CustomBuilder | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | set virtual node of accessibility |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## align

```TypeScript
default align(alignment: Alignment | LocalizedAlignment | undefined): this
```

Sets the alignment mode of the component content in the drawing area. Default value: **Alignment.Center**.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default align(alignment: Alignment | LocalizedAlignment | undefined): this--><!--Device-CommonMethod-default align(alignment: Alignment | LocalizedAlignment | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignment | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| LocalizedAlignment \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## alignRules

```TypeScript
default alignRules(value: AlignRuleOption | LocalizedAlignRuleOptions | undefined): this
```

Sets the alignment rules in the relative container. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_This API is valid only when the container is RelativeContainer. \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_LocalizedAlignRuleOptions takes the right-to-left scripts into account, using start and end instead of left and right for alignment in the horizontal direction. Prioritize this API in aligning child components in the relative container.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default alignRules(value: AlignRuleOption | LocalizedAlignRuleOptions | undefined): this--><!--Device-CommonMethod-default alignRules(value: AlignRuleOption | LocalizedAlignRuleOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| LocalizedAlignRuleOptions \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## alignSelf

```TypeScript
default alignSelf(value: ItemAlign | undefined): this
```

Sets the alignment mode of the child components along the cross axis of the parent container. Default value: **ItemAlign.Auto**.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default alignSelf(value: ItemAlign | undefined): this--><!--Device-CommonMethod-default alignSelf(value: ItemAlign | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## allowDrop

```TypeScript
default allowDrop(value: Array<UniformDataType> | null | Array<string> | undefined): this
```

Allowed drop uniformData type for this node.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default allowDrop(value: Array<UniformDataType> | null | Array<string> | undefined): this--><!--Device-CommonMethod-default allowDrop(value: Array<UniformDataType> | null | Array<string> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| null \| Array&lt;string&gt; \| undefined | 是 | the uniformData type for this node. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | - return the component attribute. |

## animation

```TypeScript
default animation(value: AnimateParam | undefined): this
```

animation

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default animation(value: AnimateParam | undefined): this--><!--Device-CommonMethod-default animation(value: AnimateParam | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## aspectRatio

```TypeScript
default aspectRatio(value: double | undefined): this
```

Sets the aspect ratio of the component, which can be obtained using the following formula: width/height. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_If only width and aspectRatio are set, the height is calculated using the following formula: width/aspectRatio. \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_If only height and aspectRatio are set, the width is calculated using the following formula: height x aspectRatio. \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_If width, height, and aspectRatio are all set, the explicitly set height is ignored, and the effective height is calculated using the following formula: width/aspectRatio. \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_This parameter takes effect only when a valid value greater than 0 is specified.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default aspectRatio(value: double | undefined): this--><!--Device-CommonMethod-default aspectRatio(value: double | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backdropBlur

```TypeScript
default backdropBlur(radius: double | undefined, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): this
```

为组件添加背景模糊效果，支持自定义设置模糊半径和灰阶参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default backdropBlur(radius: double | undefined, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): this--><!--Device-CommonMethod-default backdropBlur(radius: double | undefined, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | double \| undefined | 是 | 为当前组件添加背景模糊效果，入参为模糊半径，模糊半径越大越模糊，为0时不模糊。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当radius的值为undefined时，恢复为默认无模糊的背景。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 灰阶模糊参数。对图像中的黑白色进行色阶调整，使其趋于灰色更为柔和美观，对图像中的彩色调整没有效果。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：grayscale: [0,0] |
| sysOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 系统自适应调节参数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：{ disableSystemAdaptation: false } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## background

```TypeScript
default background(content: CustomBuilder | ResourceColor | undefined, options?: BackgroundOptions): this
```

Set the background to a given CustomBuilder, or set it to a specific ResourceColor.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default background(content: CustomBuilder | ResourceColor | undefined, options?: BackgroundOptions): this--><!--Device-CommonMethod-default background(content: CustomBuilder | ResourceColor | undefined, options?: BackgroundOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceColor \| undefined | 是 |  |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backgroundBlurStyle

```TypeScript
default backgroundBlurStyle(style: BlurStyle | undefined, options?: BackgroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): this
```

为当前组件提供一种背景材质模糊能力，通过枚举值的方式封装了不同的模糊半径、蒙版颜色、蒙版透明度、饱和度、亮度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default backgroundBlurStyle(style: BlurStyle | undefined, options?: BackgroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): this--><!--Device-CommonMethod-default backgroundBlurStyle(style: BlurStyle | undefined, options?: BackgroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 背景模糊样式。模糊样式中封装了模糊半径、蒙版颜色、蒙版透明度、饱和度、亮度五个参数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当style的值为undefined时，恢复为默认关闭模糊的背景。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 背景模糊选项。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_该参数在ArkTS卡片中，暂不支持使用。 |
| sysOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 系统自适应调节参数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：{ disableSystemAdaptation: false } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backgroundBrightness

```TypeScript
default backgroundBrightness(params: BackgroundBrightnessOptions | undefined): this
```

设置组件背景提亮效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default backgroundBrightness(params: BackgroundBrightnessOptions | undefined): this--><!--Device-CommonMethod-default backgroundBrightness(params: BackgroundBrightnessOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 设置组件背景提亮效果，包括：亮度变化速率，提亮程度。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当params的值为undefined时，恢复为无提亮效果的背景。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backgroundColor

```TypeScript
default backgroundColor(value: ResourceColor | ColorMetrics | undefined): this
```

Background color

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default backgroundColor(value: ResourceColor | ColorMetrics | undefined): this--><!--Device-CommonMethod-default backgroundColor(value: ResourceColor | ColorMetrics | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ColorMetrics \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backgroundEffect

```TypeScript
default backgroundEffect(options: BackgroundEffectOptions | undefined, sysOptions?: SystemAdaptiveOptions): this
```

设置组件背景属性，包括背景模糊半径、亮度、饱和度和颜色等参数。 > **说明：** > > backgroundEffect接口为实时接口，每帧对模糊等效果执行实时渲染，性能负载较大。当组件背景模糊效果无需变动时，推荐采用静态模糊接口 > [blur]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_实现模糊效果。最佳实践请参考： > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default backgroundEffect(options: BackgroundEffectOptions | undefined, sysOptions?: SystemAdaptiveOptions): this--><!--Device-CommonMethod-default backgroundEffect(options: BackgroundEffectOptions | undefined, sysOptions?: SystemAdaptiveOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 设置组件背景属性包括：饱和度，亮度，颜色。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当options的值为undefined时，恢复为无效果的背景。 |
| sysOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backgroundFilter

```TypeScript
default backgroundFilter(filter: Filter | undefined): this
```

设置背景滤镜视觉效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default backgroundFilter(filter: Filter | undefined): this--><!--Device-CommonMethod-default backgroundFilter(filter: Filter | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 背景滤镜视觉效果。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当filter的值为undefined时，无背景滤镜视觉效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## backgroundImage

```TypeScript
default backgroundImage(src: ResourceStr | PixelMap | undefined): this
```

Background image

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default backgroundImage(src: ResourceStr | PixelMap | undefined): this--><!--Device-CommonMethod-default backgroundImage(src: ResourceStr | PixelMap | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| PixelMap \| undefined | 是 | the background image source |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backgroundImage

```TypeScript
default backgroundImage(src: ResourceStr | PixelMap | undefined, options: BackgroundImageOptions): this
```

Background image

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default backgroundImage(src: ResourceStr | PixelMap | undefined, options: BackgroundImageOptions): this--><!--Device-CommonMethod-default backgroundImage(src: ResourceStr | PixelMap | undefined, options: BackgroundImageOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| PixelMap \| undefined | 是 | the background image source |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | config the options |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backgroundImage

```TypeScript
default backgroundImage(src: ResourceStr | PixelMap | undefined, repeat: ImageRepeat): this
```

Background image src:Image address url

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default backgroundImage(src: ResourceStr | PixelMap | undefined, repeat: ImageRepeat): this--><!--Device-CommonMethod-default backgroundImage(src: ResourceStr | PixelMap | undefined, repeat: ImageRepeat): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| PixelMap \| undefined | 是 |  |
| repeat | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backgroundImagePosition

```TypeScript
default backgroundImagePosition(value: Position | Alignment | undefined): this
```

Background image position x:Horizontal coordinate;y:Vertical axis coordinate.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default backgroundImagePosition(value: Position | Alignment | undefined): this--><!--Device-CommonMethod-default backgroundImagePosition(value: Position | Alignment | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Alignment \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backgroundImageResizable

```TypeScript
default backgroundImageResizable(value: ResizableOptions | undefined): this
```

Background image resizable. value:resizable options

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default backgroundImageResizable(value: ResizableOptions | undefined): this--><!--Device-CommonMethod-default backgroundImageResizable(value: ResizableOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Indicates the resizable options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backgroundImageSize

```TypeScript
default backgroundImageSize(value: SizeOptions | ImageSize | undefined): this
```

Background image size

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default backgroundImageSize(value: SizeOptions | ImageSize | undefined): this--><!--Device-CommonMethod-default backgroundImageSize(value: SizeOptions | ImageSize | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ImageSize \| undefined | 是 | The width and height of the background image. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindContentCover

```TypeScript
default bindContentCover(isShow: boolean | Bindable<boolean> | undefined, builder: CustomBuilder | undefined, type?: ModalTransition): this
```

给组件绑定全屏模态页面，点击后显示模态页面。模态页面内容自定义，显示方式可设置无动画过渡，上下切换过渡以及透明渐变过渡。 > **说明：** > > 该接口不支持在[attributeModifier]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindContentCover(isShow: boolean | Bindable<boolean> | undefined, builder: CustomBuilder | undefined, type?: ModalTransition): this--><!--Device-CommonMethod-default bindContentCover(isShow: boolean | Bindable<boolean> | undefined, builder: CustomBuilder | undefined, type?: ModalTransition): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isShow | boolean \| Bindable&lt;boolean&gt; \| undefined | 是 | 是否显示全屏模态页面。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-true：显示全屏模态页面。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-false：隐藏全屏模态页面。 |
| builder | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 配置全屏模态页面内容。 |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 全屏模态页面的系统转场方式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 默认值：ModalTransition.DEFAULT。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 同transition同时设置时，此属性不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindContentCover

```TypeScript
default bindContentCover(isShow: boolean | Bindable<boolean> | undefined, builder: CustomBuilder | undefined, options?: ContentCoverOptions): this
```

给组件绑定全屏模态页面，点击后显示模态页面。模态页面内容自定义，可自定义设置转场方式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindContentCover(isShow: boolean | Bindable<boolean> | undefined, builder: CustomBuilder | undefined, options?: ContentCoverOptions): this--><!--Device-CommonMethod-default bindContentCover(isShow: boolean | Bindable<boolean> | undefined, builder: CustomBuilder | undefined, options?: ContentCoverOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isShow | boolean \| Bindable&lt;boolean&gt; \| undefined | 是 | 是否显示全屏模态页面。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-true：显示全屏模态页面。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-false：隐藏全屏模态页面。 |
| builder | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 配置全屏模态页面内容。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 配置全屏模态页面的可选属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindContextMenu

```TypeScript
default bindContextMenu(content: CustomBuilder | undefined, responseType: ResponseType | undefined, options?: ContextMenuOptions): this
```

Binds a context menu to this component, which is displayed when the user long-presses or right-clicks the component. Only custom menu items are supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindContextMenu(content: CustomBuilder | undefined, responseType: ResponseType | undefined, options?: ContextMenuOptions): this--><!--Device-CommonMethod-default bindContextMenu(content: CustomBuilder | undefined, responseType: ResponseType | undefined, options?: ContextMenuOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Indicates the content of context menu. |
| responseType | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Indicates response type of context menu, Long pressing with a mouse device is not supported. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Indicates the options of context menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindContextMenu

```TypeScript
default bindContextMenu(isShow: boolean | Bindable<boolean> | undefined, content: CustomBuilder | undefined, options?: ContextMenuOptions): this
```

Binds a context menu to the component, whose visibility is subject to the isShow settings.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindContextMenu(isShow: boolean | Bindable<boolean> | undefined, content: CustomBuilder | undefined, options?: ContextMenuOptions): this--><!--Device-CommonMethod-default bindContextMenu(isShow: boolean | Bindable<boolean> | undefined, content: CustomBuilder | undefined, options?: ContextMenuOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isShow | boolean \| Bindable&lt;boolean&gt; \| undefined | 是 | Menu display switch,supports incoming twoway binding parameters.true means display content, false means hide content, default is false.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_NOTE\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_The menu can be displayed properly only when the related page has been constructed. If this parameter is set to true before the construction is complete, display issues, such as misplacement, distortion, or failure to pop up, may occur. To trigger dragging by long presses is not supported.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ |
| content | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Indicates the content of context menu. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Indicates the options of context menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindContextMenuByIsShow

```TypeScript
default bindContextMenuByIsShow(isShow: boolean | Bindable<boolean> | undefined,
        content: CustomBuilder | Array<MenuElement> | undefined, options?: ContextMenuOptions): this
```

Binds a context menu to the component, whose visibility is subject to the isShow settings.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindContextMenuByIsShow(isShow: boolean | Bindable<boolean> | undefined,        content: CustomBuilder | Array<MenuElement> | undefined, options?: ContextMenuOptions): this--><!--Device-CommonMethod-default bindContextMenuByIsShow(isShow: boolean | Bindable<boolean> | undefined,        content: CustomBuilder | Array<MenuElement> | undefined, options?: ContextMenuOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isShow | boolean \| Bindable&lt;boolean&gt; \| undefined | 是 | Menu display switch,supports incoming two-way binding parameters.true means display content, false means hide content, default is false.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_NOTE\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_The menu can be displayed properly only when the related page has been constructed. If this parameter is set to true before the construction is complete, display issues, such as misplacement, distortion, or failure to pop up, may occur. Dragging via long press is not supported.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ |
| content | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Array&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 | Indicates the content of context menu. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Indicates the options of context menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindContextMenuByResponseType

```TypeScript
default bindContextMenuByResponseType(content: CustomBuilder | Array<MenuElement> | undefined,
        responseType: ResponseType | undefined, options?: ContextMenuOptions): this
```

Binds a context menu to this component, which is displayed when the user long-presses or right-clicks the component. Only custom menu items are supported.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindContextMenuByResponseType(content: CustomBuilder | Array<MenuElement> | undefined,        responseType: ResponseType | undefined, options?: ContextMenuOptions): this--><!--Device-CommonMethod-default bindContextMenuByResponseType(content: CustomBuilder | Array<MenuElement> | undefined,        responseType: ResponseType | undefined, options?: ContextMenuOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Array&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 | Indicates the content of context menu. |
| responseType | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Indicates response type of context menu. Long pressing with a mouse device is not supported. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Indicates the options of context menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindContextMenuWithResponse

```TypeScript
default bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | undefined, options?: ContextMenuOptions): this
```

Binds a context menu to this component, which is displayed when the user long-presses or right-clicks the component. Only custom menu items are supported. Long pressing with a mouse device is not supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | undefined, options?: ContextMenuOptions): this--><!--Device-CommonMethod-default bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | undefined, options?: ContextMenuOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 | Indicates the content of context menu. Undefined means unbinding. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Indicates the options of context menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindContextMenuWithResponse

```TypeScript
default bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | Array<MenuElement> | undefined,
        options?: ContextMenuOptions): this
```

Binds a context menu to this component, which is displayed when the user long-presses or right-clicks the component. Only custom menu items are supported. Long pressing with a mouse device is not supported.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | Array<MenuElement> | undefined,        options?: ContextMenuOptions): this--><!--Device-CommonMethod-default bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | Array<MenuElement> | undefined,        options?: ContextMenuOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| Array&lt;MenuElement&gt; \| undefined | 是 | Indicates the content of context menu. Undefined means unbinding. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Indicates the options of context menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindMenu

```TypeScript
default bindMenu(content: Array<MenuElement> | CustomBuilder | undefined, options?: MenuOptions): this
```

Menu control

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindMenu(content: Array<MenuElement> | CustomBuilder | undefined, options?: MenuOptions): this--><!--Device-CommonMethod-default bindMenu(content: Array<MenuElement> | CustomBuilder | undefined, options?: MenuOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| CustomBuilder \| undefined | 是 | Indicates the content of menu. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Indicates the options of menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindMenu

```TypeScript
default bindMenu(isShow: boolean | Bindable<boolean> | undefined, content: Array<MenuElement> | CustomBuilder | undefined, options?: MenuOptions): this
```

Menu control

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindMenu(isShow: boolean | Bindable<boolean> | undefined, content: Array<MenuElement> | CustomBuilder | undefined, options?: MenuOptions): this--><!--Device-CommonMethod-default bindMenu(isShow: boolean | Bindable<boolean> | undefined, content: Array<MenuElement> | CustomBuilder | undefined, options?: MenuOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isShow | boolean \| Bindable&lt;boolean&gt; \| undefined | 是 | Menu display switch,supports incoming two-way binding parameters.true means display menu, false means hide menu, default is false. |
| content | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| CustomBuilder \| undefined | 是 | Indicates the content of menu. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Indicates the options of menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindPopup

```TypeScript
default bindPopup(show: boolean | undefined, popup: PopupOptions | CustomPopupOptions | undefined): this
```

Popup control \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_: \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_The popup can be displayed only after the entire page is fully constructed. Therefore, to avoid incorrect display positions and shapes, do not set this parameter to true while the page is still being constructed. \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindPopup(show: boolean | undefined, popup: PopupOptions | CustomPopupOptions | undefined): this--><!--Device-CommonMethod-default bindPopup(show: boolean | undefined, popup: PopupOptions | CustomPopupOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| show | boolean \| undefined | 是 | Whether to show the popup, default is false. |
| popup | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| CustomPopupOptions \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindSheet

```TypeScript
default bindSheet(isShow: boolean | Bindable<boolean> | undefined, builder: CustomBuilder | undefined, options?: SheetOptions): this
```

给组件绑定半模态页面，点击后显示模态页面。 > **说明：** > > 该接口不支持在[attributeModifier]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindSheet(isShow: boolean | Bindable<boolean> | undefined, builder: CustomBuilder | undefined, options?: SheetOptions): this--><!--Device-CommonMethod-default bindSheet(isShow: boolean | Bindable<boolean> | undefined, builder: CustomBuilder | undefined, options?: SheetOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isShow | boolean \| Bindable&lt;boolean&gt; \| undefined | 是 | 是否显示半模态页面。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：显示半模态页面。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_false：隐藏半模态页面。 |
| builder | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 配置半模态页面内容。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 配置半模态页面的可选属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## bindTips

```TypeScript
default bindTips(message: TipsMessageType | undefined, options?: TipsOptions): this
```

Tips control

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default bindTips(message: TipsMessageType | undefined, options?: TipsOptions): this--><!--Device-CommonMethod-default bindTips(message: TipsMessageType | undefined, options?: TipsOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## blendMode

```TypeScript
default blendMode(value: BlendMode | undefined, type?: BlendApplyType): this
```

Defines how the component's content (including the content of it child components) is blended with the existing content on the canvas (possibly offscreen canvas) below.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default blendMode(value: BlendMode | undefined, type?: BlendApplyType): this--><!--Device-CommonMethod-default blendMode(value: BlendMode | undefined, type?: BlendApplyType): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Blend mode.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **BlendMode.NONE**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**NOTE**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_When **BlendMode.NONE** is used, the blend effect is **BlendMode.SRC\_\_\_ESCAPED\_UNDERSCORE\_\_\_OVER** by default, and **BlendApplyType** does not take effect. |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Whether the blend mode is implemented offscreen.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **BlendApplyType.FAST**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**NOTE**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1. **BlendApplyType.FAST**: The blend mode is not implemented offscreen.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. **BlendApplyType.OFFSCREEN**: An offscreen canvas of the size of the current component is created. The content of the current component (including child components) is then drawn onto the offscreen canvas, and blended with the existing content on the canvas below using the specified blend mode. This approach may cause issues with screen capture for APIs such as linearGradientBlur\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_12+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_, backgroundEffect, and brightness. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## blur

```TypeScript
default blur(blurRadius: double | undefined, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): this
```

Adds the content blurring effect for the current component. The input parameter is the blurring radius. The larger the blurring radius, the more blurring the content. If the value is 0, the content blurring effect is not blurring.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default blur(blurRadius: double | undefined, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): this--><!--Device-CommonMethod-default blur(blurRadius: double | undefined, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurRadius | double \| undefined | 是 | value indicates radius of backdrop blur. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | options indicates blur options. |
| sysOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | system adaptive options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## border

```TypeScript
default border(value: BorderOptions | undefined): this
```

Sets the border.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default border(value: BorderOptions | undefined): this--><!--Device-CommonMethod-default border(value: BorderOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## borderColor

```TypeScript
default borderColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors | undefined): this
```

Sets the border color. Default value: **Color.Black**.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default borderColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors | undefined): this--><!--Device-CommonMethod-default borderColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| EdgeColors \| LocalizedEdgeColors \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## borderImage

```TypeScript
default borderImage(value: BorderImageOption | undefined): this
```

Sets the border image of the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default borderImage(value: BorderImageOption | undefined): this--><!--Device-CommonMethod-default borderImage(value: BorderImageOption | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Border image or border gradient. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## borderRadius

```TypeScript
default borderRadius(value: Length | BorderRadiuses | LocalizedBorderRadiuses | undefined, type?: RenderStrategy | undefined): this
```

Sets the radius of the border rounded corners. The radius is restricted by the component size. The maximum value is half of the component width or height. NOTE 1. **RenderStrategy.FAST**: The current component and its child components will be drawn directly onto the canvas with rounded corners applied. 2. **RenderStrategy.OFFSCREEN**: The current component and its child components will first be rendered onto an off-screen canvas, then undergo a rounded corner clipping, and finally be drawn onto the main canvas.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default borderRadius(value: Length | BorderRadiuses | LocalizedBorderRadiuses | undefined, type?: RenderStrategy | undefined): this--><!--Device-CommonMethod-default borderRadius(value: Length | BorderRadiuses | LocalizedBorderRadiuses | undefined, type?: RenderStrategy | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| BorderRadiuses \| LocalizedBorderRadiuses \| undefined | 是 |  |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 否 | Application types for drawing rounded corners.Default value: **RenderStrategy.FAST**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## borderStyle

```TypeScript
default borderStyle(value: BorderStyle | EdgeStyles | undefined): this
```

Sets the border style. Default value: **BorderStyle.Solid**.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default borderStyle(value: BorderStyle | EdgeStyles | undefined): this--><!--Device-CommonMethod-default borderStyle(value: BorderStyle | EdgeStyles | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| EdgeStyles \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## borderWidth

```TypeScript
default borderWidth(value: Length | EdgeWidths | LocalizedEdgeWidths | undefined): this
```

Sets the border width. Percentage values are not supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default borderWidth(value: Length | EdgeWidths | LocalizedEdgeWidths | undefined): this--><!--Device-CommonMethod-default borderWidth(value: Length | EdgeWidths | LocalizedEdgeWidths | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| EdgeWidths \| LocalizedEdgeWidths \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## brightness

```TypeScript
default brightness(value: double | undefined): this
```

Applies a brightness effect to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default brightness(value: double | undefined): this--><!--Device-CommonMethod-default brightness(value: double | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| undefined | 是 | Brightness of the component. The value **1** indicates no effects.The value **0** indicates the complete darkness. If the value is less than **1**, the brightness decreases. If the value is greater than **1**, the brightness increases. A larger value indicates a higher brightness. A brightness of 2 turns the component completely white.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **1.0**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Recommended value range: [0, 2].\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**NOTE**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_A value less than 0 evaluates to the value **0**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**Widget capability**: This API can be used in ArkTS widgets since API version 9. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## chainMode

```TypeScript
default chainMode(direction: Axis | undefined, style: ChainStyle | undefined): this
```

Sets the parameters of the chain in which the component is the head. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_This parameter has effect only when the parent container is RelativeContainer. \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_The chain head is the first component in the chain that satisfies the chain formation rules. In a horizontal layout, it starts from the left (or from the right in a mirrored language layout). In a vertical layout, it starts from the top.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default chainMode(direction: Axis | undefined, style: ChainStyle | undefined): this--><!--Device-CommonMethod-default chainMode(direction: Axis | undefined, style: ChainStyle | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | indicates direction of the chain |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | indicates style of the chain |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## chainWeight

```TypeScript
default chainWeight(chainWeight: ChainWeightOptions | undefined): this
```

Sets the weight of the component in a chain, which is used to re-lay out components that form the chain. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_This API has effect only when the parent container is RelativeContainer.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default chainWeight(chainWeight: ChainWeightOptions | undefined): this--><!--Device-CommonMethod-default chainWeight(chainWeight: ChainWeightOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chainWeight | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## clickEffect

```TypeScript
default clickEffect(value: ClickEffect | null | undefined): this
```

设置当前组件的点击回弹效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default clickEffect(value: ClickEffect | null | undefined): this--><!--Device-CommonMethod-default clickEffect(value: ClickEffect | null | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null \| undefined | 是 | 设置当前组件点击回弹效果。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_可通过undefined或者null取消点击回弹效果。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_不建议在组件大小动态变化的场景中使用该功能。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当组件无法触发通用事件时，不支持该属性。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_回弹触发缩放后可能造成触摸点不在控件上，控件上无法响应手势事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return the component attribute. |

## clip

```TypeScript
default clip(value: boolean | undefined): this
```

是否对子组件超出当前组件范围外的区域进行裁剪。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default clip(value: boolean | undefined): this--><!--Device-CommonMethod-default clip(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | 参数为boolean类型，设置是否按照父容器边缘轮廓进行裁剪。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：false \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true表示按照父容器边缘轮廓进行裁剪，false表示不对子组件进行裁剪。 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：** 设置为true后，子组件超出当前组件范围外的区域将不响应绑定的手势事件。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value的值为undefined时，恢复为不对子组件超出当前组件范围外的区域进行裁剪。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## clipShape

```TypeScript
default clipShape(value: CircleShape | EllipseShape | PathShape | RectShape | undefined): this
```

按指定的形状（形状中可包含位置信息）对当前组件进行裁剪。 > **说明：** > > 不同的形状支持的属性范围不同，路径是一种形状，除此之外还有椭圆、矩形等形状。 > > 路径的形状不支持设置宽度和高度。具体形状支持的属性参考具体形状的文档。 > > 形状中的[fill]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_属性对clipShape接口不生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default clipShape(value: CircleShape | EllipseShape | PathShape | RectShape | undefined): this--><!--Device-CommonMethod-default clipShape(value: CircleShape | EllipseShape | PathShape | RectShape | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| EllipseShape \| PathShape \| RectShape \| undefined | 是 | 参数为相应类型的组件，按指定的形状（形状中可包含位置信息）对当前组件进行裁剪。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：** 裁剪不会导致被裁剪区域无法响应绑定的手势事件。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value的值为undefined时，会重置为当前值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## colorBlend

```TypeScript
default colorBlend(value: Color | string | Resource | undefined): this
```

Applies a color blend effect to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default colorBlend(value: Color | string | Resource | undefined): this--><!--Device-CommonMethod-default colorBlend(value: Color | string | Resource | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| string \| Resource \| undefined | 是 | Color to blend with the component. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## compositingFilter

```TypeScript
default compositingFilter(filter: Filter | undefined): this
```

设置合成滤镜视觉效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default compositingFilter(filter: Filter | undefined): this--><!--Device-CommonMethod-default compositingFilter(filter: Filter | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 合成滤镜视觉效果。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当filter的值为undefined时，无合成滤镜视觉效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## constraintSize

```TypeScript
default constraintSize(value: ConstraintSizeOptions | undefined): this
```

Sets the constraint size of the component, which is used to limit the size range during component layout. Default value: **{minWidth: 0, maxWidth: Infinity, minHeight: 0, maxHeight: Infinity}**.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default constraintSize(value: ConstraintSizeOptions | undefined): this--><!--Device-CommonMethod-default constraintSize(value: ConstraintSizeOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## contrast

```TypeScript
default contrast(value: double | undefined): this
```

Applies a contrast effect to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default contrast(value: double | undefined): this--><!--Device-CommonMethod-default contrast(value: double | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| undefined | 是 | Contrast of the component. The input parameter is a contrast value. If the value is **1**, the source image is displayed. If the value is greater than 1, a larger value indicates a higher contrast and a clearer image. If the value is less than 1, a smaller value indicates a lower contrast is.If the value is **0**, the image becomes all gray. The unit is percentage.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **1.0**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Recommended value range: [0, 10).\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**NOTE**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_A value less than 0 evaluates to the value **0**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## customProperty

```TypeScript
default customProperty(name: string, value: CustomProperty): this
```

Sets the custom property of the current component. This API does not work for custom components.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default customProperty(name: string, value: CustomProperty): this--><!--Device-CommonMethod-default customProperty(name: string, value: CustomProperty): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | the name of the custom property. |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | the value of the custom property. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## debugLine

```TypeScript
default debugLine(sourceLine: string, moduleName?: string): this
```

Set the component's source code redirection information.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default debugLine(sourceLine: string, moduleName?: string): this--><!--Device-CommonMethod-default debugLine(sourceLine: string, moduleName?: string): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceLine | string | 是 | the source code line. |
| moduleName | string | 否 | module to which the component belongs. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## defaultFocus

```TypeScript
default defaultFocus(value: boolean | undefined): this
```

Set default focused component when a page create.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default defaultFocus(value: boolean | undefined): this--><!--Device-CommonMethod-default defaultFocus(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | True means to set the component as the default focus,and the value false has no effect. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## direction

```TypeScript
default direction(value: Direction | undefined): this
```

Sets how elements are laid out along the main axis of the container. Default value: **Direction.Auto**.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default direction(value: Direction | undefined): this--><!--Device-CommonMethod-default direction(value: Direction | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## displayPriority

```TypeScript
default displayPriority(value: double | undefined): this
```

Sets the display priority for the component in the layout container. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_This parameter is only effective in Row, Column, and Flex (single-line) container components.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default displayPriority(value: double | undefined): this--><!--Device-CommonMethod-default displayPriority(value: double | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## doubleSided

```TypeScript
default doubleSided(value: boolean | undefined): this
```

Sets whether to component is double-sided.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default doubleSided(value: boolean | undefined): this--><!--Device-CommonMethod-default doubleSided(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | Whether to component is double-sided.**true**: Both front and back sides are visible (default).**false**: Only to front side is visible, to back side is hidden when rotated.When **value** is **undefined**, the component reverts to default double-sided setting (**true**). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## dragPreview

```TypeScript
default dragPreview(preview: CustomBuilder | DragItemInfo | string | undefined, config?: PreviewConfiguration): this
```

Set preview of the component for dragging process

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default dragPreview(preview: CustomBuilder | DragItemInfo | string | undefined, config?: PreviewConfiguration): this--><!--Device-CommonMethod-default dragPreview(preview: CustomBuilder | DragItemInfo | string | undefined, config?: PreviewConfiguration): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| preview | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| DragItemInfo \| string \| undefined | 是 | preview of the component for dragging process |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | drag preview configuration. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return the component attribute. |

## dragPreviewOptions

```TypeScript
default dragPreviewOptions(value: DragPreviewOptions | undefined, options?: DragInteractionOptions): this
```

Set the selectable area drag preview options.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default dragPreviewOptions(value: DragPreviewOptions | undefined, options?: DragInteractionOptions): this--><!--Device-CommonMethod-default dragPreviewOptions(value: DragPreviewOptions | undefined, options?: DragInteractionOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | preview options value. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | drag interaction options value. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return the component attribute. |

## draggable

```TypeScript
default draggable(value: boolean | undefined): this
```

Enable the selectable area can be dragged.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default draggable(value: boolean | undefined): this--><!--Device-CommonMethod-default draggable(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | true means the area can be dragged, false means the area can't be dragged.The default value is false. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return the component attribute. |

## drawModifier

```TypeScript
default drawModifier(modifier: DrawModifier | undefined): this
```

Sets the drawModifier of the current component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default drawModifier(modifier: DrawModifier | undefined): this--><!--Device-CommonMethod-default drawModifier(modifier: DrawModifier | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | drawModifier used to draw, or undefined if it is not available.Default value: undefined A custom modifier applies only to the FrameNode of the currently bound component, not to its subnodes. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableClickSoundEffect

```TypeScript
default enableClickSoundEffect(enabled: boolean | undefined): this
```

Set whether this component should have sound effects enabled for clicking. Sound effects playback is affected by the audio-related settings in the device system settings. When the user sets the device to silent mode, sound effects cannot be played.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default enableClickSoundEffect(enabled: boolean | undefined): this--><!--Device-CommonMethod-default enableClickSoundEffect(enabled: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 | indicates whether this component should have sound effects enabled for clicking.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Pass in undefined to reset the default value, default value is true, but even it's true, the sound effect is only supported in some specific devices. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enabled

```TypeScript
default enabled(value: boolean | undefined): this
```

If the value is true, the component is available and can respond to operations such as clicking. If it is set to false, click operations are not responded.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default enabled(value: boolean | undefined): this--><!--Device-CommonMethod-default enabled(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## expandSafeArea

```TypeScript
default expandSafeArea(types?: Array<SafeAreaType>, edges?: Array<SafeAreaEdge>): this
```

Sets the safe area to be expanded to. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_default:{types: [SafeAreaType.SYSTEM, SafeAreaType.CUTOUT, SafeAreaType.KEYBOARD], edges: [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM, SafeAreaEdge.START, SafeAreaEdge.END]}

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default expandSafeArea(types?: Array<SafeAreaType>, edges?: Array<SafeAreaEdge>): this--><!--Device-CommonMethod-default expandSafeArea(types?: Array<SafeAreaType>, edges?: Array<SafeAreaEdge>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | 否 | Indicates the types of the safe area. |
| edges | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | 否 | Indicates the edges of the safe area. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | The component instance. |

## flexBasis

```TypeScript
default flexBasis(value: double | string | undefined): this
```

Sets the base size of the component in the main axis of the parent container. Default value: **'auto'**.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default flexBasis(value: double | string | undefined): this--><!--Device-CommonMethod-default flexBasis(value: double | string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| string \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## flexGrow

```TypeScript
default flexGrow(value: double | undefined): this
```

Sets the percentage of the parent container's remaining space that is allocated to the component. Default value: **0**.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default flexGrow(value: double | undefined): this--><!--Device-CommonMethod-default flexGrow(value: double | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## flexShrink

```TypeScript
default flexShrink(value: double | undefined): this
```

Sets the percentage of the parent container's shrink size that is allocated to the component. Default value: 0 when the parent container is Column or Row, 1 when the parent container is Flex..

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default flexShrink(value: double | undefined): this--><!--Device-CommonMethod-default flexShrink(value: double | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## focusBox

```TypeScript
default focusBox(style: FocusBoxStyle | undefined): this
```

Set the component's focusBox style.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default focusBox(style: FocusBoxStyle | undefined): this--><!--Device-CommonMethod-default focusBox(style: FocusBoxStyle | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Component's focusBox style. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## focusOnTouch

```TypeScript
default focusOnTouch(value: boolean | undefined): this
```

Set a component focused when the component be touched.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default focusOnTouch(value: boolean | undefined): this--><!--Device-CommonMethod-default focusOnTouch(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | True means the component is focusable on touch, false means the component is not focusable on touch. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## focusScopeId

```TypeScript
default focusScopeId(id: string | undefined, isGroup?: boolean, arrowStepOut?: boolean): this
```

Set container as a focus group with a specific identifier.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default focusScopeId(id: string | undefined, isGroup?: boolean, arrowStepOut?: boolean): this--><!--Device-CommonMethod-default focusScopeId(id: string | undefined, isGroup?: boolean, arrowStepOut?: boolean): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string \| undefined | 是 | focus scope identifier. |
| isGroup | boolean | 否 | whether this scope is a focus group, the default value is false. |
| arrowStepOut | boolean | 否 | whether the arrow keys can move focus from inside the focus group to outside,only effective when isGroup is true, the default value is true. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## focusScopePriority

```TypeScript
default focusScopePriority(scopeId: string | undefined, priority?: FocusPriority): this
```

Set the focus priority of component in a specific focus scope.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default focusScopePriority(scopeId: string | undefined, priority?: FocusPriority): this--><!--Device-CommonMethod-default focusScopePriority(scopeId: string | undefined, priority?: FocusPriority): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scopeId | string \| undefined | 是 |  |
| priority | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | the default value is AUTO |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## focusable

```TypeScript
default focusable(value: boolean | undefined): this
```

Set focusable. Components that have default interaction logic, such as Button and TextInput, are focusable by default. Other components, such as Text and Image, are not focusable by default. Only focusable components can trigger a focus event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default focusable(value: boolean | undefined): this--><!--Device-CommonMethod-default focusable(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## foregroundBlurStyle

```TypeScript
default foregroundBlurStyle(style: BlurStyle | undefined, options?: ForegroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): this
```

Applies a foreground blur style to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default foregroundBlurStyle(style: BlurStyle | undefined, options?: ForegroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): this--><!--Device-CommonMethod-default foregroundBlurStyle(style: BlurStyle | undefined, options?: ForegroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Settings of the foreground blur style. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |
| sysOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | system adaptive options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## foregroundColor

```TypeScript
default foregroundColor(value: ResourceColor | ColoringStrategy | undefined): this
```

设置组件的前景色。当组件未设置前景色，默认继承父组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default foregroundColor(value: ResourceColor | ColoringStrategy | undefined): this--><!--Device-CommonMethod-default foregroundColor(value: ResourceColor | ColoringStrategy | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ColoringStrategy \| undefined | 是 | 设置组件的前景颜色或者根据智能取色策略设置前景颜色。不支持属性动画。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value的值为undefined时，维持之前取值或组件默认取值，具体行为不同组件可能会有差异，建议开发者使用确定颜色或[ColoringStrategy]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## foregroundEffect

```TypeScript
default foregroundEffect(options: ForegroundEffectOptions | undefined): this
```

Foreground effect.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default foregroundEffect(options: ForegroundEffectOptions | undefined): this--><!--Device-CommonMethod-default foregroundEffect(options: ForegroundEffectOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | options indicates the effect options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## foregroundFilter

```TypeScript
default foregroundFilter(filter: Filter | undefined): this
```

设置前景滤镜（内容）视觉效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default foregroundFilter(filter: Filter | undefined): this--><!--Device-CommonMethod-default foregroundFilter(filter: Filter | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 前景滤镜（内容）视觉效果。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当filter的值为undefined时，无前景滤镜（内容）视觉效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## freeze

```TypeScript
default freeze(value: boolean | undefined): this
```

Sets whether to freeze the component. When frozen, the component and its children are cached for repeated drawing after offscreen rendering, without updating internal attributes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default freeze(value: boolean | undefined): this--><!--Device-CommonMethod-default freeze(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | Whether to freeze the component. When frozen, the component and its children are cached for repeated drawing after offscreen rendering, without updating internal attributes. If the opacity of the component is not 1, the drawing effect may vary depending on the value.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **false**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ **true**: Freeze the component.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**false**: Do not freeze the component. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## geometryTransition

```TypeScript
default geometryTransition(id: string | undefined, options?: GeometryTransitionOptions): this
```

组件内隐式共享元素转场。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default geometryTransition(id: string | undefined, options?: GeometryTransitionOptions): this--><!--Device-CommonMethod-default geometryTransition(id: string | undefined, options?: GeometryTransitionOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string \| undefined | 是 | geometry transition id |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 组件内共享元素转场动画参数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值为 { follow: false }。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## gesture

```TypeScript
default gesture(gesture: GestureType, mask?: GestureMask): this
```

Bind gesture recognition. gesture:Bound Gesture Type,mask:GestureMask;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default gesture(gesture: GestureType, mask?: GestureMask): this--><!--Device-CommonMethod-default gesture(gesture: GestureType, mask?: GestureMask): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesture | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 |  |
| mask | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## gestureModifier

```TypeScript
default gestureModifier(modifier: GestureModifier | undefined): this
```

Sets the gesture modifier.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default gestureModifier(modifier: GestureModifier | undefined): this--><!--Device-CommonMethod-default gestureModifier(modifier: GestureModifier | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## grayscale

```TypeScript
default grayscale(value: double | undefined): this
```

Applies a grayscale effect to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default grayscale(value: double | undefined): this--><!--Device-CommonMethod-default grayscale(value: double | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| undefined | 是 | Grayscale conversion ratio of the component.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_If the value is **1.0**, the component is completely converted to grayscale.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_If the value is **0.0**, the component remains unchanged. Between **0** and **1**,\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_the value applies a linear multiplier on the grayscale effect. The unit is percentage.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **0.0**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Value range: [0.0, 1.0].\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**NOTE**:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_A value less than **0.0** evaluates to the value **0.0**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_7\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_A value greater than **1.0** evaluates to the value **1.0**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_8\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## groupDefaultFocus

```TypeScript
default groupDefaultFocus(value: boolean | undefined): this
```

Set default focused component when focus on a focus group.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default groupDefaultFocus(value: boolean | undefined): this--><!--Device-CommonMethod-default groupDefaultFocus(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | True means the component is the default focus of the parent container, and false means the component is not the default focus of the parent container. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## height

```TypeScript
default height(heightValue: Length | LayoutPolicy | undefined): this
```

Sets the height of the component or its vertical layout policy. By default, the component uses the height required for its content. If the height of the component is greater than that of the parent container, the component will be drawn beyond the parent container scope.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default height(heightValue: Length | LayoutPolicy | undefined): this--><!--Device-CommonMethod-default height(heightValue: Length | LayoutPolicy | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| heightValue | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| LayoutPolicy \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hitTestBehavior

```TypeScript
default hitTestBehavior(value: HitTestMode | undefined): this
```

Sets how the component behaves during hit testing.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default hitTestBehavior(value: HitTestMode | undefined): this--><!--Device-CommonMethod-default hitTestBehavior(value: HitTestMode | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | the hit test mode.@default HitTestMode.default - Both the node and its child nodes respond to the hit test of a touch event,but its sibling nodes are blocked from the hit test. The hit test for ancestor nodes is not affected. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hoverEffect

```TypeScript
default hoverEffect(value: HoverEffect | undefined): this
```

Set hover effect.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default hoverEffect(value: HoverEffect | undefined): this--><!--Device-CommonMethod-default hoverEffect(value: HoverEffect | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Hover effect of the component in hover state. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hueRotate

```TypeScript
default hueRotate(value: double | string | undefined): this
```

Rotates the hue of the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default hueRotate(value: double | string | undefined): this--><!--Device-CommonMethod-default hueRotate(value: double | string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| string \| undefined | 是 | Hue rotation angle of the component.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_A rotation of 360 degrees leaves the color unchanged.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_A rotation of 180 degrees and then -180 degrees also leaves the color unchanged.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_When the data type is number, the value **90** is equivalent to **'90deg'**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## id

```TypeScript
default id(value: string | undefined): this
```

Id. User can set an id to the component to identify it.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default id(value: string | undefined): this--><!--Device-CommonMethod-default id(value: string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## ignoreLayoutSafeArea

```TypeScript
default ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType> | undefined, edges?: Array<LayoutSafeAreaEdge> | undefined): this
```

Expands the layout safe area of a component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType> | undefined, edges?: Array<LayoutSafeAreaEdge> | undefined): this--><!--Device-CommonMethod-default ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType> | undefined, edges?: Array<LayoutSafeAreaEdge> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| undefined | 否 | The region type to expand the component's layout safe area into.The default value is LayoutSafeAreaType.SYSTEM. |
| edges | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| undefined | 否 | The set of edges for which to ignore layout safe area.The default value is LayoutSafeAreaEdge.ALL. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## inspectorLabel

```TypeScript
default inspectorLabel(label: string | undefined): this
```

Set the component's inspector label which only display on DevEco Studio.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default inspectorLabel(label: string | undefined): this--><!--Device-CommonMethod-default inspectorLabel(label: string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string \| undefined | 是 | the inspector label. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## invert

```TypeScript
default invert(value: double | InvertOptions | undefined): this
```

Invert the input image. Value defines the scale of the conversion. 100% of the value is a complete reversal. A value of 0% does not change the image. (Percentage)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default invert(value: double | InvertOptions | undefined): this--><!--Device-CommonMethod-default invert(value: double | InvertOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| InvertOptions \| undefined | 是 | value indicates the scale of the conversion or the options of invert. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## key

```TypeScript
default key(value: string | undefined): this
```

Key. User can set an key to the component to identify it.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default key(value: string | undefined): this--><!--Device-CommonMethod-default key(value: string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## keyboardShortcut

```TypeScript
default keyboardShortcut(value: string | FunctionKey | undefined, keys: Array<ModifierKey> | undefined, action?: () => void): this
```

Sets hot keys

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default keyboardShortcut(value: string | FunctionKey | undefined, keys: Array<ModifierKey> | undefined, action?: () => void): this--><!--Device-CommonMethod-default keyboardShortcut(value: string | FunctionKey | undefined, keys: Array<ModifierKey> | undefined, action?: () => void): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| FunctionKey \| undefined | 是 | Character of the combination key. |
| keys | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| undefined | 是 | The modifier keys modify the action of key when the key are pressed at the same time. |
| action | () =&gt; void | 否 | Callback function, triggered when the shortcut keyboard is pressed. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## layoutGravity

```TypeScript
default layoutGravity(alignment: LocalizedAlignment | undefined): this
```

Defines the align rules of child component in Stack container.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default layoutGravity(alignment: LocalizedAlignment | undefined): this--><!--Device-CommonMethod-default layoutGravity(alignment: LocalizedAlignment | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignment | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## layoutWeight

```TypeScript
default layoutWeight(value: double | string | undefined): this
```

Sets the weight of the component during layout. A component with this attribute is allocated space along the main axis of its parent container (Row, Column, or Flex) based on its specified weight. Default value: **0**.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default layoutWeight(value: double | string | undefined): this--><!--Device-CommonMethod-default layoutWeight(value: double | string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| string \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## lightUpEffect

```TypeScript
default lightUpEffect(value: double | undefined): this
```

Applies a light up effect to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default lightUpEffect(value: double | undefined): this--><!--Device-CommonMethod-default lightUpEffect(value: double | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| undefined | 是 | Light up degree of the component.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_The value ranges from 0 to 1.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_If the value is **0**, the component is dark. If the value is **1**, the component is fully illuminated.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Between **0** and **1**, a larger value indicates higher luminance.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_A value less than 0 is handled as the value **0**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_A value greater than 1 is handled as the value **1**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## linearGradient

```TypeScript
default linearGradient(value: LinearGradientOptions | undefined): this
```

Linear Gradient angle: Angle of Linear Gradient. The default value is 180; direction: Direction of Linear Gradient. The default value is GradientDirection.Bottom; colors: Color description for gradients. repeating: repeating. The default value is false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default linearGradient(value: LinearGradientOptions | undefined): this--><!--Device-CommonMethod-default linearGradient(value: LinearGradientOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Linear gradient.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_If **options** is **undefined**, the linear gradient is disabled. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## linearGradientBlur

```TypeScript
default linearGradientBlur(value: double | undefined, options: LinearGradientBlurOptions | undefined): this
```

Applies a linear gradient foreground blur effect to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default linearGradientBlur(value: double | undefined, options: LinearGradientBlurOptions | undefined): this--><!--Device-CommonMethod-default linearGradientBlur(value: double | undefined, options: LinearGradientBlurOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| undefined | 是 | the blurring radius. The larger the blurring radius, the more blurring the content, and if the value is 0, the content blurring effect is not blurring. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | the linear gradient blur options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## margin

```TypeScript
default margin(value: Margin | Length | LocalizedMargin | undefined): this
```

Sets the margin of the component. Default value: **0**.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default margin(value: Margin | Length | LocalizedMargin | undefined): this--><!--Device-CommonMethod-default margin(value: Margin | Length | LocalizedMargin | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Length \| LocalizedMargin \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## markAnchor

```TypeScript
default markAnchor(value: Position | LocalizedPosition | undefined): this
```

Sets the anchor for locating the component, which is used to move the component further away from the position specified by position or offset.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default markAnchor(value: Position | LocalizedPosition | undefined): this--><!--Device-CommonMethod-default markAnchor(value: Position | LocalizedPosition | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| LocalizedPosition \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## mask

```TypeScript
default mask(value: ProgressMask | undefined): this
```

为组件上添加可调节进度的遮罩。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default mask(value: ProgressMask | undefined): this--><!--Device-CommonMethod-default mask(value: ProgressMask | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 在当前组件上加上可动态设置进度、最大值和颜色的遮罩。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value的值为undefined时，恢复为无进度遮罩效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## maskShape

```TypeScript
default maskShape(value: CircleShape | EllipseShape | PathShape | RectShape | undefined): this
```

为组件上添加指定形状的遮罩。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default maskShape(value: CircleShape | EllipseShape | PathShape | RectShape | undefined): this--><!--Device-CommonMethod-default maskShape(value: CircleShape | EllipseShape | PathShape | RectShape | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| EllipseShape \| PathShape \| RectShape \| undefined | 是 | 在当前组件上加上指定形状的遮罩。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value的值为undefined时，会重置为当前值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## materialFilter

```TypeScript
default materialFilter(filter: Filter | undefined): this
```

设置系统材质滤镜效果，系统材质滤镜的绘制早于[backgroundFilter]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_绘制，即位于backgroundFilter的更底层。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default materialFilter(filter: Filter | undefined): this--><!--Device-CommonMethod-default materialFilter(filter: Filter | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 系统材质滤镜视觉效果。设置为undefined时恢复为无系统材质滤镜效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## monopolizeEvents

```TypeScript
default monopolizeEvents(monopolize: boolean | undefined): this
```

Sets whether the component exclusively handles events. true: The component exclusively handles events. false: The component does not exclusively handle events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default monopolizeEvents(monopolize: boolean | undefined): this--><!--Device-CommonMethod-default monopolizeEvents(monopolize: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| monopolize | boolean \| undefined | 是 | indicate the monopoly of events@default false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## motionBlur

```TypeScript
default motionBlur(value: MotionBlurOptions | undefined): this
```

Apply a motion blur effect to the component being scaled or moved. 1.Do not use this API in intra-component transitions, shared element transitions, implicit element transitions, or particle animations. Doing so may cause unexpected results. 2.The **radius** parameter of **motionBlur** must be set to **0** for the initial state. Otherwise, there may be unexpected results during a cold start. 3.This API must be used together with the **onFinish** parameter of **AnimateParam**. Its **radius** parameter must be set to **0** when the animation ends; otherwise, there may be unexpected results. 4.When using this API, do not frequently change the blur radius of the same component; otherwise, there may be unexpected results. For example, if you frequently click the image in the example, the blur effect may not work sometimes. 5.To avoid unexpected results, make sure the coordinates of the motion blur anchor point are the same as those of the animation scaling anchor point. 6.To avoid unexpected results, set the blur radius to a value less than 1.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default motionBlur(value: MotionBlurOptions | undefined): this--><!--Device-CommonMethod-default motionBlur(value: MotionBlurOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Motion blur options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## motionPath

```TypeScript
default motionPath(value: MotionPathOptions | undefined): this
```

设置组件的路径动画。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default motionPath(value: MotionPathOptions | undefined): this--><!--Device-CommonMethod-default motionPath(value: MotionPathOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 设置组件的运动路径。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value的值为undefined时，使用默认值{ MotionPathOptions: {path: " ", from: 0, to: 1, rotatable: false } }。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## mouseResponseRegion

```TypeScript
default mouseResponseRegion(value: Array<Rectangle> | Rectangle | undefined): this
```

Sets the mouse response region of current component

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default mouseResponseRegion(value: Array<Rectangle> | Rectangle | undefined): this--><!--Device-CommonMethod-default mouseResponseRegion(value: Array<Rectangle> | Rectangle | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| Rectangle \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return the component attribute |

## nextFocus

```TypeScript
default nextFocus(nextStep: FocusMovement | undefined): this
```

Set nextFocus.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default nextFocus(nextStep: FocusMovement | undefined): this--><!--Device-CommonMethod-default nextFocus(nextStep: FocusMovement | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| nextStep | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## obscured

```TypeScript
default obscured(reasons: Array<ObscuredReasons> | undefined): this
```

Sets obscured

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default obscured(reasons: Array<ObscuredReasons> | undefined): this--><!--Device-CommonMethod-default obscured(reasons: Array<ObscuredReasons> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reasons | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| undefined | 是 | reasons of obscuration |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## offset

```TypeScript
default offset(value: Position | Edges | LocalizedEdges | undefined): this
```

Sets the offset of the component relative to its original position. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_The offset attribute does not affect the layout of the parent container. It adjusts the component position only during drawing.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default offset(value: Position | Edges | LocalizedEdges | undefined): this--><!--Device-CommonMethod-default offset(value: Position | Edges | LocalizedEdges | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Edges \| LocalizedEdges \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAccessibilityActionIntercept

```TypeScript
default onAccessibilityActionIntercept(callback: AccessibilityActionInterceptCallback | undefined): this
```

Register accessibility action intercept callback, when accessibility action is to be executed,the callback will be executed

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onAccessibilityActionIntercept(callback: AccessibilityActionInterceptCallback | undefined): this--><!--Device-CommonMethod-default onAccessibilityActionIntercept(callback: AccessibilityActionInterceptCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | accessibility action intercept callback function |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAccessibilityFocus

```TypeScript
default onAccessibilityFocus(callback: AccessibilityFocusCallback | undefined): this
```

Register accessibility focus callback,when the component is focused or out of focus,the callback will be executed

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onAccessibilityFocus(callback: AccessibilityFocusCallback | undefined): this--><!--Device-CommonMethod-default onAccessibilityFocus(callback: AccessibilityFocusCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | accessibility focus callback function |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAccessibilityHover

```TypeScript
default onAccessibilityHover(callback: AccessibilityCallback | undefined): this
```

Trigger a accessibility hover event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onAccessibilityHover(callback: AccessibilityCallback | undefined): this--><!--Device-CommonMethod-default onAccessibilityHover(callback: AccessibilityCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | A callback instance used when the component is touched after accessibility mode is enabled. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAccessibilityHoverTransparent

```TypeScript
default onAccessibilityHoverTransparent(callback: AccessibilityTransparentCallback | undefined): this
```

prompt for current component and descendants unable to handle accessibility hover event

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onAccessibilityHoverTransparent(callback: AccessibilityTransparentCallback | undefined): this--><!--Device-CommonMethod-default onAccessibilityHoverTransparent(callback: AccessibilityTransparentCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | A callback instance used when current component and descendants not handled accessibility hover event |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAppear

```TypeScript
default onAppear(event: (() => void) | undefined): this
```

This callback is triggered when a component mounts a display.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onAppear(event: (() => void) | undefined): this--><!--Device-CommonMethod-default onAppear(event: (() => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (() =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAreaChange

```TypeScript
default onAreaChange(event: ((oldValue: Area, newValue: Area) => void) | undefined): this
```

This callback is triggered when the size or position of this component change finished.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onAreaChange(event: ((oldValue: Area, newValue: Area) => void) | undefined): this--><!--Device-CommonMethod-default onAreaChange(event: ((oldValue: Area, newValue: Area) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ((oldValue: Area, newValue: Area) =&gt; void) \| undefined | 是 | event callback. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAreaChange

```TypeScript
default onAreaChange (event: AreaChangeCallback, options?: AreaChangeOptions): this
```

This callback is triggered when the size or position of this component has finished changing. The interval between two area change callbacks will not be less than the expected update interval.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onAreaChange (event: AreaChangeCallback, options?: AreaChangeOptions): this--><!--Device-CommonMethod-default onAreaChange (event: AreaChangeCallback, options?: AreaChangeOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback invoked when the area of the component changes. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | The options for the area change event. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAttach

```TypeScript
default onAttach(callback: VoidCallback | undefined): this
```

This callback is triggered when a component mounts to view tree.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onAttach(callback: VoidCallback | undefined): this--><!--Device-CommonMethod-default onAttach(callback: VoidCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAxisEvent

```TypeScript
default onAxisEvent(event: Callback<AxisEvent> | undefined): this
```

Handle axis events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onAxisEvent(event: Callback<AxisEvent> | undefined): this--><!--Device-CommonMethod-default onAxisEvent(event: Callback<AxisEvent> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onBlur

```TypeScript
default onBlur(event: (() => void) | undefined): this
```

Triggered when the current component loses focus.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onBlur(event: (() => void) | undefined): this--><!--Device-CommonMethod-default onBlur(event: (() => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (() =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onChildTouchTest

```TypeScript
default onChildTouchTest(event: ((value: Array<TouchTestInfo>) => TouchResult) | undefined): this
```

Called to specify how to perform the touch test on the children of this component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onChildTouchTest(event: ((value: Array<TouchTestInfo>) => TouchResult) | undefined): this--><!--Device-CommonMethod-default onChildTouchTest(event: ((value: Array<TouchTestInfo>) => TouchResult) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ((value: Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt;) =&gt; TouchResult) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onClick

```TypeScript
default onClick(event: ((event: ClickEvent) => void) | undefined): this
```

Called when a click event occurs. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_: \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_ Since API version 9, the following constraints apply when this API is used in service widgets: \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_ Click events cannot be triggered if the finger is pressed for more than 800 ms. \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_ Click events cannot be triggered if the finger moves more than 20 px after pressing down. \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onClick(event: ((event: ClickEvent) => void) | undefined): this--><!--Device-CommonMethod-default onClick(event: ((event: ClickEvent) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ((event: ClickEvent) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onClick

```TypeScript
default onClick(event: Callback<ClickEvent> | undefined, distanceThreshold: double | undefined): this
```

Trigger a click event when a click is clicked, move distance should smaller than distanceThreshold. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_: \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_ If the distanceThreshold value specified is less than or equal to 0 vp, it will be converted to the default value. Since API version 9, the following constraints apply when this API is used in service widgets: \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_ Click events cannot be triggered if the finger is pressed for more than 800 ms. \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_ Click events cannot be triggered if the finger moves more than 20 px after pressing down. \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onClick(event: Callback<ClickEvent> | undefined, distanceThreshold: double | undefined): this--><!--Device-CommonMethod-default onClick(event: Callback<ClickEvent> | undefined, distanceThreshold: double | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 | this function callback executed when the click action is recognized |
| distanceThreshold | double \| undefined | 是 | the distance threshold of finger's movement when detecting a click action@default (2^31-1)vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onDetach

```TypeScript
default onDetach(callback: VoidCallback | undefined): this
```

This callback is triggered when a component is detached from view tree.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onDetach(callback: VoidCallback | undefined): this--><!--Device-CommonMethod-default onDetach(callback: VoidCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onDigitalCrown

```TypeScript
default onDigitalCrown(handler: Callback<CrownEvent> | undefined): this
```

Digital crown input.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onDigitalCrown(handler: Callback<CrownEvent> | undefined): this--><!--Device-CommonMethod-default onDigitalCrown(handler: Callback<CrownEvent> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onDisAppear

```TypeScript
default onDisAppear(event: (() => void) | undefined): this
```

This callback is triggered when component uninstallation disappears.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onDisAppear(event: (() => void) | undefined): this--><!--Device-CommonMethod-default onDisAppear(event: (() => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (() =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onDragEnd

```TypeScript
default onDragEnd(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this
```

This function is called when the drag event is end.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onDragEnd(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this--><!--Device-CommonMethod-default onDragEnd(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ((event: DragEvent, extraParams?: string) =&gt; void) \| undefined | 是 | indicates the function to be called. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return the component attribute. |

## onDragEnter

```TypeScript
default onDragEnter(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this
```

After binding, a callback is triggered when the component is dragged to the range of the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onDragEnter(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this--><!--Device-CommonMethod-default onDragEnter(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ((event: DragEvent, extraParams?: string) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onDragLeave

```TypeScript
default onDragLeave(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this
```

After binding, a callback is triggered when the component is dragged out of the component range.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onDragLeave(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this--><!--Device-CommonMethod-default onDragLeave(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ((event: DragEvent, extraParams?: string) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onDragMove

```TypeScript
default onDragMove(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this
```

After binding, a callback is triggered when the drag moves within the range of a placeable component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onDragMove(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this--><!--Device-CommonMethod-default onDragMove(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ((event: DragEvent, extraParams?: string) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onDragSpringLoading

```TypeScript
default onDragSpringLoading(callback: Callback<SpringLoadingContext> | null | undefined, configuration?: DragSpringLoadingConfiguration): this
```

Enables the component as a drag-and-drop target with spring loading functionality. When a dragged object hovers over the target, it triggers a callback notification. Spring Loading is an enhanced feature for drag-and-drop operations, allowing users to automatically trigger view transitions during dragging by hovering (hover) without needing to use another hand. This feature is primarily designed to enhance the smoothness and efficiency of drag-and-drop operations. Below are some common scenarios suitable for supporting this feature: - In a file manager, when dragging a file and hovering over a folder, the folder is automatically opened. - On a desktop launcher, when dragging a file and hovering over an application icon, the application is automatically opened.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onDragSpringLoading(callback: Callback<SpringLoadingContext> | null | undefined, configuration?: DragSpringLoadingConfiguration): this--><!--Device-CommonMethod-default onDragSpringLoading(callback: Callback<SpringLoadingContext> | null | undefined, configuration?: DragSpringLoadingConfiguration): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| null \| undefined | 是 | Registers the callback for spring loading response, or |
| configuration | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | The initialized spring loading configuration which is |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | - return the component attribute. |

## onDragStart

```TypeScript
default onDragStart(event: ((event: DragEvent, extraParams?: string) => CustomBuilder | DragItemInfo) | undefined): this
```

After a listener is bound, the component can be dragged. After the drag occurs, a callback is triggered. (To be triggered, press and hold for 170 milliseconds (ms)) \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_:\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ The global builder is not supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onDragStart(event: ((event: DragEvent, extraParams?: string) => CustomBuilder | DragItemInfo) | undefined): this--><!--Device-CommonMethod-default onDragStart(event: ((event: DragEvent, extraParams?: string) => CustomBuilder | DragItemInfo) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ((event: DragEvent, extraParams?: string) =&gt; CustomBuilder \| DragItemInfo) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onDrop

```TypeScript
default onDrop(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this
```

The component bound to this event can be used as the drag release target. This callback is triggered when the drag behavior is stopped within the scope of the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onDrop(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this--><!--Device-CommonMethod-default onDrop(event: ((event: DragEvent, extraParams?: string) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ((event: DragEvent, extraParams?: string) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onDrop

```TypeScript
default onDrop(eventCallback: OnDragEventCallback | undefined, dropOptions: DropOptions): this
```

The component bound to this event can be used as the drag release target. This callback is triggered when the drag behavior is stopped within the scope of the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onDrop(eventCallback: OnDragEventCallback | undefined, dropOptions: DropOptions): this--><!--Device-CommonMethod-default onDrop(eventCallback: OnDragEventCallback | undefined, dropOptions: DropOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventCallback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | event callback. |
| dropOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | the drop handling options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onFocus

```TypeScript
default onFocus(event: (() => void) | undefined): this
```

Trigger a event when got focus.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onFocus(event: (() => void) | undefined): this--><!--Device-CommonMethod-default onFocus(event: (() => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (() =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onFocusAxisEvent

```TypeScript
default onFocusAxisEvent(event: Callback<FocusAxisEvent> | undefined): this
```

Trigger a FocusAxisEvent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onFocusAxisEvent(event: Callback<FocusAxisEvent> | undefined): this--><!--Device-CommonMethod-default onFocusAxisEvent(event: Callback<FocusAxisEvent> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onGestureCollectIntercept

```TypeScript
default onGestureCollectIntercept(callback: GestureCollectInterceptCallback): this
```

When the events and gestures on this node and higher-priority nodes have been collected, the callback is executed. This callback is used to intervene in the event and gesture collection results.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onGestureCollectIntercept(callback: GestureCollectInterceptCallback): this--><!--Device-CommonMethod-default onGestureCollectIntercept(callback: GestureCollectInterceptCallback): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | A callback instance used when the component does a touch test. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onGestureJudgeBegin

```TypeScript
default onGestureJudgeBegin(callback: ((gestureInfo: GestureInfo, event: BaseGestureEvent) => GestureJudgeResult) | undefined): this
```

When a gesture bound to this component will be accepted, a user-defined callback is triggered to get the result

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onGestureJudgeBegin(callback: ((gestureInfo: GestureInfo, event: BaseGestureEvent) => GestureJudgeResult) | undefined): this--><!--Device-CommonMethod-default onGestureJudgeBegin(callback: ((gestureInfo: GestureInfo, event: BaseGestureEvent) => GestureJudgeResult) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ((gestureInfo: GestureInfo, event: BaseGestureEvent) =&gt; GestureJudgeResult) \| undefined | 是 | A callback instance used when a gesture bound to this component will be accepted. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onGestureRecognizerJudgeBegin

```TypeScript
default onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback | undefined): this
```

Binds a custom gesture recognizer judgment callback to the component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback | undefined): this--><!--Device-CommonMethod-default onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | A callback instance used when a gesture bound to this component will be accepted. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onGestureRecognizerJudgeBegin

```TypeScript
default onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback | undefined, exposeInnerGesture: boolean | undefined): this
```

Binds a custom gesture recognizer judgment callback to the component. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_: \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_ For a composite component, setting exposeInnerGesture to true exposes the internal gesture recognizer of the \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_ composite component in the current parameter callback. Currently, only the Tabs component is supported. \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_ Do not set exposeInnerGesture for other components. When exposeInnerGesture is set to false, this API provides the same functionality \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_ as the onGestureRecognizerJudgeBegin API. \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback | undefined, exposeInnerGesture: boolean | undefined): this--><!--Device-CommonMethod-default onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback | undefined, exposeInnerGesture: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | A callback instance used when a gesture bound to this component will be accepted. |
| exposeInnerGesture | boolean \| undefined | 是 | This parameter is a flag. This flag determines whether to expose internal gestures. The default value is false. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onHover

```TypeScript
default onHover(event: ((isHover: boolean, event: HoverEvent) => void) | undefined): this
```

Trigger a hover event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onHover(event: ((isHover: boolean, event: HoverEvent) => void) | undefined): this--><!--Device-CommonMethod-default onHover(event: ((isHover: boolean, event: HoverEvent) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ((isHover: boolean, event: HoverEvent) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onHoverMove

```TypeScript
default onHoverMove(event: Callback<HoverEvent> | undefined): this
```

Trigger a hover move event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onHoverMove(event: Callback<HoverEvent> | undefined): this--><!--Device-CommonMethod-default onHoverMove(event: Callback<HoverEvent> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onKeyEvent

```TypeScript
default onKeyEvent(event: Callback<KeyEvent, boolean> | undefined): this
```

Keyboard input

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onKeyEvent(event: Callback<KeyEvent, boolean> | undefined): this--><!--Device-CommonMethod-default onKeyEvent(event: Callback<KeyEvent, boolean> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_, boolean&gt; \| undefined | 是 | Callback for handling the key event. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onKeyEventDispatch

```TypeScript
default onKeyEventDispatch(event: Callback<KeyEvent, boolean> | undefined): this
```

Customize the handling and distribution of key events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onKeyEventDispatch(event: Callback<KeyEvent, boolean> | undefined): this--><!--Device-CommonMethod-default onKeyEventDispatch(event: Callback<KeyEvent, boolean> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_, boolean&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onKeyPreIme

```TypeScript
default onKeyPreIme(event: Callback<KeyEvent, boolean> | undefined): this
```

Handle keyboard events before input method events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onKeyPreIme(event: Callback<KeyEvent, boolean> | undefined): this--><!--Device-CommonMethod-default onKeyPreIme(event: Callback<KeyEvent, boolean> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_, boolean&gt; \| undefined | 是 | Callback for handling the key event. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onMouse

```TypeScript
default onMouse(event: ((event: MouseEvent) => void) | undefined): this
```

Triggered when the component is clicked by a mouse button or the mouse pointer moves on the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onMouse(event: ((event: MouseEvent) => void) | undefined): this--><!--Device-CommonMethod-default onMouse(event: ((event: MouseEvent) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ((event: MouseEvent) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onNeedSoftkeyboard

```TypeScript
default onNeedSoftkeyboard(onNeedSoftkeyboardCallback: OnNeedSoftkeyboardCallback | undefined): this
```

Called when component is focused, the return value indicates whether keyboard is needed.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onNeedSoftkeyboard(onNeedSoftkeyboardCallback: OnNeedSoftkeyboardCallback | undefined): this--><!--Device-CommonMethod-default onNeedSoftkeyboard(onNeedSoftkeyboardCallback: OnNeedSoftkeyboardCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onNeedSoftkeyboardCallback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onPreDrag

```TypeScript
default onPreDrag(callback: Callback<PreDragStatus> | undefined): this
```

After binding, a callback is triggered when the preDrag status change finished.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onPreDrag(callback: Callback<PreDragStatus> | undefined): this--><!--Device-CommonMethod-default onPreDrag(callback: Callback<PreDragStatus> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 | callback - The callback will be triggered when the preDrag status change. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return the component attribute. |

## onSizeChange

```TypeScript
default onSizeChange(event: SizeChangeCallback | undefined): this
```

This callback is triggered when the component size changes due to layout updates. This event is not triggered for render attribute changes caused by re-rendering.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onSizeChange(event: SizeChangeCallback | undefined): this--><!--Device-CommonMethod-default onSizeChange(event: SizeChangeCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | event callback. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onTouch

```TypeScript
default onTouch(event: ((event: TouchEvent) => void) | undefined): this
```

Invoked when a touch event is triggered.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onTouch(event: ((event: TouchEvent) => void) | undefined): this--><!--Device-CommonMethod-default onTouch(event: ((event: TouchEvent) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ((event: TouchEvent) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onTouchIntercept

```TypeScript
default onTouchIntercept(callback: Callback<TouchEvent, HitTestMode> | undefined): this
```

When the component does a touch test, a user-defined callback is triggered.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onTouchIntercept(callback: Callback<TouchEvent, HitTestMode> | undefined): this--><!--Device-CommonMethod-default onTouchIntercept(callback: Callback<TouchEvent, HitTestMode> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_, \_\_\_MD\_LINK\_USD\_2\_\_\_&gt; \| undefined | 是 | A callback instance used when the component does a touch test. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onTouchTestDone

```TypeScript
default onTouchTestDone(callback: TouchTestDoneCallback | undefined): this
```

Register one callback which will be executed when all gesture recognizers are collected done, this happens when user touchs down, the system do hit test process and collect gesture recognizers base on the touch position, after this, before handling any move events, the component can use this interface to know which gesture recognizers will participate in the recognition and competing with each other.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onTouchTestDone(callback: TouchTestDoneCallback | undefined): this--><!--Device-CommonMethod-default onTouchTestDone(callback: TouchTestDoneCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | A callback instance used when all gesture recognizers are collected. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onVisibleAreaApproximateChange

```TypeScript
default onVisibleAreaApproximateChange(options: VisibleAreaEventOptions | undefined, event: VisibleAreaChangeCallback | undefined): this
```

Set or reset the callback which is triggered when the visibleArea of component changed. The interval between two visible area change callbacks will not be less than the expected update interval.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onVisibleAreaApproximateChange(options: VisibleAreaEventOptions | undefined, event: VisibleAreaChangeCallback | undefined): this--><!--Device-CommonMethod-default onVisibleAreaApproximateChange(options: VisibleAreaEventOptions | undefined, event: VisibleAreaChangeCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | The options for the visibility event. |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | The callback will be triggered when the visibleArea of component changed and get close to any number in ratios defined by options.If set undefined will reset the target callback. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onVisibleAreaChange

```TypeScript
default onVisibleAreaChange(ratios: Array<double> | undefined, event: VisibleAreaChangeCallback | undefined): this
```

Trigger a visible area change event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onVisibleAreaChange(ratios: Array<double> | undefined, event: VisibleAreaChangeCallback | undefined): this--><!--Device-CommonMethod-default onVisibleAreaChange(ratios: Array<double> | undefined, event: VisibleAreaChangeCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ratios | Array&lt;double&gt; \| undefined | 是 | Threshold array. Each threshold represents a ratio of the component's visible area to the component's total area. The value range of the threshold is [0.0, 1.0]. |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Callback for visible area changes of the component. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onVisibleAreaChange

```TypeScript
default onVisibleAreaChange(ratios: Array<double> | undefined, event: VisibleAreaChangeCallback | undefined, measureFromViewport: boolean | undefined): this
```

Trigger a visible area change event.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default onVisibleAreaChange(ratios: Array<double> | undefined, event: VisibleAreaChangeCallback | undefined, measureFromViewport: boolean | undefined): this--><!--Device-CommonMethod-default onVisibleAreaChange(ratios: Array<double> | undefined, event: VisibleAreaChangeCallback | undefined, measureFromViewport: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ratios | Array&lt;double&gt; \| undefined | 是 | Threshold array. Each threshold represents a ratio of the component's visible area to the component's total area. The value range of the threshold is [0.0, 1.0]. |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Callback for visible area changes of the component. |
| measureFromViewport | boolean \| undefined | 是 | When this parameter is set to true, the parts of the component that exceed the parent component's area will also be included in the visible area calculation.However, this only applies if the parent component does not explicitly set the clip property to true.If the parent component sets clip to true, regardless of the value of this parameter, the parts that exceed the parent component's area will still be treated as invisible in the visible area calculation. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## opacity

```TypeScript
default opacity(value: double | Resource | undefined): this
```

设置组件的不透明度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default opacity(value: double | Resource | undefined): this--><!--Device-CommonMethod-default opacity(value: double | Resource | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| Resource \| undefined | 是 | 元素的不透明度，取值范围为0到1，若设置的值小于0时，则取值为0，若设置的值大于1时，则取值为1，1表示不透明，0表示完全透明，达到隐藏组件效果，但是在布局中占位。 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 默认值：1 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：** \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 子组件会继承父组件的透明度，并与自身的透明度属性叠加。如：父组件透明度为0.1，子组件设置透明度为0.8，则子组件实际透明度为0.1*0.8=0.08。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当opacity的值为undefined时，恢复为默认不透明度为1的状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## outline

```TypeScript
default outline(value: OutlineOptions | undefined): this
```

Sets the outline attributes in one declaration.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default outline(value: OutlineOptions | undefined): this--><!--Device-CommonMethod-default outline(value: OutlineOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Outline attributes. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## outlineColor

```TypeScript
default outlineColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors | undefined): this
```

Sets the color of the outline.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default outlineColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors | undefined): this--><!--Device-CommonMethod-default outlineColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| EdgeColors \| LocalizedEdgeColors \| undefined | 是 | Outline color.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **Color.Black**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## outlineRadius

```TypeScript
default outlineRadius(value: Dimension | OutlineRadiuses | undefined): this
```

Sets the radius of the outline corners.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default outlineRadius(value: Dimension | OutlineRadiuses | undefined): this--><!--Device-CommonMethod-default outlineRadius(value: Dimension | OutlineRadiuses | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| OutlineRadiuses \| undefined | 是 | adius of the outline corners. Percentage values are not supported.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **0**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Maximum effective value: Component width/2 + outlineWidth or component height/2 + outlineWidth. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## outlineStyle

```TypeScript
default outlineStyle(value: OutlineStyle | EdgeOutlineStyles | undefined): this
```

Sets the style of the outline.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default outlineStyle(value: OutlineStyle | EdgeOutlineStyles | undefined): this--><!--Device-CommonMethod-default outlineStyle(value: OutlineStyle | EdgeOutlineStyles | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| EdgeOutlineStyles \| undefined | 是 | Outline style.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **OutlineStyle.SOLID**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## outlineWidth

```TypeScript
default outlineWidth(value: Dimension | EdgeOutlineWidths | undefined): this
```

Sets the thickness of the outline.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default outlineWidth(value: Dimension | EdgeOutlineWidths | undefined): this--><!--Device-CommonMethod-default outlineWidth(value: Dimension | EdgeOutlineWidths | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| EdgeOutlineWidths \| undefined | 是 | Outline thickness. Percentage values are not supported.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **0**Outline thickness. Percentage values are not supported.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **0**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## overlay

```TypeScript
default overlay(value: string | CustomBuilder | ComponentContent<Object> | undefined, options?: OverlayOptions): this
```

Add mask text to the current component. The layout is the same as that of the current component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default overlay(value: string | CustomBuilder | ComponentContent<Object> | undefined, options?: OverlayOptions): this--><!--Device-CommonMethod-default overlay(value: string | CustomBuilder | ComponentContent<Object> | undefined, options?: OverlayOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| CustomBuilder \| ComponentContent&lt;Object&gt; \| undefined | 是 |  |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## padding

```TypeScript
default padding(value: Padding | Length | LocalizedPadding | undefined): this
```

Sets the padding of the component. Default value: **0**.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default padding(value: Padding | Length | LocalizedPadding | undefined): this--><!--Device-CommonMethod-default padding(value: Padding | Length | LocalizedPadding | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Length \| LocalizedPadding \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## parallelGesture

```TypeScript
default parallelGesture(gesture: GestureType, mask?: GestureMask): this
```

Binding gestures that can be triggered simultaneously with internal component gestures gesture:Bound Gesture Type,mask:GestureMask;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default parallelGesture(gesture: GestureType, mask?: GestureMask): this--><!--Device-CommonMethod-default parallelGesture(gesture: GestureType, mask?: GestureMask): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesture | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 |  |
| mask | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## pixelRound

```TypeScript
default pixelRound(value: PixelRoundPolicy | undefined): this
```

Sets the pixel rounding policy for the current component in the specified direction. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_If a direction is not set, the pixels are rounded to the nearest whole number in that direction.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default pixelRound(value: PixelRoundPolicy | undefined): this--><!--Device-CommonMethod-default pixelRound(value: PixelRoundPolicy | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | indicates the rounding policy for the bounds of the component. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## pixelStretchEffect

```TypeScript
default pixelStretchEffect(options: PixelStretchEffectOptions | undefined): this
```

Applies a pixel stretch effect to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default pixelStretchEffect(options: PixelStretchEffectOptions | undefined): this--><!--Device-CommonMethod-default pixelStretchEffect(options: PixelStretchEffectOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Pixel stretch effect options.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_The value includes the length by which a pixel is stretched toward the four edges.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**NOTE**:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1. If the length is a positive value, the original image is stretched, and the image size increases. The edge pixels grow by the set length toward the top, bottom, left, and right edges.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. If the length is a negative value, the original image shrinks as follows, but the image size remains unchanged:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Shrinking mode:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_(1) The image shrinks from the four edges by the absolute value of length set through **options**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_(2) The image is stretched back to the original size with edge pixels.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_7\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_3. Constraints on **options**:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_8\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_(1) The length values for the four edges must be all positive or all negative. That is, the four edges are stretched or shrink at the same time in the same direction.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_9\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_(2) The length values must all be a percentage or a specific value. Combined use of the percentage and specific value is not allowed.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_10\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_(3) If the input value is invalid, the image is displayed as {0, 0, 0, 0}, that is, the image is the same as the original image.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_11\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## position

```TypeScript
default position(value: Position | Edges | LocalizedEdges | undefined): this
```

Sets the absolute position of the component relative to the position of the parent component. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_The attribute is not available for a layout container whose width and height are zero.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default position(value: Position | Edges | LocalizedEdges | undefined): this--><!--Device-CommonMethod-default position(value: Position | Edges | LocalizedEdges | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Edges \| LocalizedEdges \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## priorityGesture

```TypeScript
default priorityGesture(gesture: GestureType, mask?: GestureMask): this
```

Binding Preferential Recognition Gestures gesture:Bound Gesture Type,mask:GestureMask;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default priorityGesture(gesture: GestureType, mask?: GestureMask): this--><!--Device-CommonMethod-default priorityGesture(gesture: GestureType, mask?: GestureMask): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesture | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 |  |
| mask | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## radialGradient

```TypeScript
default radialGradient(value: RadialGradientOptions | undefined): this
```

Creates a radial gradient. Anonymous Object Rectification.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default radialGradient(value: RadialGradientOptions | undefined): this--><!--Device-CommonMethod-default radialGradient(value: RadialGradientOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Radial gradient.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- **center**: center of the radial gradient, that is, the coordinates relative to the upper left corner of the current component.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- **radius**: radius of the radial gradient.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ Value range: [0, +∞).\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**NOTE**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_A value less than 0 is treated as **0**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- colors: array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- **repeating**: whether the colors are repeated.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_7\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ Default value: **false**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## renderFit

```TypeScript
default renderFit(fitMode: RenderFit | undefined): this
```

设置宽高动画过程中的组件内容填充方式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default renderFit(fitMode: RenderFit | undefined): this--><!--Device-CommonMethod-default renderFit(fitMode: RenderFit | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fitMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 设置宽高动画过程中的组件内容填充方式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当fitMode的值为undefined时，取默认值。恢复为内容填充方式为RenderFit.TOP\_\_\_ESCAPED\_UNDERSCORE\_\_\_LEFT的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## renderGroup

```TypeScript
default renderGroup(value: boolean | undefined): this
```

Sets whether the component and its child components are rendered off the screen as a whole before being blended with its parent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default renderGroup(value: boolean | undefined): this--><!--Device-CommonMethod-default renderGroup(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | Whether the component and its child components are rendered off the screen as a whole before being blended with its parent. If the opacity of the component is not 1, the drawing effect may vary depending on the value.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **false**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ The value **true** means the component and its child components are rendered off the screen as a whole, and **false** means the opposite. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## responseRegion

```TypeScript
default responseRegion(value: Array<Rectangle> | Rectangle | undefined): this
```

Sets the response region of the current component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default responseRegion(value: Array<Rectangle> | Rectangle | undefined): this--><!--Device-CommonMethod-default responseRegion(value: Array<Rectangle> | Rectangle | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| Rectangle \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## responseRegionList

```TypeScript
default responseRegionList(regions: Array<ResponseRegion> | undefined): this
```

Sets the response region list of the current component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default responseRegionList(regions: Array<ResponseRegion> | undefined): this--><!--Device-CommonMethod-default responseRegionList(regions: Array<ResponseRegion> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| regions | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return the component attribute |

## restoreId

```TypeScript
default restoreId(value: int | undefined): this
```

id for distribute identification.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default restoreId(value: int | undefined): this--><!--Device-CommonMethod-default restoreId(value: int | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## reuse

```TypeScript
default reuse(options: ReuseOptions | undefined): this
```

Reuse id is used for identify the reuse type of each @ComponentV2 custom component, which can give user control of sub-component recycle and reuse.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default reuse(options: ReuseOptions | undefined): this--><!--Device-CommonMethod-default reuse(options: ReuseOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | The configuration parameter for reusable custom component. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## reuseId

```TypeScript
default reuseId(id: string | undefined): this
```

Reuse id is used for identify the reuse type for each custom node.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default reuseId(id: string | undefined): this--><!--Device-CommonMethod-default reuseId(id: string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string \| undefined | 是 | The id for reusable custom node. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## rotate

```TypeScript
default rotate(value: RotateOptions | RotateAngleOptions | undefined): this
```

设置组件旋转。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default rotate(value: RotateOptions | RotateAngleOptions | undefined): this--><!--Device-CommonMethod-default rotate(value: RotateOptions | RotateAngleOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| RotateAngleOptions \| undefined | 是 | 可使组件在以组件左上角为坐标原点的坐标系中进行旋转。其中，(x, y, z）指定一个矢量，作为旋转轴；或使用(angleX, angleY, angleZ）指定三个轴方向上的旋转角。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：{\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_centerX: '50%',\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_centerY: '50%',\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_centerZ: 0,\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_perspective: 0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_}\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value的值为undefined时，恢复为无旋转效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## safeAreaPadding

```TypeScript
default safeAreaPadding(paddingValue: Padding | LengthMetrics | LocalizedPadding | undefined): this
```

Sets the safe area padding. It enables a container to add a component-level safe area for child components to expand into. Default value: **LengthMetrics.vp(0)**

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default safeAreaPadding(paddingValue: Padding | LengthMetrics | LocalizedPadding | undefined): this--><!--Device-CommonMethod-default safeAreaPadding(paddingValue: Padding | LengthMetrics | LocalizedPadding | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| paddingValue | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| LengthMetrics \| LocalizedPadding \| undefined | 是 | Indicates safeArea padding values |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## saturate

```TypeScript
default saturate(value: double | undefined): this
```

Applies a saturation effect to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default saturate(value: double | undefined): this--><!--Device-CommonMethod-default saturate(value: double | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| undefined | 是 | Saturation of the component. The saturation is the ratio of the chromatic component to the achromatic component (gray) in a color. If the value is **1**,the original image is displayed. If the value is greater than **1**, a higher percentage of the chromatic component indicates a higher saturation. If the value is less than **1**, a higher percentage of the achromatic component indicates a lower saturation. The unit is percentage.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **1.0**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Recommended value range: [0, 50).\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**NOTE**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_A value less than 0 evaluates to the value **0**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## scale

```TypeScript
default scale(value: ScaleOptions | undefined): this
```

设置组件缩放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default scale(value: ScaleOptions | undefined): this--><!--Device-CommonMethod-default scale(value: ScaleOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 可以分别设置X轴、Y轴、Z轴的缩放比例，默认值为1，同时可以通过centerX和centerY设置缩放的中心点。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：{\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_x: 1,\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_y: 1,\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_z: 1,\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_centerX:'50%',\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_centerY:'50%'\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_}\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_7\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value的值为undefined时，恢复为无缩放效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## sepia

```TypeScript
default sepia(value: double | undefined): this
```

Sepia conversion ratio of the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default sepia(value: double | undefined): this--><!--Device-CommonMethod-default sepia(value: double | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| undefined | 是 | Sepia conversion ratio of the component. If the value is **1**, the image is completely sepia. If the value is **0**, the component remains unchanged. The unit is percentage.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ Value range: [0, +∞). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## shadow

```TypeScript
default shadow(value: ShadowOptions | ShadowStyle | undefined): this
```

Applies a shadow effect to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default shadow(value: ShadowOptions | ShadowStyle | undefined): this--><!--Device-CommonMethod-default shadow(value: ShadowOptions | ShadowStyle | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ShadowStyle \| undefined | 是 | Shadow of the component.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_When the value type is **ShadowOptions**, the blur radius, shadow color,and offset along the x-axis and y-axis can be specified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_When the value type is **ShadowStyle**, the shadow style can be specified. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## sharedTransition

```TypeScript
default sharedTransition(id: string | undefined, options?: sharedTransitionOptions): this
```

设置共享元素转场动效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default sharedTransition(id: string | undefined, options?: sharedTransitionOptions): this--><!--Device-CommonMethod-default sharedTransition(id: string | undefined, options?: sharedTransitionOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string \| undefined | 是 | 两个页面中id值相同且不为空字符串的组件即为共享元素，在页面转场时可显示共享元素转场动效。当id的值为undefined时，共享元素转场不生效。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 共享元素转场动画参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## shouldBuiltInRecognizerParallelWith

```TypeScript
default shouldBuiltInRecognizerParallelWith(callback: ShouldBuiltInRecognizerParallelWithCallback | undefined): this
```

Provides a callback to set the parallel relationship between built-in gestures and gestures of other components in the response chain.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default shouldBuiltInRecognizerParallelWith(callback: ShouldBuiltInRecognizerParallelWithCallback | undefined): this--><!--Device-CommonMethod-default shouldBuiltInRecognizerParallelWith(callback: ShouldBuiltInRecognizerParallelWithCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | A callback instance used when a component is doing touch test. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## shouldRecognizerParallelWith

```TypeScript
default shouldRecognizerParallelWith(callback: ShouldRecognizerParallelWithCallback | undefined): this
```

Provides a callback to set the parallel relationship between gestures of current component and gestures of other components in the response chain.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default shouldRecognizerParallelWith(callback: ShouldRecognizerParallelWithCallback | undefined): this--><!--Device-CommonMethod-default shouldRecognizerParallelWith(callback: ShouldRecognizerParallelWithCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | A callback instance used when a component is doing touch test. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## size

```TypeScript
default size(value: SizeOptions | undefined): this
```

Sets the size of the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default size(value: SizeOptions | undefined): this--><!--Device-CommonMethod-default size(value: SizeOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## smartGestureShortcut

```TypeScript
default smartGestureShortcut(options?: SmartGestureShortcutOptions): this
```

Enable or disable specific smart gesture shortcuts, and set response priorities for them.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default smartGestureShortcut(options?: SmartGestureShortcutOptions): this--><!--Device-CommonMethod-default smartGestureShortcut(options?: SmartGestureShortcutOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Options for configuring smart gesture shortcuts. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return component instance who call the method. |

## sphericalEffect

```TypeScript
default sphericalEffect(value: double | undefined): this
```

Applies a spherical effect to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default sphericalEffect(value: double | undefined): this--><!--Device-CommonMethod-default sphericalEffect(value: double | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| undefined | 是 | Spherical degree of the component.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_The value ranges from 0 to 1.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**NOTE**:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1. If the value is **0**, the component remains unchanged. If the value is 1, the component is completely spherical. Between **0** and **1**, a larger value indicates a higher spherical degree. A value less than 0 is handled as the value **0**. A value greater than 1 is handled as the value **1**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. The component's shadow and outer stroke do not support spherical effects.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_3. If the value is greater than 0, the component is frozen and not updated, and its content is drawn to the transparent offscreen buffer. To update the component attributes, set the value to **0**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## stateStyles

```TypeScript
default stateStyles(value: StateStyles | undefined): this
```

Sets styles for component state.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default stateStyles(value: StateStyles | undefined): this--><!--Device-CommonMethod-default stateStyles(value: StateStyles | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## sweepGradient

```TypeScript
default sweepGradient(value: SweepGradientOptions | undefined): this
```

Creates a sweep gradient.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default sweepGradient(value: SweepGradientOptions | undefined): this--><!--Device-CommonMethod-default sweepGradient(value: SweepGradientOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Sweep gradient, which can sweep around the specified center point in the 0–360 degree range. If the rotation angle exceeds the range, a monochrome color instead of a gradient will be drawn.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- **center**: center of the sweep gradient, that is, the coordinates relative to the upper left corner of the current component.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- **start**: start angle of the sweep gradient.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ Default value: **0**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_If the angle is specified with a string, only the deg, grad, rad,and turn types are supported.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- **end**: end angle of the sweep gradient.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ Default value: **0**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_If the angle is specified with a string, only the deg, grad, rad,and turn types are supported.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_7\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- **rotation**: rotation angle of the sweep gradient.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_8\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ Default value: **0**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_9\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_If the angle is specified with a string, only the deg, grad, rad,and turn types are supported.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_10\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- colors: array of color stops,each of which consists of a color and its stop position. Invalid colors are automatically skipped.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_11\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- **repeating**: whether the colors are repeated.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_12\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ Default value: **false**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_13\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**NOTE**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_14\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_A value less than 0 is treated as **0**. A value greater than 360 is treated as **360**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_15\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_When **start**, **end**, or **rotation** is specified with a string, the string must be a number or a number followed by one of the following units: deg, rad, grad, and turn. Valid value examples are "90", "90deg", and "1.57rad". |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## systemBarEffect

```TypeScript
default systemBarEffect(): this
```

Applies a system bar effect to the component, which means to invert colors based on the background and add a blur.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default systemBarEffect(): this--><!--Device-CommonMethod-default systemBarEffect(): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return the component attribute. |

## systemMaterial

```TypeScript
default systemMaterial(material: SystemUiMaterial | undefined): this
```

Set system-styled materials for the component. The material effect behaves differently on devices with different level of computing powers. On devices with lower computing power, it affects attributes such as the backgroundColor, borderWidth, borderColor, shadow. On devices with higher computing power, it adds a filter effect at the system material layer, which can produce an effect similar to glass.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default systemMaterial(material: SystemUiMaterial | undefined): this--><!--Device-CommonMethod-default systemMaterial(material: SystemUiMaterial | undefined): this-End-->

**系统能力：** 
- API版本23+：SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| material | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | System-styled material. Undefined indicates reverting to the effect of no system material.\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 23 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## tabIndex

```TypeScript
default tabIndex(index: int | undefined): this
```

Set focus index by key tab. The tabIndex and focusScopeId cannot be used together.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default tabIndex(index: int | undefined): this--><!--Device-CommonMethod-default tabIndex(index: int | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## tabStop

```TypeScript
default tabStop(isTabStop: boolean | undefined): this
```

Set TabStop on component focus

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default tabStop(isTabStop: boolean | undefined): this--><!--Device-CommonMethod-default tabStop(isTabStop: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isTabStop | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## toolbar

```TypeScript
default toolbar(value: CustomBuilder | undefined): this
```

Config toolbar for current component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default toolbar(value: CustomBuilder | undefined): this--><!--Device-CommonMethod-default toolbar(value: CustomBuilder | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## transform

```TypeScript
default transform(value: Matrix4Transit | undefined): this
```

可用于显示二维变换时的矩阵变换。包含三维变换时应使用[transform3D]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default transform(value: Matrix4Transit | undefined): this--><!--Device-CommonMethod-default transform(value: Matrix4Transit | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 设置当前组件的变换矩阵。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value的值为undefined时，恢复为单位矩阵的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## transform3D

```TypeScript
default transform3D(transform: Matrix4Transit | undefined): this
```

设置组件的三维变换矩阵。当涉及包含透视效果的三维变换时，transform接口显示效果可能有误，推荐使用transform3D接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default transform3D(transform: Matrix4Transit | undefined): this--><!--Device-CommonMethod-default transform3D(transform: Matrix4Transit | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transform | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 三维变换矩阵。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当transform的值为undefined时，恢复为单位矩阵的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## transition

```TypeScript
default transition(value: TransitionEffect | undefined): this
```

设置组件插入时显示和删除时隐藏的过渡效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default transition(value: TransitionEffect | undefined): this--><!--Device-CommonMethod-default transition(value: TransitionEffect | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 设置组件插入时显示和删除时隐藏的过渡效果。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：** \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_详细描述[TransitionEffect]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_对象说明。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value的值为undefined时，无过渡效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## transition

```TypeScript
default transition(effect: TransitionEffect | undefined, onFinish: TransitionFinishCallback | undefined): this
```

设置组件插入时显示和删除时隐藏的过渡效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default transition(effect: TransitionEffect | undefined, onFinish: TransitionFinishCallback | undefined): this--><!--Device-CommonMethod-default transition(effect: TransitionEffect | undefined, onFinish: TransitionFinishCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 设置组件插入时显示和删除时隐藏的过渡效果。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：** \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_详细描述[TransitionEffect]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_对象说明。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value的值为undefined时，无过渡效果。 |
| onFinish | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 转场动画结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## translate

```TypeScript
default translate(value: TranslateOptions | undefined): this
```

设置组件平移。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default translate(value: TranslateOptions | undefined): this--><!--Device-CommonMethod-default translate(value: TranslateOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 可使组件在以组件左上角为坐标原点的坐标系中进行移动。其中，x，y，z的值分别表示在对应轴移动的距离，值为正时表示向对应轴的正向移动，值为负时表示向对应轴的反向移动。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：{\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_x: 0,\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_y: 0,\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_z: 0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_}\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当value的值为undefined时，恢复为无平移效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## useEffect

```TypeScript
default useEffect(useEffect: boolean | undefined, effectType: EffectType | undefined): this
```

Specifies whether to apply the effect defined by \_\_\_MD\_COMMENT\_DESC\_USD\_1\_\_\_the parent \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ or \_\_\_MD\_COMMENT\_DESC\_USD\_2\_\_\_the window.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default useEffect(useEffect: boolean | undefined, effectType: EffectType | undefined): this--><!--Device-CommonMethod-default useEffect(useEffect: boolean | undefined, effectType: EffectType | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| useEffect | boolean \| undefined | 是 | Whether to apply the effect defined by \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_the parent **EffectComponent** or \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_the window.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_The value **true** means to apply the effect defined by \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_the parent **EffectComponent** or \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_the window.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **false**. |
| effectType | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Type of effect to apply to the component, which is defined by\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_the parent **EffectComponent** or \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_the window.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **EffectType.DEFAULT**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return the component attribute. |

## useEffect

```TypeScript
default useEffect(value: boolean | undefined): this
```

Specifies whether to combine the drawing of special effects, such as background blur.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default useEffect(value: boolean | undefined): this--><!--Device-CommonMethod-default useEffect(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | Whether the component inherits the special effect settings of the **EffectComponent** component.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_The value **true** means that the component inherits the special effect settings of the **EffectComponent** component, and **false** means the opposite.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **false**. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return the component attribute. |

## useShadowBatching

```TypeScript
default useShadowBatching(value: boolean | undefined): this
```

Sets whether to draw shadows of child nodes in the component at the same layer, so that the shadows of elements at the same layer overlap.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default useShadowBatching(value: boolean | undefined): this--><!--Device-CommonMethod-default useShadowBatching(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | Whether to draw shadows of child nodes in the component at the same layer, so that the shadows of elements at the same layer overlap.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: **false**.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**NOTE**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1. When this feature is disabled (default), if the shadow radius of a child node is large, the shadows of the child nodes may overlap. This overlap issue does not occur when the feature is enabled.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Avoid nesting **useShadowBatching**. When used in nested mode, **useShadowBatching** takes effect for the current child node only and cannot be recursively used. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## visibility

```TypeScript
default visibility(value: Visibility | undefined): this
```

Controls the display or hide of the current component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default visibility(value: Visibility | undefined): this--><!--Device-CommonMethod-default visibility(value: Visibility | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Whether the component is visible. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## visualEffect

```TypeScript
default visualEffect(effect: VisualEffect | undefined): this
```

设置非滤镜视觉效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default visualEffect(effect: VisualEffect | undefined): this--><!--Device-CommonMethod-default visualEffect(effect: VisualEffect | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 非滤镜视觉效果。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当effect的值为undefined时，无非滤镜视觉效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## width

```TypeScript
default width(widthValue: Length | LayoutPolicy | undefined): this
```

Sets the width of the component or its horizontal layout policy. By default, the component uses the width required for its content. If the width of the component is greater than that of the parent container, the component will be drawn beyond the parent container scope.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default width(widthValue: Length | LayoutPolicy | undefined): this--><!--Device-CommonMethod-default width(widthValue: Length | LayoutPolicy | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| widthValue | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| LayoutPolicy \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## zIndex

```TypeScript
default zIndex(value: int | undefined): this
```

The sibling components in the same container are hierarchically displayed. A larger value of z indicates a higher display level.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-default zIndex(value: int | undefined): this--><!--Device-CommonMethod-default zIndex(value: int | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

