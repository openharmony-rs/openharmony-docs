# CommonMethod

CommonMethod.

**起始版本：** 11

<!--Device-unnamed-declare class CommonMethod<T>--><!--Device-unnamed-declare class CommonMethod<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="accessibilityactionoptions"></a>
## accessibilityActionOptions

```TypeScript
accessibilityActionOptions(option: AccessibilityActionOptions | undefined): T
```

设置组件的无障碍操作的可选参数，用于限制或修改屏幕朗读等辅助应用发起的操作行为。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityActionOptions(option: AccessibilityActionOptions | undefined): T--><!--Device-CommonMethod-accessibilityActionOptions(option: AccessibilityActionOptions | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [AccessibilityActionOptions](../arkts-apis/arkts-arkui-accessibilityactionoptions-i.md) \| undefined | 是 | 无障碍操作的参数，用于限制或者修改无障碍操作下的滑动行为。<br>AccessibilityActionOptions中的scrollStep用于设置无障碍操作下的滑动步数。<br>取值为**undefined**时scrollStep按1处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回调用该接口的组件引用。 |

<a id="accessibilitychecked"></a>
## accessibilityChecked

```TypeScript
accessibilityChecked(isCheck: boolean): T
```

无障碍节点是否选中的状态维护，用于支持多选的情况使用，表示组件是否被选中。此接口只影响屏幕朗读场景下的组件状态播报信息。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本13开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityChecked(isCheck: boolean): T--><!--Device-CommonMethod-accessibilityChecked(isCheck: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isCheck | boolean | 是 | 用于表示组件是否被选中。<br>**true**：当前组件被选中。<br>**false**：当前组件未被选中。<br>**undefined**：由组件自行确定选中状态。<br>默认值：**undefined** |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilitycustomactions"></a>
## accessibilityCustomActions

```TypeScript
accessibilityCustomActions(actions: Array<AccessibilityCustomAction> | undefined): T
```

设置组件的自定义无障碍操作，支持开发者设置一个自定义actions的数组，用于给组件按操作名进行自定义操作的回调绑定。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityCustomActions(actions: Array<AccessibilityCustomAction> | undefined): T--><!--Device-CommonMethod-accessibilityCustomActions(actions: Array<AccessibilityCustomAction> | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actions | Array&lt;AccessibilityCustomAction&gt; \| undefined | 是 | 自定义无障碍操作数组，每个操作包含操作名称和回调，用于给组件按操作名进行自定义操作的回调绑定。<br>**说明**：数组长度最大支持16个，超出部分将不生效。<br>取值为**undefined**时，不设置自定义操作。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回调用方法的组件实例。 |

<a id="accessibilitydefaultfocus"></a>
## accessibilityDefaultFocus

```TypeScript
accessibilityDefaultFocus(focus: boolean): T
```

为页面设置屏幕朗读初始焦点。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityDefaultFocus(focus: boolean): T--><!--Device-CommonMethod-accessibilityDefaultFocus(focus: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| focus | boolean | 是 | 为页面设置屏幕朗读初始焦点。值为true则表示该组件为当前页默认首焦点，值为false或其他值无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilitydescription"></a>
## accessibilityDescription

```TypeScript
accessibilityDescription(value: string): T
```

设置无障碍说明。该属性用于为用户进一步说明当前组件，开发人员可为组件设置相对较详细的解释文本，帮助用户理解将要执行的操作。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityDescription(value: string): T--><!--Device-CommonMethod-accessibilityDescription(value: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 无障碍说明，用于为用户进一步说明当前组件，开发人员可为组件的该属性设置相对较详细的解释文本，帮助用户理解将要执行的操作。如帮助用户理解将要执行的操作可能导致什么后果，尤其是当这些后果无法从组件本身属性与无障碍文本中了解到时。若组件既拥有文本属性又拥有无障碍说明属性，则组件被选中时，先播报组件的文本属性，再播报无障碍说明属性的内容。<br>默认值：**""** |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form |

<a id="accessibilitydescription-1"></a>
## accessibilityDescription

```TypeScript
accessibilityDescription(description: Resource): T
```

设置无障碍说明，支持通过Resource引用资源文件。该属性用于为用户进一步说明当前组件，开发人员可为组件设置相对较详细的解释文本，帮助用户理解将要执行的操作。<p><strong>NOTE</strong>:<br>Reference resource of the accessibility description. You can specify further explanation<br>of the current component, for example, possible operation consequences, especially those that<br>cannot be learned from component attributes and accessibility text. If a component contains<br>both text information and the accessibility description, the text is read first and then the<br>accessibility description, when the component is selected.</p>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityDescription(description: Resource): T--><!--Device-CommonMethod-accessibilityDescription(description: Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| description | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | set description of accessibility |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilityfocusdrawlevel"></a>
## accessibilityFocusDrawLevel

```TypeScript
accessibilityFocusDrawLevel(drawLevel: FocusDrawLevel): T
```

无障碍焦点绿框的绘制层级设置功能。默认层级是跟随组件。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本19开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityFocusDrawLevel(drawLevel: FocusDrawLevel): T--><!--Device-CommonMethod-accessibilityFocusDrawLevel(drawLevel: FocusDrawLevel): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawLevel | [FocusDrawLevel](../arkts-apis/arkts-arkui-focusdrawlevel-e.md) | 是 | 无障碍绘制能力，默认情况下绘制聚焦节点本身。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilitygroup"></a>
## accessibilityGroup

```TypeScript
accessibilityGroup(value: boolean): T
```

Sets whether to enable accessibility grouping.

<p><strong>NOTE</strong><br>Whether to enable accessibility grouping. When accessibility grouping is enabled,<br>the component and all its children are treated as a single selectable unit, and the accessibility<br>service will no longer focus on the individual child components.</p>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityGroup(value: boolean): T--><!--Device-CommonMethod-accessibilityGroup(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | set group with accessibility, default value is false. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilitygroup-1"></a>
## accessibilityGroup

```TypeScript
accessibilityGroup(isGroup: boolean, accessibilityOptions: AccessibilityOptions): T
```

Sets whether to enable accessibility grouping.

<p><strong>NOTE</strong><br>If accessibility grouping is enabled and the component does not contain a universal text attribute<br>or an accessibility text attribute, the system will concatenate the universal text attributes of<br>its child components to form a merged text for the component. If a child component lacks a universal<br>text attribute, it will be ignored in the concatenation process.

<br>When accessibilityPreferred is set to true, the system will prioritize concatenating the accessibility<br>text attributes of the child components to form the merged text. If a child component lacks an<br>accessibility text attribute, the system will continue to concatenate its universal text attribute.<br>If a child component lacks both, it will be ignored.</p>

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本14开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityGroup(isGroup: boolean, accessibilityOptions: AccessibilityOptions): T--><!--Device-CommonMethod-accessibilityGroup(isGroup: boolean, accessibilityOptions: AccessibilityOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isGroup | boolean | 是 | set group with accessibility, default value is false. |
| accessibilityOptions | [AccessibilityOptions](../arkts-apis/arkts-arkui-accessibilityoptions-i.md) | 是 | accessibilityOptions for accessibility, default value is false. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilitylevel"></a>
## accessibilityLevel

```TypeScript
accessibilityLevel(value: string): T
```

Sets the accessibility level.This property determines whether the component can be recognized by accessibility services.<p>Accessibility level, which is used to decide whether a component can be identified by the accessibility service.<br>The options are as follows:<br>"auto": The component's recognizability is determined by the accessibility grouping service and ArkUI.<br>"yes": The component can be recognized by accessibility services.<br>"no": The component cannot be recognized by accessibility services.<br>"no-hide-descendants": Neither the component nor its child components can be recognized by accessibility services.<strong>NOTE</strong><br>When accessibilityLevel is set to "auto", the component's recognizability depends on the following factors:<br>1. The accessibility service internally determines whether the component can be recognized.<br>2. If the parent component's accessibilityGroup property has isGroup set to true, the accessibility service will<br>not focus on its child components, making them unrecognizable.<br>3. If the parent component's accessibilityLevel is set to "no-hide-descendants", the component will not be<br>recognized by accessibility services.</p>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityLevel(value: string): T--><!--Device-CommonMethod-accessibilityLevel(value: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | set accessibility level, default value is auto. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilitynextfocusid"></a>
## accessibilityNextFocusId

```TypeScript
accessibilityNextFocusId(nextId: string): T
```

指定屏幕朗读扫动走焦过程中组件的下一个焦点。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityNextFocusId(nextId: string): T--><!--Device-CommonMethod-accessibilityNextFocusId(nextId: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| nextId | string | 是 | 下一个被指定聚焦组件的[唯一标识id](arkts-arkui-commonmethod-c.md#id-1)。若唯一标识id无对应组件，则设置的accessibilityNextFocusId不存在，设置无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilitynextfocusid-1"></a>
## accessibilityNextFocusId

```TypeScript
accessibilityNextFocusId(nextId: string, nextFocusParams : AccessibilityNextFocusParams | undefined): T
```

指定屏幕朗读扫动走焦过程中组件的下一个焦点，并支持配置详细参数。<br>通过AccessibilityNextFocusParams参数，可以配置是否在无障碍下一个焦点处理过程中查找后代节点中的焦点。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityNextFocusId(nextId: string, nextFocusParams : AccessibilityNextFocusParams | undefined): T--><!--Device-CommonMethod-accessibilityNextFocusId(nextId: string, nextFocusParams : AccessibilityNextFocusParams | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| nextId | string | 是 | 下一个被指定聚焦组件的[唯一标识id](arkts-arkui-commonmethod-c.md#id-1)。若唯一标识id无对应组件，则设置的accessibilityNextFocusId不存在，设置无效。 |
| nextFocusParams | [AccessibilityNextFocusParams](../arkts-apis/arkts-arkui-accessibilitynextfocusparams-i.md) \| undefined | 是 | 无障碍下一个焦点处理的详细参数，用于配置是否在后代节点中查找可聚焦节点。<br>取值为**undefined**时，不配置下一个焦点处理的详细参数，不在后代节点中查找焦点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilityrole"></a>
## accessibilityRole

```TypeScript
accessibilityRole(role: AccessibilityRoleType): T
```

设置无障碍组件类型，特定组件类型有特定的朗读方式，可以根据应用诉求，修改组件类型，用于控制无障碍模式下对组件的朗读方式和朗读内容。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityRole(role: AccessibilityRoleType): T--><!--Device-CommonMethod-accessibilityRole(role: AccessibilityRoleType): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| role | [AccessibilityRoleType](arkts-arkui-accessibilityroletype-e.md) | 是 | 屏幕朗读播报的组件类型，如按钮、图表。具体类型可由开发者自定义。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilityscrolltriggerable"></a>
## accessibilityScrollTriggerable

```TypeScript
accessibilityScrollTriggerable(isTriggerable: boolean): T
```

设置无障碍节点是否支持屏幕朗读滚动操作。当屏幕朗读在扫动走焦时，若容器内当前页面无可聚焦的组件，会发起一次自动滚动操作。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityScrollTriggerable(isTriggerable: boolean): T--><!--Device-CommonMethod-accessibilityScrollTriggerable(isTriggerable: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isTriggerable | boolean | 是 | 用于表示组件是否支持该能力。<br>**true**：屏幕朗读焦点切换而容器内当前页面无可聚焦的组件时，需要自动滚动操作。<br>**false**：屏幕朗读焦点切换而容器内当前页面无可聚焦的组件时，不需要自动滚动操作。<br>**undefined**：还原默认值。<br>默认值：**true** |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilityselected"></a>
## accessibilitySelected

```TypeScript
accessibilitySelected(isSelect: boolean): T
```

无障碍节点是否选中的状态维护，用于支持单选的情况使用，表示组件是否被选中。此接口只影响屏幕朗读场景下的组件状态播报信息。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本13开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilitySelected(isSelect: boolean): T--><!--Device-CommonMethod-accessibilitySelected(isSelect: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSelect | boolean | 是 | 用于表示组件是否被选中。<br>**true**：当前组件被选中。<br>**false**：当前组件未被选中。<br>**undefined**：由组件自行确定选中状态。<br>默认值：**undefined** |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilitystatedescription"></a>
## accessibilityStateDescription

```TypeScript
accessibilityStateDescription(description: string | Resource | undefined): T
```

设置组件的状态播报文本，用于屏幕朗读场景下清晰说明组件当前的实时状态。屏幕朗读时会优先播报该状态文本。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityStateDescription(description: string | Resource | undefined): T--><!--Device-CommonMethod-accessibilityStateDescription(description: string | Resource | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| description | string \| Resource \| undefined | 是 | 需要播报组件当前状态的语音播报文本。<br>设置文本超过1000字符时，截取前1000字符进行播报。<br>**undefined**：播报文本默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回调用该接口的组件引用。 |

<a id="accessibilitytext"></a>
## accessibilityText

```TypeScript
accessibilityText(value: string): T
```

Sets the accessibility text.When a component does not contain a text attribute, you can use this API to set an accessibility text attribute, so that accessibility services can announce the specified content for the component.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityText(value: string): T--><!--Device-CommonMethod-accessibilityText(value: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | set accessibility text, default value is "". |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilitytext-1"></a>
## accessibilityText

```TypeScript
accessibilityText(text: Resource): T
```

Sets the accessibility text.<p><strong>NOTE</strong>If a component has both text content and accessibility text, only the accessibility text is announced.<br>If a component is grouped for accessibility purposes but lacks both text content and accessibility<br>text, the screen reader will concatenate text from its child components (depth-first traversal).<br>To prioritize accessibility text concatenation, set accessibilityPreferred in accessibilityGroup.</p>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityText(text: Resource): T--><!--Device-CommonMethod-accessibilityText(text: Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | set accessibility text |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilitytexthint"></a>
## accessibilityTextHint

```TypeScript
accessibilityTextHint(value: string): T
```

设置组件的文本提示信息，供无障碍辅助应用查询。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityTextHint(value: string): T--><!--Device-CommonMethod-accessibilityTextHint(value: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 组件的文本提示信息，供无障碍辅助应用查询。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilityusesamepage"></a>
## accessibilityUseSamePage

```TypeScript
accessibilityUseSamePage(pageMode: AccessibilitySamePageMode): T
```

设置当前组件和宿主应用为同page模式。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityUseSamePage(pageMode: AccessibilitySamePageMode): T--><!--Device-CommonMethod-accessibilityUseSamePage(pageMode: AccessibilitySamePageMode): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pageMode | [AccessibilitySamePageMode](arkts-arkui-accessibilitysamepagemode-e.md) | 是 | 当前跨进程嵌入式显示的组件和宿主应用的同page模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="accessibilityvirtualnode"></a>
## accessibilityVirtualNode

```TypeScript
accessibilityVirtualNode(builder: CustomBuilder): T
```

设置无障碍虚拟子节点。对自绘制组件传入一个自定义的CustomBuilder，该CustomBuilder中的组件在后端仅做布局不做显示，辅助应用获取无障碍节点信息时会返回CustomBuilder中的节点信息。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-accessibilityVirtualNode(builder: CustomBuilder): T--><!--Device-CommonMethod-accessibilityVirtualNode(builder: CustomBuilder): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | 无障碍虚拟子节点，使开发者可以对自绘制组件传入一个自定义的CustomBuilder，该CustomBuilder中的组件在后端仅做布局不做显示，辅助应用获取无障碍节点信息时会返回CustomBuilder中的节点信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form |

<a id="align"></a>
## align

```TypeScript
align(value: Alignment): T
```

设置当前组件绘制区域内的子组件的对齐方式，支持 [attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-align(value: Alignment): T--><!--Device-CommonMethod-align(value: Alignment): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Alignment](../arkts-apis/arkts-arkui-alignment-e.md) | 是 | 设置当前组件绘制区域内的子组件的对齐方式。<br/>只在[Stack](../../apis-arkts/arkts-apis/arkts-arkts-util-stack-stack-c.md),[FolderStack](FolderStack),[Shape](Shape),[Button](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-mouseevent-button-e.md),[Marquee](Marquee),[StepperItem](StepperItem),[Text](Text),[TextArea](TextArea),[TextInput](TextInput),[RichEditor](RichEditor),[Hyperlink](Hyperlink),[SymbolGlyph](SymbolGlyph),[ListItem](ListItem),[GridItem](GridItem),[Scroll](Scroll),[FlowItem](FlowItem),[ImageAnimator](ImageAnimator),[LoadingProgress](LoadingProgress),[PatternLock](PatternLock),[Progress](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-progress-i.md),[QRCode](QRCode),[TextClock](TextClock),[TextTimer](TextTimer),[MenuItem](StMenuItemack),[Toggle](Toggle),[Checkbox](Checkbox), and [NodeContainer](NodeContainer)中生效，其中和文本相关的组件Marquee、Text、TextArea、TextInput、RichEditor、Hyperlink的align结果参考[textAlign](ts-basic-components-text.md#textalign)。<br/>不支持textAlign属性的组件则无法设置水平方向的文字对齐。<br/>默认值：Alignment.Center<br/>**说明：**<br/>该属性在[Stack](ts-container-stack.md)组件上支持镜像能力，在其他组件上不支持镜像能力。<br/>在Stack中该属性与alignContent效果一致，只能设置子组件在当前组件内的对齐方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="align-1"></a>
## align

```TypeScript
align(alignment: Alignment | LocalizedAlignment): T
```

设置当前组件绘制区域内的子组件的对齐方式，增加支持镜像的能力，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-align(alignment: Alignment | LocalizedAlignment): T--><!--Device-CommonMethod-align(alignment: Alignment | LocalizedAlignment): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignment | [Alignment](../arkts-apis/arkts-arkui-alignment-e.md) \| LocalizedAlignment | 是 | 设置当前组件绘制区域内的子组件的对齐方式，增加支持镜像的能力。<br/>[LocalizedAlignment](../arkts-apis/arkts-arkui-localizedalignment-e.md)只在[Shape](Shape),[Button](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-mouseevent-button-e.md),[GridItem](GridItem),[FlowItem](FlowItem),[ImageAnimator](ImageAnimator),[LoadingProgress](LoadingProgress),[PatternLock](PatternLock),[Progress](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-progress-i.md),[QRCode](QRCode),[TextClock](TextClock),[TextTimer](TextTimer),[StepperItem](StepperItem),[MenuItem](MenuItem),[Toggle](MenuItem),[Checkbox](Checkbox), and [ListItem](ListItem)中有效果。<br/>其中，除ListItem与Alignment的效果保持一致以外，其他组件镜像切换均生效；其他设置LocalizedAlignment无效果的组件按其默认效果显示。<br/>默认值：Al ignment.Center、LocalizedAlignment.CENTER<br/>设置异常值按默认值处理，效果为居中显示。<br/>**说明：**<br/>Alignment类型不支持镜像能力；LocalizedAlignment类型支持镜像能力，选择LocalizedAlignment中的枚举值，根据direction或系统语言方向的改变实现镜像切换。其中dire ction的优先级高于系统语言方向，当设置direction且不为auto时，LocalizedAlignment的镜像按照direction进行布局；当设置direction为auto或未设置时，LocalizedAli gnment的镜像按照系统语言方向进行布局。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="alignrules"></a>
## alignRules

```TypeScript
alignRules(value: AlignRuleOption): T
```

指定设置在相对布局组件中子组件的对齐规则，仅当父组件为[RelativeContainer](RelativeContainer)时生效，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-alignRules(value: AlignRuleOption): T--><!--Device-CommonMethod-alignRules(value: AlignRuleOption): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [AlignRuleOption](arkts-arkui-alignruleoption-i.md) | 是 | 指定设置在相对布局组件中子组件的对齐规则。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="alignrules-1"></a>
## alignRules

```TypeScript
alignRules(alignRule: LocalizedAlignRuleOptions): T
```

指定设置在相对布局组件中子组件的对齐规则，仅当父组件为[RelativeContainer](RelativeContainer)时生效。该方法水平方向上以start和end分别替代原方法的left和right，以便在RTL模式下能镜像显示，建议使用该方法指定设置在相对布局组件中子组件的对齐规则，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-alignRules(alignRule: LocalizedAlignRuleOptions): T--><!--Device-CommonMethod-alignRules(alignRule: LocalizedAlignRuleOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignRule | [LocalizedAlignRuleOptions](arkts-arkui-localizedalignruleoptions-i.md) | 是 | 指定设置在相对布局组件中子组件的对齐规则。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="alignself"></a>
## alignSelf

```TypeScript
alignSelf(value: ItemAlign): T
```

子组件在父容器交叉轴的对齐格式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-alignSelf(value: ItemAlign): T--><!--Device-CommonMethod-alignSelf(value: ItemAlign): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ItemAlign](../arkts-apis/arkts-arkui-itemalign-e.md) | 是 | 子组件在父容器交叉轴的对齐格式，会覆盖([Flex](Flex), [Column](Column), [Row](Row), or [GridRow](GridRow))布局容器中的alignItems设置。<br/>[GridCol](GridCol)可以绑定alignSelf属性来改变它自身在交叉轴方向上的布局。<br/>默认值：ItemAlign.Auto |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="allowdrop"></a>
## allowDrop

```TypeScript
allowDrop(value: Array<UniformDataType> | null | Array<string>): T
```

设置该组件上允许落入的数据类型。如果未设置allowDrop，组件将默认接受所有数据类型。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-allowDrop(value: Array<UniformDataType> | null | Array<string>): T--><!--Device-CommonMethod-allowDrop(value: Array<UniformDataType> | null | Array<string>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;UniformDataType&gt; \| null \| Array&lt;string&gt; | 是 | 设置该组件上允许落入的数据类型。从API version 12开始，允许设置成null使该组件不接受所有的数据类型。从API version 23开始，支持设置自定义数据类型Array<string>，自定义数据类型为应用自行定义的数据类型字符串，字符串无明确格式要求，但不应与UniformDataType标准类型格式重复，建议以易记易区分为原则来定义。<br>**起始版本：** 23 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="allowforcedark"></a>
## allowForceDark

```TypeScript
allowForceDark(value: boolean): T
```

Set whether the component enables the ability to invert colors.This interface needs to be set as the first attribute of the component.

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-allowForceDark(value: boolean): T--><!--Device-CommonMethod-allowForceDark(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | value indicates whether the component enables the ability to invert colors. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@atomicservice |

<a id="animation"></a>
## animation

```TypeScript
animation(value: AnimateParam): T
```

设置组件的属性动画。

> **说明：**  
>  
> - 在单一页面上存在大量应用动效的组件时，可以使用[renderGroup](arkts-arkui-commonmethod-c.md#rendergroup-1)方法来解决卡顿问题，从而提升动画性能。最佳实践请参考  
> [动画使用指导-使用renderGroup](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-fair-use-animation#section1223162922415)。  
>  
>  
> - 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-animation(value: AnimateParam): T--><!--Device-CommonMethod-animation(value: AnimateParam): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [AnimateParam](arkts-arkui-animateparam-i.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="aspectratio"></a>
## aspectRatio

```TypeScript
aspectRatio(value: number): T
```

指定当前组件的宽高比，aspectRatio=width/height。  
- 仅设置width、aspectRatio时，height=width/aspectRatio。  
- 仅设置height、aspectRatio时，width=height*aspectRatio。  
- 同时设置width、height和aspectRatio时，height不生效，height=width/aspectRatio。

设置aspectRatio属性后，组件宽高会受父组件内容区大小限制，[constraintSize](arkts-arkui-commonmethod-c.md#constraintsize-1)的优先级高于aspectRatio。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-aspectRatio(value: number): T--><!--Device-CommonMethod-aspectRatio(value: number): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 指定当前组件的宽高比。<br/>API version 9及以前，默认值为：1.0。<br/>API version10：无默认值。<br/>**说明：**<br/>该属性在不设置值或者设置非法值(小于等于0)时不生效。<br/>例如，Row只设置宽度且没有子组件，aspectRatio不设置值或者设置成负数时，此时Row高度为0。<br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="attributemodifier"></a>
## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<T>): T
```

Sets the attribute modifier.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-attributeModifier(modifier: AttributeModifier<T>): T--><!--Device-CommonMethod-attributeModifier(modifier: AttributeModifier<T>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](arkts-arkui-attributemodifier-i.md)&lt;T&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="backdropblur"></a>
## backdropBlur

```TypeScript
backdropBlur(value: number, options?: BlurOptions): T
```

为组件添加背景模糊效果，支持自定义设置模糊半径和灰阶参数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backdropBlur(value: number, options?: BlurOptions): T--><!--Device-CommonMethod-backdropBlur(value: number, options?: BlurOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 为当前组件添加背景模糊效果，入参为模糊半径，模糊半径越大越模糊，为0时不模糊。<br/>取值范围：[0, +∞)<br/>默认值：0 |
| options | [BlurOptions](arkts-arkui-bluroptions-i.md) | 否 | 灰阶模糊参数。对图像中的黑白色进行色阶调整，使其趋于灰色更为柔和美观，对图像中的彩色调整没有效果。<br/>默认值：grayscale:[0,0]<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="backdropblur-1"></a>
## backdropBlur

```TypeScript
backdropBlur(radius: Optional<number>, options?: BlurOptions): T
```

为组件添加背景模糊效果，支持自定义设置模糊半径和灰阶参数。与[backdropBlur](arkts-arkui-commonmethod-c.md#backdropblur-1)相比，radius参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backdropBlur(radius: Optional<number>, options?: BlurOptions): T--><!--Device-CommonMethod-backdropBlur(radius: Optional<number>, options?: BlurOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 为当前组件添加背景模糊效果，入参为模糊半径，模糊半径越大越模糊，为0时不模糊。当radius的值为undefined时，恢复为默认无模糊的背景。<br/>取值范围：[0, +∞)<br/>默认值：0<br/> |
| options | [BlurOptions](arkts-arkui-bluroptions-i.md) | 否 | 灰阶模糊参数。对图像中的黑白色进行色阶调整，使其趋于灰色更为柔和美观，对图像中的彩色调整没有效果。<br/>默认值：grayscale: [0,0] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="backdropblur-2"></a>
## backdropBlur

```TypeScript
backdropBlur(radius: Optional<number>, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): T
```

为组件添加背景模糊效果，支持自定义设置模糊半径和灰阶参数。与[backdropBlur<sup>18+</sup>](arkts-arkui-commonmethod-c.md#backdropblur-1)相比，新增了sysOptions参数，即支持系统自适应调节参数。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本19开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backdropBlur(radius: Optional<number>, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): T--><!--Device-CommonMethod-backdropBlur(radius: Optional<number>, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 为当前组件添加背景模糊效果，入参为模糊半径，模糊半径越大越模糊，为0时不模糊。<br/>当radius的值为undefined时，恢复为默认无模糊的背景。<br/>取值范围：[0, +∞)<br/>默认值：0 |
| options | [BlurOptions](arkts-arkui-bluroptions-i.md) | 否 | 灰阶模糊参数。对图像中的黑白色进行色阶调整，使其趋于灰色更为柔和美观，对图像中的彩色调整没有效果。<br/>默认值：grayscale: [0,0] |
| sysOptions | [SystemAdaptiveOptions](arkts-arkui-systemadaptiveoptions-i.md) | 否 | 系统自适应调节参数。<br/>默认值：{ disableSystemAdaptation: false } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="background"></a>
## background

```TypeScript
background(content: CustomBuilder | ResourceColor, options?: BackgroundOptions): T
```

Add a background for the component.

Anonymous Object Rectification.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-background(content: CustomBuilder | ResourceColor, options?: BackgroundOptions): T--><!--Device-CommonMethod-background(content: CustomBuilder | ResourceColor, options?: BackgroundOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [CustomBuilder](arkts-arkui-custombuilder-t.md) \| ResourceColor | 是 |  |
| options | [BackgroundOptions](arkts-arkui-backgroundoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="backgroundblurstyle"></a>
## backgroundBlurStyle

```TypeScript
backgroundBlurStyle(value: BlurStyle, options?: BackgroundBlurStyleOptions): T
```

为当前组件提供一种背景材质模糊能力，通过枚举值的方式封装了不同的模糊半径、蒙版颜色、蒙版透明度、饱和度、亮度。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backgroundBlurStyle(value: BlurStyle, options?: BackgroundBlurStyleOptions): T--><!--Device-CommonMethod-backgroundBlurStyle(value: BlurStyle, options?: BackgroundBlurStyleOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BlurStyle](arkts-arkui-blurstyle-e.md) | 是 | 背景模糊样式。模糊样式中封装了模糊半径、蒙版颜色、蒙版透明度、饱和度、亮度五个参数。 |
| options | [BackgroundBlurStyleOptions](arkts-arkui-backgroundblurstyleoptions-i.md) | 否 | 背景模糊选项。用于配置模糊激活策略和不生效时的背景色。不传入时使用默认激活策略[BlurStyleActivePolicy](arkts-arkui-blurstyleactivepolicy-e.md).ALWAYS_ACTIVE。<br/>该参数在ArkTS卡片中，暂不支持使用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="backgroundblurstyle-1"></a>
## backgroundBlurStyle

```TypeScript
backgroundBlurStyle(style: Optional<BlurStyle>, options?: BackgroundBlurStyleOptions): T
```

为当前组件提供一种背景材质模糊能力，通过枚举值的方式封装了不同的模糊半径、蒙版颜色、蒙版透明度、饱和度、亮度。与[backgroundBlurStyle<sup>9+</sup>](arkts-arkui-commonmethod-c.md#backgroundblurstyle-1)相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backgroundBlurStyle(style: Optional<BlurStyle>, options?: BackgroundBlurStyleOptions): T--><!--Device-CommonMethod-backgroundBlurStyle(style: Optional<BlurStyle>, options?: BackgroundBlurStyleOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;BlurStyle&gt; | 是 | 背景模糊样式。模糊样式中封装了模糊半径、蒙版颜色、蒙版透明度、饱和度、亮度五个参数。<br/>当style的值为undefined时，恢复为默认关闭模糊的背景。 |
| options | [BackgroundBlurStyleOptions](arkts-arkui-backgroundblurstyleoptions-i.md) | 否 | 背景模糊选项。用于配置模糊激活策略和不生效时的背景色。不传入时使用默认激活策略[BlurStyleActivePolicy](arkts-arkui-blurstyleactivepolicy-e.md).ALWAYS_ACTIVE。<br/>该参数在ArkTS卡片中，暂不支持使用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="backgroundblurstyle-2"></a>
## backgroundBlurStyle

```TypeScript
backgroundBlurStyle(style: Optional<BlurStyle>, options?: BackgroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): T
```

为当前组件提供一种背景材质模糊能力，通过枚举值的方式封装了不同的模糊半径、蒙版颜色、蒙版透明度、饱和度、亮度。与[backgroundBlurStyle<sup>18+</sup>](arkts-arkui-commonmethod-c.md#backgroundblurstyle-1)相比，新增了sysOptions参数，即支持系统自适应调节参数。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本19开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backgroundBlurStyle(style: Optional<BlurStyle>, options?: BackgroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): T--><!--Device-CommonMethod-backgroundBlurStyle(style: Optional<BlurStyle>, options?: BackgroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;BlurStyle&gt; | 是 | 背景模糊样式。模糊样式中封装了模糊半径、蒙版颜色、蒙版透明度、饱和度、亮度五个参数。<br/>当style的值为undefined时，恢复为默认关闭模糊的背景。 |
| options | [BackgroundBlurStyleOptions](arkts-arkui-backgroundblurstyleoptions-i.md) | 否 | 背景模糊选项。<br/>该参数在ArkTS卡片中，暂不支持使用。 |
| sysOptions | [SystemAdaptiveOptions](arkts-arkui-systemadaptiveoptions-i.md) | 否 | 系统自适应调节参数。<br/>默认值：{ disableSystemAdaptation: false } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="backgroundbrightness"></a>
## backgroundBrightness

```TypeScript
backgroundBrightness(params: BackgroundBrightnessOptions): T
```

设置组件背景提亮效果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-backgroundBrightness(params: BackgroundBrightnessOptions): T--><!--Device-CommonMethod-backgroundBrightness(params: BackgroundBrightnessOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [BackgroundBrightnessOptions](arkts-arkui-backgroundbrightnessoptions-i.md) | 是 | 设置组件背景提亮效果，包括：亮度变化速率，提亮程度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="backgroundbrightness-1"></a>
## backgroundBrightness

```TypeScript
backgroundBrightness(options: Optional<BackgroundBrightnessOptions>): T
```

设置组件背景提亮效果。与[backgroundBrightness<sup>12+</sup>](arkts-arkui-commonmethod-c.md#backgroundbrightness-1)相比，options参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-backgroundBrightness(options: Optional<BackgroundBrightnessOptions>): T--><!--Device-CommonMethod-backgroundBrightness(options: Optional<BackgroundBrightnessOptions>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;BackgroundBrightnessOptions&gt; | 是 | 设置组件背景提亮效果，包括：亮度变化速率，提亮程度。<br/>当options的值为undefined时，恢复为无提亮效果的背景。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="backgroundcolor"></a>
## backgroundColor

```TypeScript
backgroundColor(value: ResourceColor): T
```

Background color

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backgroundColor(value: ResourceColor): T--><!--Device-CommonMethod-backgroundColor(value: ResourceColor): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform@form@atomicservice |

<a id="backgroundcolor-1"></a>
## backgroundColor

```TypeScript
backgroundColor(color: Optional<ResourceColor>): T
```

Background color

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backgroundColor(color: Optional<ResourceColor>): T--><!--Device-CommonMethod-backgroundColor(color: Optional<ResourceColor>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="backgroundcolor-2"></a>
## backgroundColor

```TypeScript
backgroundColor(color: Optional<ResourceColor | ColorMetrics>): T
```

Background color

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backgroundColor(color: Optional<ResourceColor | ColorMetrics>): T--><!--Device-CommonMethod-backgroundColor(color: Optional<ResourceColor | ColorMetrics>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor \| ColorMetrics&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="backgroundeffect"></a>
## backgroundEffect

```TypeScript
backgroundEffect(options: BackgroundEffectOptions): T
```

设置组件背景属性，包括背景模糊半径、亮度、饱和度和颜色等参数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-backgroundEffect(options: BackgroundEffectOptions): T--><!--Device-CommonMethod-backgroundEffect(options: BackgroundEffectOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [BackgroundEffectOptions](arkts-arkui-backgroundeffectoptions-i.md) | 是 | 设置组件背景属性包括：背景模糊半径、亮度、饱和度和颜色等参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="backgroundeffect-1"></a>
## backgroundEffect

```TypeScript
backgroundEffect(options: Optional<BackgroundEffectOptions>): T
```

设置组件背景属性，包括背景模糊半径、亮度、饱和度和颜色等参数。与[backgroundEffect<sup>11+</sup>](arkts-arkui-commonmethod-c.md#backgroundeffect-1)相比，options参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-backgroundEffect(options: Optional<BackgroundEffectOptions>): T--><!--Device-CommonMethod-backgroundEffect(options: Optional<BackgroundEffectOptions>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;BackgroundEffectOptions&gt; | 是 | 设置组件背景属性包括：背景模糊半径、亮度、饱和度和颜色等参数。<br/>当options的值为undefined时，恢复为无效果的背景。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="backgroundeffect-2"></a>
## backgroundEffect

```TypeScript
backgroundEffect(options: Optional<BackgroundEffectOptions>, sysOptions?: SystemAdaptiveOptions): T
```

设置组件背景属性，包括背景模糊半径、亮度、饱和度和颜色等参数。与[backgroundEffect<sup>18+</sup>](arkts-arkui-commonmethod-c.md#backgroundeffect-1)相比，新增了sysOptions参数，即支持系统自适应调节参数。

> **说明：**  
>  
> backgroundEffect接口为实时接口，每帧对模糊等效果执行实时渲染，性能负载较大。当组件背景模糊效果无需变动时，推荐采用静态模糊接口  
> [blur](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-effectkit-filter-i.md#blur-1)实现模糊效果。最佳实践请参考：  
> [图像模糊动效优化-使用场景](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-fuzzy-scene-performance-optimization#section4945532519)。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-backgroundEffect(options: Optional<BackgroundEffectOptions>, sysOptions?: SystemAdaptiveOptions): T--><!--Device-CommonMethod-backgroundEffect(options: Optional<BackgroundEffectOptions>, sysOptions?: SystemAdaptiveOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;BackgroundEffectOptions&gt; | 是 | 设置组件背景属性包括：背景模糊半径、亮度、饱和度和颜色等参数。<br/>当options的值为undefined时，恢复为无效果的背景。 |
| sysOptions | [SystemAdaptiveOptions](arkts-arkui-systemadaptiveoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="backgroundfilter"></a>
## backgroundFilter

```TypeScript
backgroundFilter(filter: Filter): T
```

设置背景滤镜视觉效果。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-backgroundFilter(filter: Filter): T--><!--Device-CommonMethod-backgroundFilter(filter: Filter): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) | 是 | 背景滤镜视觉效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="backgroundimage"></a>
## backgroundImage

```TypeScript
backgroundImage(src: ResourceStr | PixelMap, repeat?: ImageRepeat): T
```

Background image src: Image address url

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backgroundImage(src: ResourceStr | PixelMap, repeat?: ImageRepeat): T--><!--Device-CommonMethod-backgroundImage(src: ResourceStr | PixelMap, repeat?: ImageRepeat): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| PixelMap | 是 |  |
| repeat | [ImageRepeat](../arkts-apis/arkts-arkui-imagerepeat-e.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform@form@atomicservice |

<a id="backgroundimage-1"></a>
## backgroundImage

```TypeScript
backgroundImage(src: ResourceStr | PixelMap, options?: BackgroundImageOptions): T
```

Background image

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backgroundImage(src: ResourceStr | PixelMap, options?: BackgroundImageOptions): T--><!--Device-CommonMethod-backgroundImage(src: ResourceStr | PixelMap, options?: BackgroundImageOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| PixelMap | 是 | the background image source |
| options | [BackgroundImageOptions](arkts-arkui-backgroundimageoptions-i.md) | 否 | config the options |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="backgroundimageposition"></a>
## backgroundImagePosition

```TypeScript
backgroundImagePosition(value: Position | Alignment): T
```

Background image position x:Horizontal coordinate;y:Vertical axis coordinate.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backgroundImagePosition(value: Position | Alignment): T--><!--Device-CommonMethod-backgroundImagePosition(value: Position | Alignment): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Position](../arkts-apis/arkts-arkui-display-position-i.md) \| Alignment | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform@form@atomicservice |

<a id="backgroundimageresizable"></a>
## backgroundImageResizable

```TypeScript
backgroundImageResizable(value: ResizableOptions): T
```

Background image resizable.value:resizable options

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-backgroundImageResizable(value: ResizableOptions): T--><!--Device-CommonMethod-backgroundImageResizable(value: ResizableOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResizableOptions](arkts-arkui-resizableoptions-i.md) | 是 | Indicates the resizable options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="backgroundimagesize"></a>
## backgroundImageSize

```TypeScript
backgroundImageSize(value: SizeOptions | ImageSize): T
```

Background image size

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-backgroundImageSize(value: SizeOptions | ImageSize): T--><!--Device-CommonMethod-backgroundImageSize(value: SizeOptions | ImageSize): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) \| ImageSize | 是 | @returns { T } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform@form@atomicservice |

<a id="bindcontentcover"></a>
## bindContentCover

```TypeScript
bindContentCover(isShow: boolean, builder: CustomBuilder, type?: ModalTransition): T
```

给组件绑定全屏模态页面，点击后显示模态页面。模态页面内容自定义，显示方式可设置无动画过渡，上下切换过渡以及透明渐变过渡。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindContentCover(isShow: boolean, builder: CustomBuilder, type?: ModalTransition): T--><!--Device-CommonMethod-bindContentCover(isShow: boolean, builder: CustomBuilder, type?: ModalTransition): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isShow | boolean | 是 | 是否显示全屏模态页面。<br/>-true：显示全屏模态页面。<br/>-false：隐藏全屏模态页面。<br/>从API version 10开始，该参数支持[$$](docroot://ui/state-management/arkts-two-way-sync.md)双向绑定变量。<br />从API version 18开始，该参数支持[!!](docroot://ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。 |
| builder | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | 配置全屏模态页面内容。builder里面的根节点需要唯一。 |
| type | [ModalTransition](arkts-arkui-modaltransition-e.md) | 否 | 全屏模态页面的系统转场方式。<br/> 默认值：ModalTransition.DEFAULT。<br/>**说明：**<br /> 与transition同时设置时，此属性不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="bindcontentcover-1"></a>
## bindContentCover

```TypeScript
bindContentCover(isShow: boolean, builder: CustomBuilder, options?: ContentCoverOptions): T
```

给组件绑定全屏模态页面，点击后显示模态页面。模态页面内容自定义，可自定义设置转场方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindContentCover(isShow: boolean, builder: CustomBuilder, options?: ContentCoverOptions): T--><!--Device-CommonMethod-bindContentCover(isShow: boolean, builder: CustomBuilder, options?: ContentCoverOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isShow | boolean | 是 | 是否显示全屏模态页面。<br/>-true：显示全屏模态页面。<br/>-false：隐藏全屏模态页面。<br/>从API version 10开始，该参数支持[$$](docroot://ui/state-management/arkts-two-way-sync.md)双向绑定变量。<br />从API version 18开始，该参数支持[!!](docroot://ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。 |
| builder | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | 配置全屏模态页面内容。 |
| options | [ContentCoverOptions](arkts-arkui-contentcoveroptions-i.md) | 否 | 配置全屏模态页面的可选属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="bindcontextmenu"></a>
## bindContextMenu

```TypeScript
bindContextMenu(content: CustomBuilder, responseType: ResponseType, options?: ContextMenuOptions): T
```

Binds a context menu to this component, which is displayed when the user long-presses or right-clicks the component. Only custom menu items are supported.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindContextMenu(content: CustomBuilder, responseType: ResponseType, options?: ContextMenuOptions): T--><!--Device-CommonMethod-bindContextMenu(content: CustomBuilder, responseType: ResponseType, options?: ContextMenuOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | Indicates the content of context menu. |
| responseType | [ResponseType](../arkts-apis/arkts-arkui-responsetype-e.md) | 是 | Indicates response type of context menu, Long pressing with a mouse device is not supported. |
| options | [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) | 否 | Indicates the options of context menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform@atomicservice |

<a id="bindcontextmenu-1"></a>
## bindContextMenu

```TypeScript
bindContextMenu(isShown: boolean, content: CustomBuilder, options?: ContextMenuOptions): T
```

ContextMenu control

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindContextMenu(isShown: boolean, content: CustomBuilder, options?: ContextMenuOptions): T--><!--Device-CommonMethod-bindContextMenu(isShown: boolean, content: CustomBuilder, options?: ContextMenuOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isShown | boolean | 是 | true means display content, false means hide content. |
| content | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | Indicates the content of context menu. |
| options | [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) | 否 | Indicates the options of context menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="bindcontextmenubyisshow"></a>
## bindContextMenuByIsShow

```TypeScript
bindContextMenuByIsShow(isShow: boolean, content: CustomBuilder | Array<MenuElement>, options?: ContextMenuOptions): T
```

将上下文菜单绑定到组件，组件的可见性受isShow设置的约束。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindContextMenuByIsShow(isShow: boolean, content: CustomBuilder | Array<MenuElement>, options?: ContextMenuOptions): T--><!--Device-CommonMethod-bindContextMenuByIsShow(isShow: boolean, content: CustomBuilder | Array<MenuElement>, options?: ContextMenuOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isShow | boolean | 是 | true表示显示内容，false表示隐藏内容，默认为false。<p><strong>注意</strong>：<br>只有在构建了相关页面后，菜单才能正常显示。如果设置了该参数在构建完成之前设置为true，显示问题，如错位、扭曲或无法弹出上，可能会发生。不支持长按拖动。</p>. |
| content | [CustomBuilder](arkts-arkui-custombuilder-t.md) \| Array&lt;MenuElement&gt; | 是 | 上下文菜单的内容。 |
| options | [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) | 否 | 上下文菜单选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="bindcontextmenubyresponsetype"></a>
## bindContextMenuByResponseType

```TypeScript
bindContextMenuByResponseType(content: CustomBuilder | Array<MenuElement>, responseType: ResponseType,
      options?: ContextMenuOptions): T
```

将上下文菜单绑定到此组件，当用户长按或右键单击组件，支持自定义或固定样式的菜单项。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindContextMenuByResponseType(content: CustomBuilder | Array<MenuElement>, responseType: ResponseType,
      options?: ContextMenuOptions): T--><!--Device-CommonMethod-bindContextMenuByResponseType(content: CustomBuilder | Array<MenuElement>, responseType: ResponseType,
      options?: ContextMenuOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [CustomBuilder](arkts-arkui-custombuilder-t.md) \| Array&lt;MenuElement&gt; | 是 | 上下文菜单的内容。 |
| responseType | [ResponseType](../arkts-apis/arkts-arkui-responsetype-e.md) | 是 | 上下文菜单响应类型。用鼠标设备长按不支持。 |
| options | [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) | 否 | 上下文菜单选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="bindcontextmenuwithresponse"></a>
## bindContextMenuWithResponse

```TypeScript
bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | undefined, options?: ContextMenuOptions): T
```

将上下文菜单绑定到组件上，当用户长按或右键该组件时显示。仅支持自定义菜单项。鼠标设备不支持长按操作。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | undefined, options?: ContextMenuOptions): T--><!--Device-CommonMethod-bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | undefined, options?: ContextMenuOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [CustomBuilderT](arkts-arkui-custombuildert-t.md)&lt;ResponseType&gt; \| undefined | 是 | 表示上下文菜单的内容。传入undefined表示解绑。 |
| options | [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) | 否 | 表示上下文菜单的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="bindcontextmenuwithresponse-1"></a>
## bindContextMenuWithResponse

```TypeScript
bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | Array<MenuElement> | undefined,
    options?: ContextMenuOptions): T
```

将上下文菜单绑定到此组件，当用户长按或右键单击组件，支持自定义或固定样式的菜单项。不支持使用鼠标设备长按。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | Array<MenuElement> | undefined,
    options?: ContextMenuOptions): T--><!--Device-CommonMethod-bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | Array<MenuElement> | undefined,
    options?: ContextMenuOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [CustomBuilderT](arkts-arkui-custombuildert-t.md)&lt;ResponseType&gt; \| Array&lt;MenuElement&gt; \| undefined | 是 | 上下文菜单的内容。Undefined表示解除绑定。 |
| options | [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) | 否 | 上下文菜单选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="bindmenu"></a>
## bindMenu

```TypeScript
bindMenu(content: Array<MenuElement> | CustomBuilder, options?: MenuOptions): T
```

Menu control

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindMenu(content: Array<MenuElement> | CustomBuilder, options?: MenuOptions): T--><!--Device-CommonMethod-bindMenu(content: Array<MenuElement> | CustomBuilder, options?: MenuOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | Array&lt;MenuElement&gt; \| CustomBuilder | 是 | Indicates the content of menu.<br>**起始版本：** 11 |
| options | [MenuOptions](arkts-arkui-menuoptions-i.md) | 否 | Indicates the options of menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform@atomicservice |

<a id="bindmenu-1"></a>
## bindMenu

```TypeScript
bindMenu(isShow: boolean, content: Array<MenuElement> | CustomBuilder, options?: MenuOptions): T
```

Menu control

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindMenu(isShow: boolean, content: Array<MenuElement> | CustomBuilder, options?: MenuOptions): T--><!--Device-CommonMethod-bindMenu(isShow: boolean, content: Array<MenuElement> | CustomBuilder, options?: MenuOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isShow | boolean | 是 | true means display menu, false means hide menu. |
| content | Array&lt;MenuElement&gt; \| CustomBuilder | 是 | Indicates the content of menu. |
| options | [MenuOptions](arkts-arkui-menuoptions-i.md) | 否 | Indicates the options of menu. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="bindpopup"></a>
## bindPopup

```TypeScript
bindPopup(show: boolean, popup: PopupOptions | CustomPopupOptions): T
```

Popup control<p><strong>NOTE</strong>:<br>The popup can be displayed only after the entire page is fully constructed. Therefore, to avoid incorrect display positions and shapes, do not set this parameter to true while the page is still being constructed.</p>

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindPopup(show: boolean, popup: PopupOptions | CustomPopupOptions): T--><!--Device-CommonMethod-bindPopup(show: boolean, popup: PopupOptions | CustomPopupOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| show | boolean | 是 | @param { PopupOptions \| CustomPopupOptions } popup |
| popup | [PopupOptions](arkts-arkui-popupoptions-i.md) \| CustomPopupOptions | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform@atomicservice |

<a id="bindsheet"></a>
## bindSheet

```TypeScript
bindSheet(isShow: boolean, builder: CustomBuilder, options?: SheetOptions): T
```

给组件绑定半模态页面，点击后显示模态页面。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindSheet(isShow: boolean, builder: CustomBuilder, options?: SheetOptions): T--><!--Device-CommonMethod-bindSheet(isShow: boolean, builder: CustomBuilder, options?: SheetOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isShow | boolean | 是 | 是否显示半模态页面。<br/>true：显示半模态页面。<br/>false：隐藏半模态页面。<br/>从API version 10开始，该参数支持[$$](docroot://ui/state-management/arkts-two-way-sync.md)双向绑定变量。<br />从API version 18开始，该参数支持[!!](docroot://ui/state-management/arkts-new-binding.md)双向绑定变量。 |
| builder | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | 配置半模态页面内容。 |
| options | [SheetOptions](arkts-arkui-sheetoptions-i.md) | 否 | 配置半模态页面的可选属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="bindtips"></a>
## bindTips

```TypeScript
bindTips(message: TipsMessageType, options?: TipsOptions): T
```

Tips control

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-bindTips(message: TipsMessageType, options?: TipsOptions): T--><!--Device-CommonMethod-bindTips(message: TipsMessageType, options?: TipsOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | [TipsMessageType](arkts-arkui-tipsmessagetype-t.md) | 是 |  |
| options | [TipsOptions](arkts-arkui-tipsoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="blendmode"></a>
## blendMode

```TypeScript
blendMode(value: BlendMode, type?: BlendApplyType): T
```

将当前控件的内容（包含子节点内容）与下方画布（可能为离屏画布）已有内容进行混合。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-blendMode(value: BlendMode, type?: BlendApplyType): T--><!--Device-CommonMethod-blendMode(value: BlendMode, type?: BlendApplyType): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BlendMode](arkts-arkui-blendmode-e.md) | 是 | 混合模式。<br/>默认值：BlendMode.NONE<br/>**说明：**<br/>混合模式设置为BlendMode.NONE时，blend效果实际为默认的BlendMode.SRC_OVER，且BlendApplyType不生效。 |
| type | [BlendApplyType](arkts-arkui-blendapplytype-e.md) | 否 | blendMode实现方式是否离屏。<br/>默认值：BlendApplyType.FAST<br/>**说明：**<br/>1. 设置BlendApplyType.FAST时，不离屏。<br/>2. 设置BlendApplyType.OFFSCREEN时，会创建当前组件大小的离屏画布，再将当前组件（含子组件）的内容绘制到离屏画布上，再用指定的混合模式与下方画布已有内容进行混合。使用该实现方式时，将导致[linearGradientBlur<sup>12+</sup>](arkts-arkui-commonmethod-c.md#lineargradientblur-1)、[backgroundEffect](arkts-arkui-commonmethod-c.md#backgroundeffect-1)、[brightness](arkts-arkui-commonmethod-c.md#brightness-1)、[blur](arkts-arkui-commonmethod-c.md#blur-1)等需要截屏的接口无法截取到正确的画面。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="blendmode-1"></a>
## blendMode

```TypeScript
blendMode(mode: Optional<BlendMode>, type?: BlendApplyType): T
```

将当前控件的内容（包含子节点内容）与下方画布（可能为离屏画布）已有内容进行混合。与[blendMode<sup>11+</sup>](arkts-arkui-commonmethod-c.md#blendmode-1)相比，mode参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-blendMode(mode: Optional<BlendMode>, type?: BlendApplyType): T--><!--Device-CommonMethod-blendMode(mode: Optional<BlendMode>, type?: BlendApplyType): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)&lt;BlendMode&gt; | 是 | 混合模式。<br/>默认值：BlendMode.NONE<br/>当mode的值为undefined时，恢复为内容不进行混合的效果。<br/>**说明：**<br/>混合模式设置为BlendMode.NONE时，blend效果实际为默认的BlendMode.SRC_OVER，且BlendApplyType不生效。 |
| type | [BlendApplyType](arkts-arkui-blendapplytype-e.md) | 否 | blendMode实现方式是否离屏。<br/>默认值：BlendApplyType.FAST<br/>**说明：**<br/>1. 设置BlendApplyType.FAST时，不离屏。<br/>2. 设置BlendApplyType.OFFSCREEN时，会创建当前组件大小的离屏画布，再将当前组件（含子组件）的内容绘制到离屏画布上，再用指定的混合模式与下方画布已有内容进行混合。使用该实现方式时，将导致[linearGradientBlur<sup>12+</sup>](arkts-arkui-commonmethod-c.md#lineargradientblur-1)、[backgroundEffect](arkts-arkui-commonmethod-c.md#backgroundeffect-1)、[brightness](arkts-arkui-commonmethod-c.md#brightness-1)、[blur](arkts-arkui-commonmethod-c.md#blur-1)等需要截屏的接口无法截取到正确的画面。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="blur"></a>
## blur

```TypeScript
blur(value: number, options?: BlurOptions): T
```

为组件添加内容模糊效果。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-blur(value: number, options?: BlurOptions): T--><!--Device-CommonMethod-blur(value: number, options?: BlurOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 当前组件添加内容模糊效果，入参为模糊半径，模糊半径越大越模糊，为0时不模糊。 |
| options | [BlurOptions](arkts-arkui-bluroptions-i.md) | 否 | 灰阶模糊参数。对图像中的黑白色进行色阶调整，使其趋于灰色更为柔和美观，对图像中的彩色调整没有效果。<br/>默认值：grayscale:[0,0]<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="blur-1"></a>
## blur

```TypeScript
blur(blurRadius: Optional<number>, options?: BlurOptions): T
```

为组件添加内容模糊效果。与[blur](arkts-arkui-commonmethod-c.md#blur-1)相比，blurRadius参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-blur(blurRadius: Optional<number>, options?: BlurOptions): T--><!--Device-CommonMethod-blur(blurRadius: Optional<number>, options?: BlurOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurRadius | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 当前组件添加内容模糊效果，入参为模糊半径，模糊半径越大越模糊，为0时不模糊。<br/>当blurRadius的值为undefined时，维持之前取值。 |
| options | [BlurOptions](arkts-arkui-bluroptions-i.md) | 否 | 灰阶模糊参数。对图像中的黑白色进行色阶调整，使其趋于灰色更为柔和美观，对图像中的彩色调整没有效果。<br/>默认值：grayscale: [0,0] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="blur-2"></a>
## blur

```TypeScript
blur(blurRadius: Optional<number>, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): T
```

为组件添加内容模糊效果。与[blur<sup>18+</sup>](arkts-arkui-commonmethod-c.md#blur-1)相比，新增了sysOptions参数，即支持系统自适应调节参数。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本19开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-blur(blurRadius: Optional<number>, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): T--><!--Device-CommonMethod-blur(blurRadius: Optional<number>, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurRadius | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 当前组件添加内容模糊效果，入参为模糊半径，模糊半径越大越模糊，为0时不模糊。<br/>当blurRadius的值为undefined时，维持之前取值。 |
| options | [BlurOptions](arkts-arkui-bluroptions-i.md) | 否 | 灰阶模糊参数。对图像中的黑白色进行色阶调整，使其趋于灰色更为柔和美观，对图像中的彩色调整没有效果。<br/>默认值：grayscale: [0,0] |
| sysOptions | [SystemAdaptiveOptions](arkts-arkui-systemadaptiveoptions-i.md) | 否 | 系统自适应调节参数。<br/>默认值：{ disableSystemAdaptation: false } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="border"></a>
## border

```TypeScript
border(value: BorderOptions): T
```

设置边框样式。

> **说明：**  
>  
> color、radius缺省时，为了保证[borderColor](arkts-arkui-commonmethod-c.md#bordercolor-1)、[borderRadius](arkts-arkui-commonmethod-c.md#borderradius-1)生效，需要将[borderColor](arkts-arkui-commonmethod-c.md#bordercolor-1)、[borderRadius](arkts-arkui-commonmethod-c.md#borderradius-1)设置在[border](arkts-arkui-commonmethod-c.md#border-1)后。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-border(value: BorderOptions): T--><!--Device-CommonMethod-border(value: BorderOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BorderOptions](../arkts-apis/arkts-arkui-borderoptions-i.md) | 是 | <br>统一边框样式设置接口。<br/>**说明：** <br/>边框宽度默认值为0，即不显示边框。<br/>从API version9开始，父节点的border显示在子节点内容之上。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="bordercolor"></a>
## borderColor

```TypeScript
borderColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors): T
```

设置边框的颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-borderColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors): T--><!--Device-CommonMethod-borderColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| EdgeColors \| LocalizedEdgeColors | 是 | Border color.<br>Default value: **Color.Black** |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="borderimage"></a>
## borderImage

```TypeScript
borderImage(value: BorderImageOption): T
```

Sets the border image of the component.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-borderImage(value: BorderImageOption): T--><!--Device-CommonMethod-borderImage(value: BorderImageOption): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BorderImageOption](arkts-arkui-borderimageoption-i.md) | 是 | @returns { T } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform@form@atomicservice |

<a id="borderradius"></a>
## borderRadius

```TypeScript
borderRadius(value: Length | BorderRadiuses | LocalizedBorderRadiuses): T
```

设置边框的圆角半径。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-borderRadius(value: Length | BorderRadiuses | LocalizedBorderRadiuses): T--><!--Device-CommonMethod-borderRadius(value: Length | BorderRadiuses | LocalizedBorderRadiuses): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) \| BorderRadiuses \| LocalizedBorderRadiuses | 是 | Radius of the border corners. The value can be expressed as a percentage of the component's width. When combined with the [clip](arkts-arkui-commonmethod-c.md#clip-1)attribute, this setting clips child components to prevent them from extending beyond the component's boundaries.<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="borderradius-1"></a>
## borderRadius

```TypeScript
borderRadius(value: Length | BorderRadiuses | LocalizedBorderRadiuses, type?: RenderStrategy): T
```

设置边框的圆角半径和绘制圆角的模式。

**注意**1. **RenderStrategy.FAST**：当前组件及其子组件将直接以圆角效果绘制到画布上。2. **RenderStrategy.OFFSCREEN**：当前组件及其子组件将首先渲染到一个离屏画布，然后进行圆角裁剪，最后绘制到主画布上。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-borderRadius(value: Length | BorderRadiuses | LocalizedBorderRadiuses, type?: RenderStrategy): T--><!--Device-CommonMethod-borderRadius(value: Length | BorderRadiuses | LocalizedBorderRadiuses, type?: RenderStrategy): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) \| BorderRadiuses \| LocalizedBorderRadiuses | 是 | 设置元素的边框圆角半径，支持百分比，百分比依据组件宽度。设置圆角后，可搭配clip属性进行裁剪，避免子组件超出组件自身。 |
| type | [RenderStrategy](../arkts-apis/arkts-arkui-renderstrategy-e.md) | 否 | 设置组件绘制圆角的模式。<br>默认值： **RenderStrategy.FAST**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="borderstyle"></a>
## borderStyle

```TypeScript
borderStyle(value: BorderStyle | EdgeStyles): T
```

设置元素的边框线条样式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-borderStyle(value: BorderStyle | EdgeStyles): T--><!--Device-CommonMethod-borderStyle(value: BorderStyle | EdgeStyles): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BorderStyle](../arkts-apis/arkts-arkui-borderstyle-e.md) \| EdgeStyles | 是 | 设置元素的边框样式。<br/>默认值：BorderStyle.Solid   - Border style.<br>Default value: **BorderStyle.Solid**.<br>**起始版本：** 9 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="borderwidth"></a>
## borderWidth

```TypeScript
borderWidth(value: Length | EdgeWidths | LocalizedEdgeWidths): T
```

设置边框的宽度。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-borderWidth(value: Length | EdgeWidths | LocalizedEdgeWidths): T--><!--Device-CommonMethod-borderWidth(value: Length | EdgeWidths | LocalizedEdgeWidths): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) \| EdgeWidths \| LocalizedEdgeWidths | 是 | Border width. This parameter cannot be set in percentage.<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="brightness"></a>
## brightness

```TypeScript
brightness(value: number): T
```

为组件添加高光效果。不通过该接口设置时，默认无变化。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-brightness(value: number): T--><!--Device-CommonMethod-brightness(value: number): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 为当前组件添加高光效果，入参为高光比例，值为1时没有效果，小于1时亮度变暗，小于或等于0为全黑，大于1时亮度增加，数值越大亮度越大，亮度大于或等于2时会变为全白。<br/>取值范围：[0, +∞)<br/>推荐取值范围：[0, 2]<br/>**说明：**<br/>设置小于0的值时，按值为0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="brightness-1"></a>
## brightness

```TypeScript
brightness(brightness: Optional<number>): T
```

为组件添加高光效果。不通过该接口设置时，默认无变化。与[brightness](arkts-arkui-commonmethod-c.md#brightness-1)相比，brightness参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-brightness(brightness: Optional<number>): T--><!--Device-CommonMethod-brightness(brightness: Optional<number>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brightness | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 为当前组件添加高光效果，入参为高光比例，值为1时没有效果，小于1时亮度变暗，小于或等于0为全黑，大于1时亮度增加，数值越大亮度越大，亮度大于或等于2时会变为全白。<br/>取值范围：[0, +∞)<br/>推荐取值范围：[0, 2]<br/>**说明：**<br/>设置小于0的值时，按值为0处理。<br/>当brightness的值为undefined时，恢复为亮度为1的高光效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="chainmode"></a>
## chainMode

```TypeScript
chainMode(direction: Axis, style: ChainStyle): T
```

指定以该组件为链头所构成的链的参数，仅当父组件为RelativeContainer时生效。链头指满足成链规则时链的第一个组件（水平方向从左边起始，镜像语言下从右边起始；竖直方向从上边起始）。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-chainMode(direction: Axis, style: ChainStyle): T--><!--Device-CommonMethod-chainMode(direction: Axis, style: ChainStyle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | [Axis](../arkts-apis/arkts-arkui-axis-e.md) | 是 | 链的方向。 |
| style | [ChainStyle](arkts-arkui-chainstyle-e.md) | 是 | 链的样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="chainweight"></a>
## chainWeight

```TypeScript
chainWeight(chainWeight: ChainWeightOptions): T
```

对形成链的组件进行重新布局。仅当父组件为[RelativeContainer](RelativeContainer)时生效。

> **说明：**  
>  
> 从API version 23开始，支持 [attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-chainWeight(chainWeight: ChainWeightOptions): T--><!--Device-CommonMethod-chainWeight(chainWeight: ChainWeightOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chainWeight | [ChainWeightOptions](../arkts-apis/arkts-arkui-chainweightoptions-i.md) | 是 | 设置了chainWeight属性的组件与同一条链上的兄弟组件在水平或竖直方向的尺寸会按照设置的权重进行分配，分配时会忽略组件本身尺寸设置，按分配的权重自适应占满剩余空间。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="clickeffect"></a>
## clickEffect

```TypeScript
clickEffect(value: ClickEffect | null): T
```

设置当前组件的点击回弹效果。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-clickEffect(value: ClickEffect | null): T--><!--Device-CommonMethod-clickEffect(value: ClickEffect | null): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ClickEffect](arkts-arkui-clickeffect-i.md) \| null | 是 | 设置当前组件点击回弹效果。<br/>**说明：**<br/>可通过null取消点击回弹效果。<br/>不建议在组件大小动态变化的场景中使用该功能。<br/   >当组件无法触发通用事件时，不支持该属性。<br/>回弹触发缩放后可能造成触摸点不在控件上，控件上无法响应手势事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="clickeffect-1"></a>
## clickEffect

```TypeScript
clickEffect(effect: Optional<ClickEffect | null>): T
```

设置当前组件的点击回弹效果。与[clickEffect](arkts-arkui-commonmethod-c.md#clickeffect-1)相比，新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-clickEffect(effect: Optional<ClickEffect | null>): T--><!--Device-CommonMethod-clickEffect(effect: Optional<ClickEffect | null>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [Optional](arkts-arkui-optional-t.md)&lt;ClickEffect \| null&gt; | 是 | 设置当前组件的点击回弹效果。<br/>**说明：**<br/>可通过undefined或者null取消点击回弹效果。<br/>不建议在组件大小动态变化的场景中使用该功能。<br/>当组件无法触发通用事件时，不支持该属性。<br/>回弹触发缩放后可能造成触摸点不在控件上，控件上无法响应手势事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="clip"></a>
## clip

```TypeScript
clip(value: boolean): T
```

是否对子组件超出当前组件范围外的区域进行裁剪。不设置该接口时，默认不对子组件超出当前组件范围外的区域进行裁剪。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-clip(value: boolean): T--><!--Device-CommonMethod-clip(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置子组件是否按照当前组件边缘轮廓进行裁剪。<br/>true表示子组件按照当前组件边缘轮廓进行裁剪，false表示不对子组件进行裁剪。 <br/>**说明：** 设置为true后，子组件超出当前组件范围外的区域将不响应绑定的手势事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="clip-1"></a>
## clip

```TypeScript
clip(clip: Optional<boolean>): T
```

是否对子组件超出当前组件范围外的区域进行裁剪。不设置该接口时，默认不对子组件超出当前组件范围外的区域进行裁剪。与[clip<sup>12+</sup>](arkts-arkui-commonmethod-c.md#clip-1)相比，新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-clip(clip: Optional<boolean>): T--><!--Device-CommonMethod-clip(clip: Optional<boolean>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clip | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置子组件是否按照当前组件边缘轮廓进行裁剪。<br/>**说明：** 设置为true后，子组件超出当前组件范围外的区域将不响应绑定的手势事件。<br/>当clip的值为undefined时，恢复为不对子组件超出当前组件范围外的区域进行裁剪。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="clip-2"></a>
## clip

```TypeScript
clip(value: boolean | CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute): T
```

按指定的形状对当前组件进行裁剪。

> **说明：**

**起始版本：** 7

**废弃版本：** 12

**替代接口：** [clipShape(value:](arkts-arkui-commonmethod-c.md#clipshape-1)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-clip(value: boolean | CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute): T--><!--Device-CommonMethod-clip(value: boolean | CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| CircleAttribute \| EllipseAttribute \| PathAttribute \| RectAttribute | 是 | 参数为相应类型的组件，按指定的形状对当前组件进行裁剪；参数为boolean类型时，设置是否按照父容器边缘轮廓进行裁剪。<br/>默认值：false <br/>**说明：** 参数为对应类型的组件时，裁剪不会导致被裁剪区域无法响应绑定的手势事件。参数为boolean类型时，裁剪会导致被裁剪区域无法响应绑定的手势事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="clipshape"></a>
## clipShape

```TypeScript
clipShape(value: CircleShape | EllipseShape | PathShape | RectShape): T
```

按指定的形状（形状中可包含位置信息）对当前组件进行裁剪。

> **说明：**  
>  
> 不同的形状支持的属性范围不同，路径是一种形状，除此之外还有椭圆、矩形等形状。  
>  
> 路径的形状不支持设置宽度和高度。具体形状支持的属性参考具体形状的文档。  
>  
> 形状中的[fill](../arkts-apis/arkts-arkui-arkui-shape-commonshapemethod-c.md#fill-1)属性对clipShape接口不生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-clipShape(value: CircleShape | EllipseShape | PathShape | RectShape): T--><!--Device-CommonMethod-clipShape(value: CircleShape | EllipseShape | PathShape | RectShape): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CircleShape](arkts-arkui-circleshape-t.md) \| EllipseShape \| PathShape \| RectShape | 是 | 参数为相应类型的组件，按指定的形状（形状中可包含位置信息）对当前组件进行裁剪。<br/>**说明：** 裁剪不会导致被裁剪区域无法响应绑定的手势事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="clipshape-1"></a>
## clipShape

```TypeScript
clipShape(shape: Optional<CircleShape | EllipseShape | PathShape | RectShape>): T
```

按指定的形状（形状中可包含位置信息）对当前组件进行裁剪。与[clipShape<sup>12+</sup>](arkts-arkui-commonmethod-c.md#clipshape-1)相比，新增了对undefined类型的支持。

> **说明：**  
>  
> 不同的形状支持的属性范围不同，路径是一种形状，除此之外还有椭圆、矩形等形状。  
>  
> 路径的形状不支持设置宽度和高度。具体形状支持的属性参考具体形状的文档。  
>  
> 形状中的[fill](../arkts-apis/arkts-arkui-arkui-shape-commonshapemethod-c.md#fill-1)属性对clipShape接口不生效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-clipShape(shape: Optional<CircleShape | EllipseShape | PathShape | RectShape>): T--><!--Device-CommonMethod-clipShape(shape: Optional<CircleShape | EllipseShape | PathShape | RectShape>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shape | [Optional](arkts-arkui-optional-t.md)&lt;CircleShape \| EllipseShape \| PathShape \| RectShape&gt; | 是 | 参数为相应类型的组件，按指定的形状（形状中可包含位置信息）对当前组件进行裁剪。<br/>**说明：** 裁剪不会导致被裁剪区域无法响应绑定的手势事件。<br/>当shape的值为undefined时，会重置当前值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="colorblend"></a>
## colorBlend

```TypeScript
colorBlend(value: Color | string | Resource): T
```

为组件添加颜色叠加效果。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-colorBlend(value: Color | string | Resource): T--><!--Device-CommonMethod-colorBlend(value: Color | string | Resource): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Color](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-scenetypes-color-i.md) \| string \| Resource | 是 | 为当前组件添加颜色叠加效果，入参为叠加的颜色字符串。取值可为string类型，如'0x000000'，'rgba(0,0,0,1)'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="colorblend-1"></a>
## colorBlend

```TypeScript
colorBlend(color: Optional<Color | string | Resource>): T
```

为组件添加颜色叠加效果。与[colorBlend](arkts-arkui-commonmethod-c.md#colorblend-1)相比，color参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-colorBlend(color: Optional<Color | string | Resource>): T--><!--Device-CommonMethod-colorBlend(color: Optional<Color | string | Resource>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)&lt;Color \| string \| Resource&gt; | 是 | 为当前组件添加颜色叠加效果，入参为叠加的颜色。取值可为string类型，如'0x000000'，'rgba(0,0,0,1)'。<br/>当color的值为undefined时，恢复为无颜色叠加的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="compositingfilter"></a>
## compositingFilter

```TypeScript
compositingFilter(filter: Filter): T
```

设置合成滤镜视觉效果。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-compositingFilter(filter: Filter): T--><!--Device-CommonMethod-compositingFilter(filter: Filter): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) | 是 | 合成滤镜视觉效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="constraintsize"></a>
## constraintSize

```TypeScript
constraintSize(value: ConstraintSizeOptions): T
```

设置约束尺寸，组件布局时，进行尺寸范围限制。

从API version 10开始，该接口支持calc计算特性。

**constraintSize(minWidth/maxWidth/minHeight/maxHeight)取值对width/height影响：**

| 缺省值 | 结果 |  
| ---------------------------------------- | ---------------------------------------- |  
| \ | width=MAX(minWidth,MIN(maxWidth,width))<br/>height=MAX(minHeight,MIN(maxHeight,height)) |  
| maxWidth、maxHeight | width=MAX(minWidth,width)<br/>height=MAX(minHeight,height) |  
| minWidth、minHeight | width=MIN(maxWidth,width)<br/>height=MIN(maxHeight,height) |  
| width、height |若minWidth<maxWidth，组件自身布局逻辑生效，width取值范围为[minWidth,maxWidth]；否则，width=MAX(minWidth,maxWidth)。<br/>若minHeight<maxHeig ht，组件自身布局逻辑生效，height取值范围为[minHeight,maxHeight]；否则，height=MAX(minHeight,maxHeight)。 |  
| width与maxWidth、height与maxHeight | width=minWidth<br/>height=minHeight |  
| width与minWidth、height与minHeight | 组件自身布局逻辑生效，width取值约束为不大于maxWidth。<br/>组件自身布局逻辑生效，height取值约束为不大于maxHeight。 |  
| minWidth与maxWidth、minHeight与maxHeight | width以所设值为基础，根据其他布局属性发生可能的拉伸或者压缩。<br/>height以所设值为基础，根据其他布局属性发生可能的拉伸或者压缩。|  
| width与minWidth与maxWidth | 使用父容器传递的布局限制进行布局。 |  
| height与minHeight与maxHeight | 使用父容器传递的布局限制进行布局。 |

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-constraintSize(value: ConstraintSizeOptions): T--><!--Device-CommonMethod-constraintSize(value: ConstraintSizeOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | 是 | 设置约束尺寸。constraintSize的优先级高于Width和Height。取值结果参考constraintSize取值对width/height影响。<br><br/>默认值：<br/>{<br/>minWidth:&nbsp;0,<br/>maxWidth:&nbsp;Infinity,<br/>minHeight:&nbsp;0,<br/>maxHeight:&nb sp;Infinity<br/>}<br/>异常值：数值开头的字符串仅解析出数字部分，非数值开头的字符串解析为0；其它异常值时，constraintSize属性恢复到不配置时的默认行为。<br/>单位：vp<br/>。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="contrast"></a>
## contrast

```TypeScript
contrast(value: number): T
```

为组件添加对比度效果。不通过该接口设置时，默认无变化。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-contrast(value: number): T--><!--Device-CommonMethod-contrast(value: number): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 为当前组件添加对比度效果，入参为对比度的值。值为1时，显示原图，大于1时，值越大对比度越高，图像越清晰醒目，小于1时，值越小对比度越低，当对比度为0时，图像变为全灰。<br/>推荐取值范围：[0, 10)<br/>**说明：**<br/>设置小于0的值时，按值为0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@FaAndStageModel@crossplatform@form@atomicservice |

<a id="contrast-1"></a>
## contrast

```TypeScript
contrast(contrast: Optional<number>): T
```

为组件添加对比度效果。不通过该接口设置时，默认无变化。与[contrast](arkts-arkui-commonmethod-c.md#contrast-1)相比，contrast参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-contrast(contrast: Optional<number>): T--><!--Device-CommonMethod-contrast(contrast: Optional<number>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contrast | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 为当前组件添加对比度效果，入参为对比度的值。值为1时，显示原图，大于1时，值越大对比度越高，图像越清晰醒目，小于1时，值越小对比度越低，当对比度为0时，图像变为全灰。<br/>推荐取值范围：[0, 10)<br/>**说明：**<br/>设置小于0的值时，按值为0处理。<br/>当contrast的值为undefined时，恢复为对比度为1的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="customproperty"></a>
## customProperty

```TypeScript
customProperty(name: string, value: Optional<Object>): T
```

设置组件的自定义属性。

API版本26.0.0之前，[自定义组件](docroot://ui/state-management/arkts-create-custom-components.md)不支持设置自定义属性。

从API版本26.0.0开始，自定义组件支持设置并读取自定义属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-customProperty(name: string, value: Optional<Object>): T--><!--Device-CommonMethod-customProperty(name: string, value: Optional<Object>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 自定义属性的名称。 |
| value | [Optional](arkts-arkui-optional-t.md)&lt;Object&gt; | 是 | 自定义属性的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 当前控件 |

<a id="defaultfocus"></a>
## defaultFocus

```TypeScript
defaultFocus(value: boolean): T
```

设置当前组件是否为当前[层级页面](docroot://ui/arkts-common-events-focus-event.md#基础概念)上的默认焦点。当未设置defaultFocus时，组件默认不为当前层级页面的默认焦点。

> **说明：**  
>  
> 可以设置默认焦点的页面指的是支持页面路由或是弹窗类的容器组件，例如Page、NaviDestination、NavBar、PopUp、Dialog等。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-defaultFocus(value: boolean): T--><!--Device-CommonMethod-defaultFocus(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置当前组件是否为当前[层级页面](docroot://ui/arkts-common-events-focus-event.md#基础概念)上的默认焦点，仅在初次创建的层级页面第一次进入时生效。<br/>**说明：** <br/>值为true则表示为默认焦点，值为false时无效。<br/>若层级页面内无任何组件设置defaultFocus(true)，API version 11及之前，层级页面的默认焦点是当前层级页面上首个可获焦的非容器组件，API version 11之后，层级页面的默认焦点就是层级页面的根容器。<br/>若某层级页面内有多个组件设置了defaultFocus(true)，则以组件树深度遍历找到的第一个组件为默认焦点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="direction"></a>
## direction

```TypeScript
direction(value: Direction): T
```

设置当前组件绘制区域内主轴方向上的布局，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-direction(value: Direction): T--><!--Device-CommonMethod-direction(value: Direction): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Direction](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod-direction-e.md) | 是 | 设置当前组件绘制区域内主轴方向上的布局。<br/>属性配置为auto的时候，按照系统语言方向进行布局。<br/>该属性在Column组件上不生效。<br/>默认值：Direction.Auto<br/>direction取undefined或null时按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="displaypriority"></a>
## displayPriority

```TypeScript
displayPriority(value: number): T
```

设置当前组件在布局容器中显示的优先级。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-displayPriority(value: number): T--><!--Device-CommonMethod-displayPriority(value: number): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置当前组件在布局容器中显示的优先级。<br/>默认值：1<br/>**说明：**<br/>仅在[Row](Row)/[Column](Column)/[Flex(单行)](Flex)容器组件中生效。<br/> 小数点后的数字不作优先级区分，即区间为[x, x +1)内的数字视为相同优先级。例如：1.0与1.9为同一优先级。<br/>子组件的displayPriority均不大于1时，优先级没有区别。<br/>当子组件的displayPriority大于1时，displayPriority数值越大，优先级越高。若父容器空间不足，隐藏低优先级子组件。若某一优先级的子组件被隐藏，则优先级更低的子组件也都被隐藏<br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="doublesided"></a>
## doubleSided

```TypeScript
doubleSided(value: Optional<boolean>): T
```

是否绘制组件的双面。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-doubleSided(value: Optional<boolean>): T--><!--Device-CommonMethod-doubleSided(value: Optional<boolean>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否绘制组件的双面。<br/>设置为true表示组件的正面和背面都是可见的。<br/>设置为false表示组件的正面是可见的，旋转时组件的背面是不可见的。<br/>设置为undefined时效果和设置为true时保持一致，默认开启双面绘制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="dragpreview"></a>
## dragPreview

```TypeScript
dragPreview(value: CustomBuilder | DragItemInfo | string): T
```

设置组件浮起和拖拽过程中的预览图。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-dragPreview(value: CustomBuilder | DragItemInfo | string): T--><!--Device-CommonMethod-dragPreview(value: CustomBuilder | DragItemInfo | string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-custombuilder-t.md) \| DragItemInfo \| string | 是 | 设置组件浮起和拖拽过程中的预览图，仅在[onDragStart](arkts-arkui-commonmethod-c.md#ondragstart-1)拖拽方式中有效。<br/>当组件支持拖拽并同时设置[bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu-1)的预览图时，则长按浮起的预览图以[bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu-1)设置的预览图为准。开发者在[onDragStart](arkts-arkui-commonmethod-c.md#ondragstart-1)中返回的背板图优先级低于[dragPreview](arkts-arkui-commonmethod-c.md#dragpreview-1)设置的预览图，当设置了[dragPreview](arkts-arkui-commonmethod-c.md#dragpreview-1)预览图时，拖拽过程中的背板图使用[dragPreview](arkts-arkui-commonmethod-c.md#dragpreview-1)预览图。由于[CustomBuilder](docroot://reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8)需要离线渲染之后才能使用，因此存在一定的性能开销和时延，推荐优先使用 [DragItemInfo](arkts-arkui-dragiteminfo-i.md)中的[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)方式。<br/> 当传入类型为string的id时，则将id对应组件的截图作为预览图。如果id对应的组件无法查找到，或者id对应的组件[Visibility](../arkts-apis/arkts-arkui-visibility-e.md)属性设置成None/Hidden，则对组件自身进行截图作为拖拽预览图。目前截图不含有亮度、阴影、模糊和旋转等视觉效果。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="dragpreview-1"></a>
## dragPreview

```TypeScript
dragPreview(preview: CustomBuilder | DragItemInfo | string, config?: PreviewConfiguration): T
```

自定义组件拖拽过程中的预览图，仅用于设置浮起效果或者禁用浮起效果。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-dragPreview(preview: CustomBuilder | DragItemInfo | string, config?: PreviewConfiguration): T--><!--Device-CommonMethod-dragPreview(preview: CustomBuilder | DragItemInfo | string, config?: PreviewConfiguration): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| preview | [CustomBuilder](arkts-arkui-custombuilder-t.md) \| DragItemInfo \| string | 是 | 设置组件浮起和拖拽过程中的预览图，仅在[onDragStart](arkts-arkui-commonmethod-c.md#ondragstart-1)拖拽方式中有效。<br/>当组件支持拖拽并同时设置[bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu-1)的预览图时，则长按浮起的预览图以[bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu-1)设置的预览图为准。开发者在[onDragStart](arkts-arkui-commonmethod-c.md#ondragstart-1)中返回的背板图优先级低于[dragPreview](arkts-arkui-commonmethod-c.md#dragpreview-1)设置的预览图，当设置了[dragPreview](arkts-arkui-commonmethod-c.md#dragpreview-1)预览图时，拖拽过程中的背板图使用[dragPreview](arkts-arkui-commonmethod-c.md#dragpreview-1)预览图。由于[CustomBuilder](arkts-arkui-custombuilder-t.md)需要离线渲染之后才能使用，因此存在一定的性能开销和时延，推荐优先使用 [DragItemInfo](arkts-arkui-dragiteminfo-i.md)中的[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)方式。<br/> 当传入类型为string的id时，则将id对应组件的截图作为预览图。如果id对应的组件无法查找到，或者id对应的组件[Visibility](../arkts-apis/arkts-arkui-visibility-e.md)属性设置成None/Hidden，则对组件自身进行截图作为拖拽预览图。目前截图不含有亮度、阴影、模糊和旋转等视觉效果。 |
| config | [PreviewConfiguration](arkts-arkui-previewconfiguration-i.md) | 否 | 对自定义拖拽过程中的预览图进行配置。<br/>只对[dragPreview](arkts-arkui-commonmethod-c.md#dragpreview-1)中的预览生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="dragpreviewoptions"></a>
## dragPreviewOptions

```TypeScript
dragPreviewOptions(value: DragPreviewOptions, options?: DragInteractionOptions): T
```

设置拖拽过程中预览图处理模式，数量角标的显示以及预览图浮起的交互模式。不支持onItemDragStart拖拽方式。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-dragPreviewOptions(value: DragPreviewOptions, options?: DragInteractionOptions): T--><!--Device-CommonMethod-dragPreviewOptions(value: DragPreviewOptions, options?: DragInteractionOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DragPreviewOptions](arkts-arkui-dragpreviewoptions-i.md) | 是 | 设置拖拽过程中预览图处理模式及数量角标的显示。 |
| options | [DragInteractionOptions](arkts-arkui-draginteractionoptions-i.md) | 否 | 设置拖拽过程中预览图浮起的交互模式。<br/>默认值：空<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="draggable"></a>
## draggable

```TypeScript
draggable(value: boolean): T
```

设置该组件是否允许拖拽。默认情况下，组件不允许拖拽。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-draggable(value: boolean): T--><!--Device-CommonMethod-draggable(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置该组件是否允许进行拖拽。true表示允许拖拽，false表示不允许拖拽。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="drawmodifier"></a>
## drawModifier

```TypeScript
drawModifier(modifier: DrawModifier | undefined): T
```

Sets the drawModifier of the current component.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-drawModifier(modifier: DrawModifier | undefined): T--><!--Device-CommonMethod-drawModifier(modifier: DrawModifier | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [DrawModifier](arkts-arkui-drawmodifier-c.md) \| undefined | 是 | drawModifier used to draw, or undefined if it is not available. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="enableclicksoundeffect"></a>
## enableClickSoundEffect

```TypeScript
enableClickSoundEffect(enabled: boolean | undefined): T
```

设置组件是否启用默认点击音效。是否能够发音依赖设备声音相关的设置，如静音模式下不会播放音效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-enableClickSoundEffect(enabled: boolean | undefined): T--><!--Device-CommonMethod-enableClickSoundEffect(enabled: boolean | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 | 设置此组件是否启用默认点击音效。true表示启用默认点击音效；false表示禁用默认点击音效。值为undefined时，启用默认点击音效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="enabled"></a>
## enabled

```TypeScript
enabled(value: boolean): T
```

设置组件是否可交互。当未设置enabled时，组件默认可交互。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-enabled(value: boolean): T--><!--Device-CommonMethod-enabled(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 值为true表示组件可交互，响应点击等操作。<br/>值为false表示组件不可交互，不响应点击等操作。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="expandsafearea"></a>
## expandSafeArea

```TypeScript
expandSafeArea(types?: Array<SafeAreaType>, edges?: Array<SafeAreaEdge>): T
```

控制组件扩展其安全区域。

> **说明：**  
>  
> - 设置expandSafeArea属性进行组件绘制扩展时，建议组件尺寸不要设置固定宽高（百分比除外），当设置固定宽高（包括设置'auto'）时，扩展安全区域的方向只支持[SafeAreaEdge.TOP,SafeAreaEdge.START]，扩展后的组件尺寸保持不变。  
>  
> - 安全区域不会限制内部组件的布局和大小，不会裁剪内部组件。  
>  
> - 当父容器为滚动容器时，组件设置expandSafeArea属性后，自身不会延伸，但仍可触发其子节点中设置了expandSafeArea的延伸范围更新。  
>  
> - 设置expandSafeArea()时，不传参，走默认值处理；设置expandSafeArea([],[])时，相当于入参是空数组，此时expandSafeArea属性设置无效。  
>  
> - 组件设置expandSafeArea生效的条件为：  
> 1.type为SafeAreaType.KEYBOARD时默认生效，表现为组件不避让键盘。<br/>  
> 2.设置其他type，组件的边界与安全区域重合时组件能够延伸到安全区域下。例如：设备顶部状态栏高度100，那么组件在屏幕中的绝对位置需要为0 <= y <= 100。  
>  
> - 组件延伸到避让区时，在避让区的事件如点击事件等可能会被系统拦截，优先给状态栏等系统组件响应。  
>  
> -滚动类容器内的组件不建议设置expandSafeArea属性，如果设置，需要按照组件嵌套关系，将当前节点到滚动类祖先容器间所有直接节点设置expandSafeArea属性，否则expandSafeArea属性在滚动后可能会失效，写法参考[示例7](#示例7滚动类容器扩展安全区)。  
>  
> - expandSafeArea属性仅作用于当前组件，不会向父组件或子组件传递，因此使用过程中，所有相关组件均需配置。  
>  
> -同时设置expandSafeArea和position属性时，position属性会优先生效，expandSafeArea属性会后生效。对于未设置position、offset等绘制属性的组件，如果其边界未与避让区重叠，设置exp andSafeArea属性将不生效，如弹窗和半模态组件。  
>  
> - 对于expandSafeArea属性无法生效的场景，若要将组件部署在避让区，需要手动调整组件的坐标。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-expandSafeArea(types?: Array<SafeAreaType>, edges?: Array<SafeAreaEdge>): T--><!--Device-CommonMethod-expandSafeArea(types?: Array<SafeAreaType>, edges?: Array<SafeAreaEdge>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;SafeAreaType&gt; | 否 | 配置扩展安全区域的类型。未添加Metadata配置项时，页面不避让挖孔，CUTOUT类型不生效。<br>默认值： [SafeAreaType.SYSTEM, SafeAreaType.CUTOUT, SafeAreaType.KEYBOARD]。<br>非法值：按默认值处理。 |
| edges | Array&lt;SafeAreaEdge&gt; | 否 | 配置扩展安全区域的边缘。<br>默认值： [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM, SafeAreaEdge.START, SafeAreaEdge.END]。<br>非法值：按默认值处理。扩展至所有避让区域。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="flexbasis"></a>
## flexBasis

```TypeScript
flexBasis(value: number | string): T
```

设置组件的基准尺寸。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-flexBasis(value: number | string): T--><!--Device-CommonMethod-flexBasis(value: number | string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 设置组件在父容器主轴方向上的基准尺寸。<br/>默认值：'auto'（表示组件在主轴方向上的基准尺寸为组件原本的大小）。<br/>string类型可选值：可以转化为数字的字符串（如'10'）或带长度单位的字符串（如'10px'）或'auto'，不允许设置百分比字符串。<br/>number：取值范围(0,+∞)，单位为vp。<br/>异常值：默认为'auto'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="flexgrow"></a>
## flexGrow

```TypeScript
flexGrow(value: number): T
```

设置组件在父容器的剩余空间所占比例。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-flexGrow(value: number): T--><!--Device-CommonMethod-flexGrow(value: number): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置父容器在主轴方向上的剩余空间分配给此属性所在组件的比例。<br/>取值范围：[0, +∞)<br/>默认值：0<br/>设置异常值时，该属性为默认值。<br>取值应为≥0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="flexshrink"></a>
## flexShrink

```TypeScript
flexShrink(value: number): T
```

设置父容器压缩尺寸分配给此属性所在组件的比例。当父容器为Column、Row时，需设置主轴方向的尺寸。

使用[getInspectorByKey](ts-universal-attributes-component-id.md#getinspectorbykey9)获取flexShrink属性时，如果该节点未设置flexShrink属性，默认返回1。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-flexShrink(value: number): T--><!--Device-CommonMethod-flexShrink(value: number): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置父容器压缩尺寸分配给此属性所在组件的比例。<br>取值限定为整数，父容器为 [Column](Column) 、[Row](Row)时， 取值范围[0,+∞).<br/>父容器为[Flex](Flex)时，默认值：1<br/>[constraintSize](arkts-arkui-commonmethod-c.md#constraintsize-1)限制组件的尺寸范围.Column和Row即使设置了constraintSize，在未设置主轴尺寸width/height/size时仍遵守默认布局行为，在主轴上自适应子组件尺寸，此时flexShrink不生效.<br/>设置异常值时，该属性为默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="focusbox"></a>
## focusBox

```TypeScript
focusBox(style: FocusBoxStyle): T
```

设置当前组件系统焦点框样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-focusBox(style: FocusBoxStyle): T--><!--Device-CommonMethod-focusBox(style: FocusBoxStyle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [FocusBoxStyle](../arkts-apis/arkts-arkui-focusboxstyle-i.md) | 是 | 设置当前组件系统焦点框样式。<br/>**说明：** <br/>仅影响走焦状态下展示了系统焦点框的组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="focusontouch"></a>
## focusOnTouch

```TypeScript
focusOnTouch(value: boolean): T
```

设置当前组件是否支持点击获焦能力。当组件未设置focusOnTouch时，组件默认不支持点击获焦能力。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-focusOnTouch(value: boolean): T--><!--Device-CommonMethod-focusOnTouch(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置当前组件是否支持点击获焦能力。true表示组件支持点击获焦，false表示不支持点击获焦。<br/>**说明：** <br/>仅在组件可点击时才能正常获取焦点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="focusscopeid"></a>
## focusScopeId

```TypeScript
focusScopeId(id: string, isGroup?: boolean): T
```

设置当前容器组件的id标识，以及是否为焦点组。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-focusScopeId(id: string, isGroup?: boolean): T--><!--Device-CommonMethod-focusScopeId(id: string, isGroup?: boolean): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 设置当前容器组件的id标识。<br/>**说明：** <br/>单个[层级页面](docroot://ui/arkts-common-events-focus-event.md#基础概念)下，id标识全局唯一，不可重复。 |
| isGroup | boolean | 否 | 设置当前容器组件是否为焦点组。true表示容器组件为焦点组，false表示容器组件不是焦点组。默认值为false。<br/>**说明：** <br/>焦点组不可嵌套，不可重复配置。<br/> 焦点组不能和tabIndex混用。<br/>配置焦点组的目的是使得容器及容器内的元素可以按照焦点组规则走焦。焦点组走焦规则：<br/>1.焦点组容器内只能通过方向键走焦，tab键会使焦点跳出焦点组容器。<br/>2.通过方向键使焦点从焦点组容器外切换到焦点组容器内时，若焦点组容器内存在优先级为PREVIOUS的组件，则优先级为PREVIOUS的组件获焦，否则，由焦点组容器内上次获焦的组件获焦。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="focusscopeid-1"></a>
## focusScopeId

```TypeScript
focusScopeId(id: string, isGroup?: boolean, arrowStepOut?: boolean): T
```

设置当前容器组件的id标识，以及是否为焦点组。新增参数arrowStepOut，用于设置能否使用方向键走焦出当前焦点组。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-focusScopeId(id: string, isGroup?: boolean, arrowStepOut?: boolean): T--><!--Device-CommonMethod-focusScopeId(id: string, isGroup?: boolean, arrowStepOut?: boolean): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 设置当前容器组件的id标识。<br/>**说明：** <br/>单个[层级页面](docroot://ui/arkts-common-events-focus-event.md#基础概念)下，id标识全局唯一，不可重复。 |
| isGroup | boolean | 否 | 设置当前容器组件是否为焦点组。true表示容器组件为焦点组，false表示容器组件不是焦点组。默认值为false。<br/>**说明：** <br/>焦点组不可嵌套，不可重复配置。<br/> 焦点组不能和tabIndex混用。<br/>配置焦点组的目的是使得容器及容器内的元素可以按照焦点组规则走焦。焦点组走焦规则：<br/>1.焦点组容器内只能通过方向键走焦，tab键会使焦点跳出焦点组容器。<br/>2.通过方向键使焦点从焦点组容器外切换到焦点组容器内时，若焦点组容器内存在优先级为PREVIOUS的组件，则优先级为PREVIOUS的组件获焦，否则，由焦点组容器内上次获焦的组件获焦。 |
| arrowStepOut | boolean | 否 | 设置能否使用方向键走焦出当前焦点组。true表示可以使用方向键走焦出当前焦点组，false表示不能使用方向键走焦出当前焦点组。默认值为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="focusscopepriority"></a>
## focusScopePriority

```TypeScript
focusScopePriority(scopeId: string, priority?: FocusPriority): T
```

设置当前组件在指定容器内获焦的优先级。需要配合[focusScopeId](arkts-arkui-commonmethod-c.md#focusscopeid-1)一起使用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-focusScopePriority(scopeId: string, priority?: FocusPriority): T--><!--Device-CommonMethod-focusScopePriority(scopeId: string, priority?: FocusPriority): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scopeId | string | 是 |  |
| priority | [FocusPriority](../arkts-apis/arkts-arkui-focuspriority-e.md) | 否 | 获焦优先级。<br/>**说明：** <br/>未设置priority时，默认为AUTO优先级。<br/>优先级对走焦以及获焦组件的影响：<br/>1.容器整体获焦（[层级页面](docroot://ui/arkts-common-events-focus-event.md#基础概念)切换/焦点切换到焦点组/容器组件使用requestFocus申请焦点）时，若容器内存在优先级为PREVIOUS的组件，则优先级为PREVIOUS的组件获焦，否则，由容器内上次获焦的组件获焦。<br/>2.容器非整体获焦（非焦点组场景下使用tab键/方向键走焦）时，若容器为首次获焦，则容器内优先级最高的组件获焦，若容器非首次获焦，不考虑优先级按照位置顺序走焦。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="focusable"></a>
## focusable

```TypeScript
focusable(value: boolean): T
```

设置当前组件是否可以获焦。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-focusable(value: boolean): T--><!--Device-CommonMethod-focusable(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置当前组件是否可以获焦，true表示组件可以获焦，false表示组件不可获焦。<br/>**说明：**<br/>存在默认交互逻辑的组件例如[Button](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-mouseevent-button-e.md)、[TextInput](arkts-arkui-textinput.md)等，默认即为可获焦，[Text](../../apis-arkgraphics2d/arkts-apis/arkts-graphics-text.md)、[Image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)等组件则默认状态为不可获焦。不可获焦状态下，无法触发[焦点事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="foregroundblurstyle"></a>
## foregroundBlurStyle

```TypeScript
foregroundBlurStyle(value: BlurStyle, options?: ForegroundBlurStyleOptions): T
```

为当前组件提供内容模糊能力。

> **说明：**  
>  
> 从API version 18开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-foregroundBlurStyle(value: BlurStyle, options?: ForegroundBlurStyleOptions): T--><!--Device-CommonMethod-foregroundBlurStyle(value: BlurStyle, options?: ForegroundBlurStyleOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BlurStyle](arkts-arkui-blurstyle-e.md) | 是 | 内容模糊样式。 |
| options | [ForegroundBlurStyleOptions](arkts-arkui-foregroundblurstyleoptions-i.md) | 否 | 内容模糊选项。默认值请参考[ForegroundBlurStyleOptions](docroot://reference/apis-arkui/arkui-ts/ts-universal-attributes-foreground-blur-style.md#foregroundblurstyleoptions)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="foregroundblurstyle-1"></a>
## foregroundBlurStyle

```TypeScript
foregroundBlurStyle(style: Optional<BlurStyle>, options?: ForegroundBlurStyleOptions): T
```

为当前组件提供内容模糊能力。与[foregroundBlurStyle](arkts-arkui-commonmethod-c.md#foregroundblurstyle-1)相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-foregroundBlurStyle(style: Optional<BlurStyle>, options?: ForegroundBlurStyleOptions): T--><!--Device-CommonMethod-foregroundBlurStyle(style: Optional<BlurStyle>, options?: ForegroundBlurStyleOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;BlurStyle&gt; | 是 |  |
| options | [ForegroundBlurStyleOptions](arkts-arkui-foregroundblurstyleoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="foregroundblurstyle-2"></a>
## foregroundBlurStyle

```TypeScript
foregroundBlurStyle(style: Optional<BlurStyle>, options?: ForegroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): T
```

为当前组件提供内容模糊能力。与[foregroundBlurStyle<sup>18+</sup>](arkts-arkui-commonmethod-c.md#foregroundblurstyle-1)相比，新增了sysOptions参数，即支持系统自适应调节参数。

> **说明：**  
>  
> foregroundBlurStyle接口为实时模糊接口，每帧执行实时渲染，性能负载较大。当模糊内容与模糊半径均无需变动时，推荐采用静态模糊接口  
> [blur](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-effectkit-filter-i.md#blur-1)。最佳实践请参考：  
> [图像模糊动效优化-使用场景](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-fuzzy-scene-performance-optimization#section4945532519)。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-foregroundBlurStyle(style: Optional<BlurStyle>, options?: ForegroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): T--><!--Device-CommonMethod-foregroundBlurStyle(style: Optional<BlurStyle>, options?: ForegroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;BlurStyle&gt; | 是 |  |
| options | [ForegroundBlurStyleOptions](arkts-arkui-foregroundblurstyleoptions-i.md) | 否 |  |
| sysOptions | [SystemAdaptiveOptions](arkts-arkui-systemadaptiveoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="foregroundcolor"></a>
## foregroundColor

```TypeScript
foregroundColor(value: ResourceColor | ColoringStrategy): T
```

Provides the general foreground color capability of UI components, and assigns color values according to the characteristics of components.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-foregroundColor(value: ResourceColor | ColoringStrategy): T--><!--Device-CommonMethod-foregroundColor(value: ResourceColor | ColoringStrategy): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| ColoringStrategy | 是 | Foreground color. The value can be a specific color or a coloring strategy. The [attribute animation](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md) is not supported. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component.@stagemodelonly@crossplatform@atomicservice |

<a id="foregroundcolor-1"></a>
## foregroundColor

```TypeScript
foregroundColor(color: Optional<ResourceColor | ColoringStrategy>): T
```

Provides the general foreground color capability of UI components, and assigns color values according to the characteristics of components.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-foregroundColor(color: Optional<ResourceColor | ColoringStrategy>): T--><!--Device-CommonMethod-foregroundColor(color: Optional<ResourceColor | ColoringStrategy>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor \| ColoringStrategy&gt; | 是 | -Foreground color. The value can be a specific color |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component.@stagemodelonly@crossplatform@atomicservice |

<a id="foregroundeffect"></a>
## foregroundEffect

```TypeScript
foregroundEffect(options: ForegroundEffectOptions): T
```

设置组件的前景属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-foregroundEffect(options: ForegroundEffectOptions): T--><!--Device-CommonMethod-foregroundEffect(options: ForegroundEffectOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ForegroundEffectOptions](arkts-arkui-foregroundeffectoptions-i.md) | 是 | 设置组件前景属性包括：模糊半径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="foregroundfilter"></a>
## foregroundFilter

```TypeScript
foregroundFilter(filter: Filter): T
```

设置前景滤镜（内容）视觉效果。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-foregroundFilter(filter: Filter): T--><!--Device-CommonMethod-foregroundFilter(filter: Filter): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) | 是 | 前景滤镜（内容）视觉效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="freeze"></a>
## freeze

```TypeScript
freeze(value: boolean): T
```

设置当前控件和子控件是否整体离屏渲染绘制后重复绘制缓存，不再进行内部属性更新。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-freeze(value: boolean): T--><!--Device-CommonMethod-freeze(value: boolean): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置当前控件和子控件是否整体离屏渲染绘制后重复绘制缓存，不再进行内部属性更新。当前控件的不透明度不为1时绘制效果可能有差异。<br/>默认值：false <br/> true时离屏渲染绘制后重复绘制缓存，false时离屏渲染绘制后不重复绘制缓存。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@atomicservice |

<a id="freeze-1"></a>
## freeze

```TypeScript
freeze(freeze: Optional<boolean>): T
```

设置当前控件和子控件是否整体离屏渲染绘制后重复绘制缓存，不再进行内部属性更新。与[freeze](arkts-arkui-commonmethod-c.md#freeze-1)相比，freeze参数新增了对undefined类型的支持。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-freeze(freeze: Optional<boolean>): T--><!--Device-CommonMethod-freeze(freeze: Optional<boolean>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| freeze | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置当前控件和子控件是否整体离屏渲染绘制后重复绘制缓存，不再进行内部属性更新。当前控件的不透明度不为1时绘制效果可能有差异。<br/>默认值：false<br/> true时离屏渲染绘制后重复绘制缓存，false时离屏渲染绘制后不重复绘制缓存。<br/>当freeze的值为undefined时，维持之前取值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@atomicservice |

<a id="geometrytransition"></a>
## geometryTransition

```TypeScript
geometryTransition(id: string): T
```

组件内隐式共享元素转场。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-geometryTransition(id: string): T--><!--Device-CommonMethod-geometryTransition(id: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 用于设置绑定关系，id置空字符串清除绑定关系避免参与共享行为，id可更换重新建立绑定关系。同一个id只能有两个组件绑定且是in/out不同类型角色，不能多个组件绑定同一个id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="geometrytransition-1"></a>
## geometryTransition

```TypeScript
geometryTransition(id: string, options?: GeometryTransitionOptions): T
```

组件内隐式共享元素转场。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-geometryTransition(id: string, options?: GeometryTransitionOptions): T--><!--Device-CommonMethod-geometryTransition(id: string, options?: GeometryTransitionOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 用于设置绑定关系，id置空字符串清除绑定关系避免参与共享行为，id可更换重新建立绑定关系。同一个id只能有两个组件绑定且是in/out不同类型角色，不能多个组件绑定同一个id。 |
| options | [GeometryTransitionOptions](arkts-arkui-geometrytransitionoptions-i.md) | 否 | 组件内共享元素转场动画参数。<br>默认值为 { follow: false }。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="gesture"></a>
## gesture

```TypeScript
gesture(gesture: GestureType, mask?: GestureMask): T
```

绑定手势。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-gesture(gesture: GestureType, mask?: GestureMask): T--><!--Device-CommonMethod-gesture(gesture: GestureType, mask?: GestureMask): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesture | [GestureType](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-gesturetype-t.md) | 是 | 绑定的手势类型。 |
| mask | [GestureMask](../arkts-apis/arkts-arkui-gesturemask-e.md) | 否 | 事件响应设置。<br/>默认值：GestureMask.Normal |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="gesturemodifier"></a>
## gestureModifier

```TypeScript
gestureModifier(modifier: GestureModifier): T
```

动态设置组件绑定的手势。

说明：gestureModifier不支持自定义组件。该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-gestureModifier(modifier: GestureModifier): T--><!--Device-CommonMethod-gestureModifier(modifier: GestureModifier): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [GestureModifier](arkts-arkui-gesturemodifier-i.md) | 是 | 动态设置当前组件的手势绑定，支持if/else语法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="grayscale"></a>
## grayscale

```TypeScript
grayscale(value: number): T
```

为组件添加灰度效果。上层渲染灰度会覆盖下层子组件渲染。不通过该接口设置时，默认无变化。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-grayscale(value: number): T--><!--Device-CommonMethod-grayscale(value: number): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 为当前组件添加灰度效果。值定义为灰度转换的比例，入参1.0则完全转为灰度图像，入参0.0则图像无变化，入参在0.0和1.0之间时，效果呈线性变化。<br/>取值范围：[0.0, 1.0]<br/>**说明：**<br/>设置小于0.0的值时，按值为0.0处理，设置大于1.0的值时，按值为1.0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="grayscale-1"></a>
## grayscale

```TypeScript
grayscale(grayscale: Optional<number>): T
```

为组件添加灰度效果。上层渲染灰度会覆盖下层子组件渲染。不通过该接口设置时，默认无变化。与[grayscale](arkts-arkui-commonmethod-c.md#grayscale-1)相比，grayscale参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-grayscale(grayscale: Optional<number>): T--><!--Device-CommonMethod-grayscale(grayscale: Optional<number>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| grayscale | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 为当前组件添加灰度效果。值定义为灰度转换的比例，入参1.0则完全转为灰度图像，入参0.0则图像无变化，入参在0.0和1.0之间时，效果呈线性变化。<br/>取值范围：[0.0, 1.0]<br/>**说明：**<br/>设置小于0.0的值时，按值为0.0处理，设置大于1.0的值时，按值为1.0处理。<br/>当grayscale的值为undefined时，取默认值0.0。恢复为无灰度效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="gridoffset"></a>
## gridOffset

```TypeScript
gridOffset(value: number): T
```

The default offset column number indicates the number of offset columns of the current component in the start direction of the parent component when the useSizeType attribute does not set the offset of the corresponding dimension. That is,the current component is located in the nth column.

**起始版本：** 11

**废弃版本：** 14

**替代接口：** grid_col/GridColInterface

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-gridOffset(value: number): T--><!--Device-CommonMethod-gridOffset(value: number): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform@atomicservice |

<a id="gridspan"></a>
## gridSpan

```TypeScript
gridSpan(value: number): T
```

Default number of occupied columns, indicating the number of occupied grid columns when the number of columns (span) of the corresponding size is not set in the useSizeType attribute.

**起始版本：** 11

**废弃版本：** 14

**替代接口：** grid_col/GridColInterface

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-gridSpan(value: number): T--><!--Device-CommonMethod-gridSpan(value: number): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform@atomicservice |

<a id="groupdefaultfocus"></a>
## groupDefaultFocus

```TypeScript
groupDefaultFocus(value: boolean): T
```

设置当前组件是否为当前组件所在容器获焦时的默认焦点。当组件未设置groupDefaultFocus时，组件默认不为当前组件所在容器获焦时的默认焦点。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-groupDefaultFocus(value: boolean): T--><!--Device-CommonMethod-groupDefaultFocus(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置当前组件是否为当前组件所在容器获焦时的默认焦点，仅在初次创建容器节点第一次获焦时生效。true表示当前组件为所在容器获焦时的默认焦点，false表示当前组件不是所在容器获焦时的默认焦点。<br/>**说明：** <br/>必须与[tabIndex](arkts-arkui-commonmethod-c.md#tabindex-1)联合使用，当某个容器设置了tabIndex，且容器内某子组件或容器自身设置了groupDefaultFocus(true)，当该容器首次TAB键获焦时，会自动将焦点转移至该指定的组件上。若容器内（包含容器本身）有多个组件设置了groupDefaultFocus(true)，则以组件树深度遍历找到的第一个组件为最终结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="height"></a>
## height

```TypeScript
height(value: Length): T
```

设置组件自身的高度，缺省时使用元素自身内容需要的高度。若子组件的高大于父组件的高，则会超出父组件的范围。从API version 10开始，该接口支持calc计算特性。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-height(value: Length): T--><!--Device-CommonMethod-height(value: Length): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 要设置的组件高度。   > **说明：**   >   > 在[Row](Row)、 [Column](Column)、[RelativeContainer](RelativeContainer)组件中，width、height设置auto表示自适应子组件。<br>单位为： vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="height-1"></a>
## height

```TypeScript
height(heightValue: Length | LayoutPolicy): T
```

设置组件自身的高度或垂直方向布局策略，缺省时使用元素自身内容需要的高度。若子组件的高大于父组件的高，则会超出父组件的范围。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-height(heightValue: Length | LayoutPolicy): T--><!--Device-CommonMethod-height(heightValue: Length | LayoutPolicy): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| heightValue | [Length](../arkts-apis/arkts-arkui-length-t.md) \| LayoutPolicy | 是 | 要设置的组件高度。<br>单位为： vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="hittestbehavior"></a>
## hitTestBehavior

```TypeScript
hitTestBehavior(value: HitTestMode): T
```

设置组件的触摸测试类型。如果组件不设置hitTestBehavior，其默认触摸测试类型为HitTestMode.Default。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-hitTestBehavior(value: HitTestMode): T--><!--Device-CommonMethod-hitTestBehavior(value: HitTestMode): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [HitTestMode](../arkts-apis/arkts-arkui-hittestmode-e.md) | 是 | 设置当前组件的触摸测试类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="hovereffect"></a>
## hoverEffect

```TypeScript
hoverEffect(value: HoverEffect): T
```

设置组件的鼠标悬浮态显示效果。当未设置hoverEffect时，组件默认鼠标悬浮态效果为HoverEffect.Auto。对于应用了悬浮态效果的组件，当鼠标悬浮于组件上并按下时，悬浮态效果会消失；当鼠标松开时，悬浮态效果会恢复。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-hoverEffect(value: HoverEffect): T--><!--Device-CommonMethod-hoverEffect(value: HoverEffect): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [HoverEffect](../arkts-apis/arkts-arkui-hovereffect-e.md) | 是 | 设置当前组件悬浮态下的悬浮效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="huerotate"></a>
## hueRotate

```TypeScript
hueRotate(value: number | string): T
```

色相旋转效果。不通过该接口设置时，默认无变化。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-hueRotate(value: number | string): T--><!--Device-CommonMethod-hueRotate(value: number | string): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 色相旋转效果，输入参数为旋转角度。<br/>取值范围：(-∞, +∞)<br/>**说明：**<br/>色调旋转360度会显示原始颜色。先将色调旋转180 度，然后再旋转-180度会显示原始颜色。数据类型为number时，值为90和'90deg'效果一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="huerotate-1"></a>
## hueRotate

```TypeScript
hueRotate(rotation: Optional<number | string>): T
```

色相旋转效果。不通过该接口设置时，默认无变化。与[hueRotate](arkts-arkui-commonmethod-c.md#huerotate-1)相比，rotation参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-hueRotate(rotation: Optional<number | string>): T--><!--Device-CommonMethod-hueRotate(rotation: Optional<number | string>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotation | [Optional](arkts-arkui-optional-t.md)&lt;number \| string&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="id"></a>
## id

```TypeScript
id(value: string): T
```

Id. User can set an id to the component to identify it.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-id(value: string): T--><!--Device-CommonMethod-id(value: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@form@atomicservice |

<a id="ignorelayoutsafearea"></a>
## ignoreLayoutSafeArea

```TypeScript
ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>): T
```

扩展组件布局时的安全区。

> **说明：**  
>  
>忽略布局安全区边缘的组件，如果其宽度或高度设置了 [LayoutPolicy.matchParent](arkts-arkui-layoutpolicy-c.md#matchparent)，其大小和位置都会改变，否则仅改变其位置。  
>  
> 依据safeAreaPadding累积功能，组件可扩展其安全区边缘到所有能感知的连续安全区域。  
>  
> 滚动类组件的子元素忽略布局安全区边缘时在滚动方向不考虑滚动组件自身及其父组件的安全区域，包括：List、ArcListItem、Grid、WaterFlow、Swiper和Tabs。  
>  
> 忽略布局安全区属性.ignoreLayoutSafeArea和忽略渲染安全区属性.expandSafeArea都设置时，.ignoreLayoutSafeArea先生效，.expandSafeArea在前者基础上再生效。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>): T--><!--Device-CommonMethod-ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;LayoutSafeAreaType&gt; | 否 | 扩展布局安全区域的类型。<br/>默认值：[LayoutSafeAreaType.SYSTEM]，扩展至所有安全区域，比如：状态栏，导航栏和组件级安全区（safeAreaPadding）。<br/>非法值：按默认值处理。 |
| edges | Array&lt;LayoutSafeAreaEdge&gt; | 否 | 扩展布局安全区的边缘，并且支持镜像能力。<br />默认值：[LayoutSafeAreaEdge.ALL]，扩展组件所有边缘。<br/>非法值：按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="inspectorlabel"></a>
## inspectorLabel

```TypeScript
inspectorLabel(label: string | undefined): T
```

设置组件的检查器标签，该标签仅在DevEco Studio上显示。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-inspectorLabel(label: string | undefined): T--><!--Device-CommonMethod-inspectorLabel(label: string | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string \| undefined | 是 | 检查器标签。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@atomicservice |

<a id="invert"></a>
## invert

```TypeScript
invert(value: number | InvertOptions): T
```

反转输入的图像。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-invert(value: number | InvertOptions): T--><!--Device-CommonMethod-invert(value: number | InvertOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| InvertOptions | 是 | 反转输入的图像。<br/>入参对象为number时。入参为图像反转的比例，值为1时完全反转，值为0则图像无变化。<br/>取值范围：[0, 1]。<br/>设置小于0的值时，按值为0处理。设置大于1的值时，按值为1处理。<br/>入参对象为 InvertOptions时，对比背景颜色灰度值和阈值区间，背景颜色灰度值小于阈值区间时反色取high值，当背景颜色灰度值大于阈值区间时反色取low值，背景颜色灰度值在阈值区间内取值由high线性渐变到low。<br/>**说明：**<br/>number和InvertOptions两种形式的入参对应不同的反转效果。两种类型的入参切换时，不会清除之前已设置的反转效果，两种反转效果会同时存在，建议始终使用同一种形式的入参。<br>**起始版本：** 7 - 10 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="invert-1"></a>
## invert

```TypeScript
invert(options: Optional<number | InvertOptions>): T
```

反转输入的图像。与[invert](arkts-arkui-commonmethod-c.md#invert-1)相比，options参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-invert(options: Optional<number | InvertOptions>): T--><!--Device-CommonMethod-invert(options: Optional<number | InvertOptions>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;number \| InvertOptions&gt; | 是 | 反转输入的图像。<br/>入参对象为number时。入参为图像反转的比例，值为1时完全反转，值为0则图像无变化。<br/>取值范围：[0, 1]。<br/>设置小于0的值时，按值为0处理。设置大于1的值时，按值为1处理。<br/>入参对象为 InvertOptions时，对比背景颜色灰度值和阈值区间，背景颜色灰度值小于阈值区间时反色取high值，当背景颜色灰度值大于阈值区间时反色取low值，背景颜色灰度值在阈值区间内取值由high线性渐变到low。<br/>当options的值为undefined时，恢复为图像无变化的效果。<br/>**说明：**<br/>number和InvertOptions两种形式的入参对应不同的反转效果。两种类型的入参切换时，不会清除之前已设置的反转效果，两种反转效果会同时存在，建议始终使用同一种形式的入参。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="key"></a>
## key

```TypeScript
key(value: string): T
```

控件标识，开发者可以通过标识来区分不同控件

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-key(value: string): T--><!--Device-CommonMethod-key(value: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="keyboardshortcut"></a>
## keyboardShortcut

```TypeScript
keyboardShortcut(value: string | FunctionKey, keys: Array<ModifierKey>, action?: () => void): T
```

设置组件的自定义组合键。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-keyboardShortcut(value: string | FunctionKey, keys: Array<ModifierKey>, action?: () => void): T--><!--Device-CommonMethod-keyboardShortcut(value: string | FunctionKey, keys: Array<ModifierKey>, action?: () => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| FunctionKey | 是 | 热键的单个字符（可以通过键盘输入的字符）或[FunctionKey](../arkts-apis/arkts-arkui-functionkey-e.md)。<br />空字符串意为取消快捷键绑定。<br/> |
| keys | Array&lt;ModifierKey&gt; | 是 | 热键组合。<br />仅当value为[FunctionKey](../arkts-apis/arkts-arkui-functionkey-e.md)的情况下keys的值可以为空。<br/> |
| action | () =&gt; void | 否 | 组合快捷键触发成功后的自定义事件回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="layoutgravity"></a>
## layoutGravity

```TypeScript
layoutGravity(alignment: LocalizedAlignment): T
```

单独设置Stack组件中子组件的对齐规则，仅当父组件为Stack时生效。与align属性同时使用时，layoutGravity优先级更高，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-layoutGravity(alignment: LocalizedAlignment): T--><!--Device-CommonMethod-layoutGravity(alignment: LocalizedAlignment): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignment | [LocalizedAlignment](../arkts-apis/arkts-arkui-localizedalignment-e.md) | 是 | 指定设置在Stack组件中子组件的对齐规则。<br/>默认值：LocalizedAlignment.CENTER。说明：当传入异常值时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="layoutweight"></a>
## layoutWeight

```TypeScript
layoutWeight(value: number | string): T
```

设置组件的布局权重，使组件在父容器（[Row](Row)/[Column](Column)/[Flex](Flex)的主轴方向按照权重分配尺寸。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-layoutWeight(value: number | string): T--><!--Device-CommonMethod-layoutWeight(value: number | string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 组件的布局权重。<br>父容器尺寸确定时，不设置layoutWeight属性或者layoutWeight属性生效值为0的元素优先占位，这些元素占位后在主轴留下的空间称为主轴剩余空间。设置了layoutWeight属性且layoutWeig ht属性生效值大于0的子元素会从主轴剩余空间中按照各自所设置的权重占比分配尺寸，分配时会忽略元素本身的尺寸设置。<br/>默认值：0<br/>**说明：** <br/>仅在[Row](Row)/[Column](Column)/[Flex](Flex)布局中生效。<br/>可选值为大于等于0的数字，或者可以转换为数字的字符串。<br/>如果容器中有子元素设置了layoutWeight属性，且设置的属性值大于0，则所有子元素不会再基于[flexShrink](arkts-arkui-commonmethod-c.md#flexshrink-1)和[flexGrow](arkts-arkui-commonmethod-c.md#flexgrow-1)布局。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="lightupeffect"></a>
## lightUpEffect

```TypeScript
lightUpEffect(value: number): T
```

设置组件图像亮起程度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-lightUpEffect(value: number): T--><!--Device-CommonMethod-lightUpEffect(value: number): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置组件图像亮起程度。<br/>取值范围：[0,1]。<br/>如果value等于0则图像为全黑，如果value等于1则图像为全亮效果。0到1之间数值越大，表示图像亮度越高。`value < 0` 或者 `value > 1`为异常情况，`value < 0`按0处理，`value > 1`按1处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="lightupeffect-1"></a>
## lightUpEffect

```TypeScript
lightUpEffect(degree: Optional<number>): T
```

设置组件图像亮起程度。与[lightUpEffect<sup>12+</sup>](arkts-arkui-commonmethod-c.md#lightupeffect-1)相比，degree参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-lightUpEffect(degree: Optional<number>): T--><!--Device-CommonMethod-lightUpEffect(degree: Optional<number>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| degree | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 设置组件图像亮起程度。<br/>取值范围：[0,1]。<br/>如果value等于0则图像为全黑，如果value等于1则图像为全亮效果。0到1之间数值越大，表示图像亮度越高。`degree < 0` 或者 `degree > 1`为异常情况，`degree < 0`按0处理，`degree > 1`按1处理。<br/>当degree的值为undefined时，恢复为亮起为1的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="lineargradient"></a>
## linearGradient

```TypeScript
linearGradient(value: LinearGradientOptions): T
```

线性渐变。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-linearGradient(value: LinearGradientOptions): T--><!--Device-CommonMethod-linearGradient(value: LinearGradientOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LinearGradientOptions](arkts-arkui-lineargradientoptions-i.md) | 是 | 线性渐变。<br>**起始版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="lineargradient-1"></a>
## linearGradient

```TypeScript
linearGradient(options: Optional<LinearGradientOptions>): T
```

线性渐变。与[linearGradient](arkts-arkui-commonmethod-c.md#lineargradient-1)相比，options参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-linearGradient(options: Optional<LinearGradientOptions>): T--><!--Device-CommonMethod-linearGradient(options: Optional<LinearGradientOptions>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;LinearGradientOptions&gt; | 是 | 线性渐变。<br/>当options的值为undefined时，恢复为无线性渐变的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="lineargradientblur"></a>
## linearGradientBlur

```TypeScript
linearGradientBlur(value: number, options: LinearGradientBlurOptions): T
```

为组件添加内容线性渐变模糊效果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-linearGradientBlur(value: number, options: LinearGradientBlurOptions): T--><!--Device-CommonMethod-linearGradientBlur(value: number, options: LinearGradientBlurOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 为模糊半径，模糊半径越大越模糊，为0时不模糊。<br/>取值范围：[0, 1000] |
| options | [LinearGradientBlurOptions](arkts-arkui-lineargradientbluroptions-i.md) | 是 | 设置线性渐变模糊效果。 <br/>线性渐变参数，包含模糊程度和模糊位置数组fractionStops，及渐变模糊方向direction。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@atomicservice |

<a id="lineargradientblur-1"></a>
## linearGradientBlur

```TypeScript
linearGradientBlur(blurRadius: Optional<number>, options: Optional<LinearGradientBlurOptions>): T
```

为组件添加内容线性渐变模糊效果。与[linearGradientBlur<sup>12+</sup>](arkts-arkui-commonmethod-c.md#lineargradientblur-1)相比，新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-linearGradientBlur(blurRadius: Optional<number>, options: Optional<LinearGradientBlurOptions>): T--><!--Device-CommonMethod-linearGradientBlur(blurRadius: Optional<number>, options: Optional<LinearGradientBlurOptions>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurRadius | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 为模糊半径，模糊半径越大越模糊，为0时不模糊。<br/>取值范围：[0, 1000]<br/>当blurRadius的值为undefined时，恢复为渐变模糊为0的效果。 |
| options | [Optional](arkts-arkui-optional-t.md)&lt;LinearGradientBlurOptions&gt; | 是 | 设置线性渐变模糊效果。<br/>线性渐变参数，包含模糊程度和模糊位置数组fractionStops，及渐变模糊方向direction。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@atomicservice |

<a id="margin"></a>
## margin

```TypeScript
margin(value: Margin | Length | LocalizedMargin): T
```

设置组件的外边距属性。在计算位置时外边距视为组件大小的一部分，从而影响组件位置。

从API version 10开始，该接口支持calc计算特性。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-margin(value: Margin | Length | LocalizedMargin): T--><!--Device-CommonMethod-margin(value: Margin | Length | LocalizedMargin): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Margin](../arkts-apis/arkts-arkui-margin-t.md) \| Length \| LocalizedMargin | 是 | Margin of the component to set.<br>When the parameter is of the **Length** type, the four margins take effect.<br>Default value: **0**<br>Unit: vp<br>When **margin** is set to a percentage, the width of the parent container is used as the basic value. When child components are laid out along the cross axis of the [Row](Row), [Column](Column), or [Flex](Flex) container, the cross axis size of the child components and the margins add up to the total size of the container.<br>For example, if the width of the **Column** container is 100, the width of the child component is 50, the left margin is 10, and the right margin is 20, then the actual horizontal offset of the child component is 10.<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="markanchor"></a>
## markAnchor

```TypeScript
markAnchor(value: Position | LocalizedPosition): T
```

设置元素在位置定位时的锚点，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-markAnchor(value: Position | LocalizedPosition): T--><!--Device-CommonMethod-markAnchor(value: Position | LocalizedPosition): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Position](../arkts-apis/arkts-arkui-display-position-i.md) \| LocalizedPosition | 是 | Positioning anchor that offsets an element from the position specified by [position](arkts-arkui-commonmethod-c.md#position-1) or [offset](arkts-arkui-commonmethod-c.md#offset-1)**.position({x: value1, y: value2}).markAnchor({x: value3, y: value4})** has the same effect as **.position({x: value1 - value3, y: value2 - value4})**. The same applies to **offset**.<br>If **.markAnchor({x: value1, y: value2})** is set separately, the effect is the same as that of **.offset({x: -value1, y: -value2})**.<br>API version 9 and earlier: The default value is **{x: 0, y: 0}**.<br>API version 10: no default value.<br>This attribute does not take effect when it is set to an abnormal value.<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="mask"></a>
## mask

```TypeScript
mask(value: ProgressMask): T
```

为组件上添加可调节进度的遮罩。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-mask(value: ProgressMask): T--><!--Device-CommonMethod-mask(value: ProgressMask): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ProgressMask](arkts-arkui-progressmask-c.md) | 是 | 在当前组件上加上可动态设置进度、最大值和颜色的遮罩。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="mask-1"></a>
## mask

```TypeScript
mask(mask: Optional<ProgressMask>): T
```

为组件上添加可调节进度的遮罩。与[mask<sup>12+</sup>](arkts-arkui-commonmethod-c.md#mask-1)相比，新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-mask(mask: Optional<ProgressMask>): T--><!--Device-CommonMethod-mask(mask: Optional<ProgressMask>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mask | [Optional](arkts-arkui-optional-t.md)&lt;ProgressMask&gt; | 是 | 在当前组件上加上可动态设置进度、最大值和颜色的遮罩。<br/>当mask的值为undefined时，恢复为无进度遮罩效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="mask-2"></a>
## mask

```TypeScript
mask(value: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute | ProgressMask): T
```

为组件上添加指定形状的遮罩。

> **说明：**

**起始版本：** 7

**废弃版本：** 12

**替代接口：** [maskShape(value:](arkts-arkui-commonmethod-c.md#maskshape-1)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-mask(value: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute | ProgressMask): T--><!--Device-CommonMethod-mask(value: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute | ProgressMask): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CircleAttribute](arkts-arkui-circle-attribute.md) \| EllipseAttribute \| PathAttribute \| RectAttribute \| ProgressMask | 是 | 在当前组件上加上指定形状的遮罩。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="maskshape"></a>
## maskShape

```TypeScript
maskShape(value: CircleShape | EllipseShape | PathShape | RectShape): T
```

为组件上添加指定形状的遮罩。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-maskShape(value: CircleShape | EllipseShape | PathShape | RectShape): T--><!--Device-CommonMethod-maskShape(value: CircleShape | EllipseShape | PathShape | RectShape): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CircleShape](arkts-arkui-circleshape-t.md) \| EllipseShape \| PathShape \| RectShape | 是 | 在当前组件上加上指定形状的遮罩。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="maskshape-1"></a>
## maskShape

```TypeScript
maskShape(shape: Optional<CircleShape | EllipseShape | PathShape | RectShape>): T
```

为组件上添加指定形状的遮罩。与[maskShape<sup>12+</sup>](arkts-arkui-commonmethod-c.md#maskshape-1)相比，新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-maskShape(shape: Optional<CircleShape | EllipseShape | PathShape | RectShape>): T--><!--Device-CommonMethod-maskShape(shape: Optional<CircleShape | EllipseShape | PathShape | RectShape>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shape | [Optional](arkts-arkui-optional-t.md)&lt;CircleShape \| EllipseShape \| PathShape \| RectShape&gt; | 是 | 在当前组件上加上指定形状的遮罩。<br/>当shape的值为undefined时，会重置当前值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="materialfilter"></a>
## materialFilter

```TypeScript
materialFilter(filter: Filter | undefined): T
```

设置系统材质滤镜效果，系统材质滤镜的绘制早于[backgroundFilter](arkts-arkui-commonmethod-c.md#backgroundfilter-1)绘制，即位于backgroundFilter的更底层。

> **说明：**  
>  
> 该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-materialFilter(filter: Filter | undefined): T--><!--Device-CommonMethod-materialFilter(filter: Filter | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) \| undefined | 是 | 系统材质滤镜视觉效果。设置为undefined时恢复为无系统材质滤镜效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="monopolizeevents"></a>
## monopolizeEvents

```TypeScript
monopolizeEvents(monopolize: boolean): T
```

设置组件是否独占事件。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-monopolizeEvents(monopolize: boolean): T--><!--Device-CommonMethod-monopolizeEvents(monopolize: boolean): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| monopolize | boolean | 是 | 组件是否独占事件。true表示组件独占事件，false表示组件不独占事件。默认值：false说明：1、如果第一根手指触发了组件事件独占，在抬起前又按下了一根手指，则第二根手指的交互继续处于组件独占状态，依次类推。2、如果开发者通过[parallelGesture](arkts-arkui-commonmethod-c.md#parallelgesture-1)绑定了与子组件同时触发的手势，如PanGesture，子组件设置了独占控制且首个响应事件，则父组件的手势不会响应。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="motionblur"></a>
## motionBlur

```TypeScript
motionBlur(value: MotionBlurOptions):T
```

在当前组件由缩放大小或位移变化引起的运动过程中，增加动态模糊效果。

> **说明：**  
>  
> - 不建议在组件内转场、共享元素转场、组件内隐式元素转场和粒子动画场景中使用该属性，否则会产生非预期效果。  
>  
> - 该属性需要在开始状态将motionBlur的参数radius设置为0，否则冷启动时会有非预期效果。  
>  
> - 该属性需要与动画的AnimateParam的onFinish参数配合使用，需要在运动模糊动画结束后将motionBlur的参数radius置为0，否则会产生非预期效果。  
>  
> - 在使用该属性过程中，不要在使用过程中频繁更改同一个组件的模糊半径，否则会产生非预期效果。比如示例中的动画，频繁点击会出现模糊效果偶尔失效的情况。  
>  
> - 运动模糊锚点坐标需要与动画缩放的锚点保持一致，否则会产生非预期效果。  
>  
> - 模糊半径建议设置1以内，否则会产生非预期效果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-motionBlur(value: MotionBlurOptions):T--><!--Device-CommonMethod-motionBlur(value: MotionBlurOptions):T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [MotionBlurOptions](arkts-arkui-motionbluroptions-i.md) | 是 | 定义运动模糊参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="motionblur-1"></a>
## motionBlur

```TypeScript
motionBlur(motionBlur: Optional<MotionBlurOptions>):T
```

在当前组件由缩放大小或位移变化引起的运动过程中，增加动态模糊效果。与[motionBlur](arkts-arkui-commonmethod-c.md#motionblur-1)相比，motionBlur参数新增了对undefined类型的支持。

1、不建议在组件内转场、共享元素转场、组件内隐式元素转场、粒子动画场景下使用该属性，否则会产生非预期效果。

2、该属性需要在开始状态将motionBlur的参数radius设置为0，否则冷启动时会有非预期效果。

3、该属性需要与动画的AnimateParam的onFinish参数配合使用，需要在运动模糊动画结束后将motionBlur的参数radius置为0，否则会产生非预期效果。

4、在使用该属性过程中，不要在使用过程中频繁更改同一个组件的模糊半径，否则会产生非预期效果。比如示例中的动画，频繁点击会出现模糊效果偶尔失效的情况。

5、运动模糊锚点坐标需要与动画缩放的锚点保持一致，否则会产生非预期效果。

6、模糊半径建议设置1以内，否则会产生非预期效果。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-motionBlur(motionBlur: Optional<MotionBlurOptions>):T--><!--Device-CommonMethod-motionBlur(motionBlur: Optional<MotionBlurOptions>):T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| motionBlur | [Optional](arkts-arkui-optional-t.md)&lt;MotionBlurOptions&gt; | 是 | 定义运动模糊参数。<br/>当motionBlur的值为undefined时，维持之前取值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="motionpath"></a>
## motionPath

```TypeScript
motionPath(value: MotionPathOptions): T
```

设置组件的路径动画。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-motionPath(value: MotionPathOptions): T--><!--Device-CommonMethod-motionPath(value: MotionPathOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [MotionPathOptions](arkts-arkui-motionpathoptions-i.md) | 是 | 设置组件的运动路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="mouseresponseregion"></a>
## mouseResponseRegion

```TypeScript
mouseResponseRegion(value: Array<Rectangle> | Rectangle): T
```

设置一个或多个鼠标触摸热区。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-mouseResponseRegion(value: Array<Rectangle> | Rectangle): T--><!--Device-CommonMethod-mouseResponseRegion(value: Array<Rectangle> | Rectangle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;Rectangle&gt; \| Rectangle | 是 | 鼠标触摸热区，包括位置和大小。<br/>默认触摸热区为整个组件，默认值：<br/>{<br/>x：0,<br/>y：0,<br/>width：'100%',<br/>height：'100%'<br/>} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="nextfocus"></a>
## nextFocus

```TypeScript
nextFocus(nextStep: Optional<FocusMovement>): T
```

设置组件的自定义焦点走焦逻辑。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-nextFocus(nextStep: Optional<FocusMovement>): T--><!--Device-CommonMethod-nextFocus(nextStep: Optional<FocusMovement>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| nextStep | [Optional](arkts-arkui-optional-t.md)&lt;FocusMovement&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="obscured"></a>
## obscured

```TypeScript
obscured(reasons: Array<ObscuredReasons>): T
```

Sets obscured

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-obscured(reasons: Array<ObscuredReasons>): T--><!--Device-CommonMethod-obscured(reasons: Array<ObscuredReasons>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reasons | Array&lt;ObscuredReasons&gt; | 是 | reasons of obscuration |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="offset"></a>
## offset

```TypeScript
offset(value: Position | Edges | LocalizedEdges): T
```

相对偏移，组件相对原本的布局位置进行偏移。和position一起使用时，position生效，offset不生效，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-offset(value: Position | Edges | LocalizedEdges): T--><!--Device-CommonMethod-offset(value: Position | Edges | LocalizedEdges): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Position](../arkts-apis/arkts-arkui-display-position-i.md) \| Edges \| LocalizedEdges | 是 | Offset of the component relative to its original layout position. The **offset** attribute does not affect the layout of the parent container. It adjusts the component position only during drawing.If of the [Position](../arkts-apis/arkts-arkui-position-t.md) type, this parameter sets the offset relative to the upper left corner of the component. If of the [Edges](../arkts-apis/arkts-arkui-graphics-edges-i.md) type, this parameter sets the offset relative to the four edges of the component. **{x: x, y: y}** has the same effect as **{left: x, top: y}** and **{right: -x, bottom: -y}**. The [LocalizedEdges](../arkts-apis/arkts-arkui-localizededges-i.md) type supports the mirror mode:**start** is equivalent to **x** with left-to-right scripts and **-x** with right-to-left scripts.<br>API version 9 and earlier: The default value is **{x: 0, y: 0}**.<br>Default unit: vp<br>API version 10: no default value.<br>This attribute does not take effect when it is set to an abnormal value.<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="onaccessibilityactionintercept"></a>
## onAccessibilityActionIntercept

```TypeScript
onAccessibilityActionIntercept(callback: AccessibilityActionInterceptCallback): T
```

注册可访问性操作拦截回调，当要执行可访问性操作时，将执行回调

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-onAccessibilityActionIntercept(callback: AccessibilityActionInterceptCallback): T--><!--Device-CommonMethod-onAccessibilityActionIntercept(callback: AccessibilityActionInterceptCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AccessibilityActionInterceptCallback](arkts-arkui-accessibilityactioninterceptcallback-t.md) | 是 | 可访问性操作拦截回调函数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="onaccessibilityfocus"></a>
## onAccessibilityFocus

```TypeScript
onAccessibilityFocus(callback: AccessibilityFocusCallback): T
```

Register accessibility focus callback,when the component is focused or out of focus,the callback will be executed

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-onAccessibilityFocus(callback: AccessibilityFocusCallback): T--><!--Device-CommonMethod-onAccessibilityFocus(callback: AccessibilityFocusCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AccessibilityFocusCallback](arkts-arkui-accessibilityfocuscallback-t.md) | 是 | accessibility focus callback function |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

<a id="onaccessibilityhover"></a>
## onAccessibilityHover

```TypeScript
onAccessibilityHover(callback: AccessibilityCallback): T
```

Trigger a accessibility hover event.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onAccessibilityHover(callback: AccessibilityCallback): T--><!--Device-CommonMethod-onAccessibilityHover(callback: AccessibilityCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AccessibilityCallback](arkts-arkui-accessibilitycallback-t.md) | 是 | A callback instance used when the component is touched after accessibility mode is enabled. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="onaccessibilityhovertransparent"></a>
## onAccessibilityHoverTransparent

```TypeScript
onAccessibilityHoverTransparent(callback: AccessibilityTransparentCallback): T
```

prompt for current component and descendants unable to handle accessibility hover event

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onAccessibilityHoverTransparent(callback: AccessibilityTransparentCallback): T--><!--Device-CommonMethod-onAccessibilityHoverTransparent(callback: AccessibilityTransparentCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AccessibilityTransparentCallback](arkts-arkui-accessibilitytransparentcallback-t.md) | 是 | A callback instance used when current component and descendants not handled accessibility hover event |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="onappear"></a>
## onAppear

```TypeScript
onAppear(event: () => void): T
```

组件挂载后触发此回调。

> **说明：**  
>  
> 回调的调用时机有可能发生在组件布局渲染后。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-onAppear(event: () => void): T--><!--Device-CommonMethod-onAppear(event: () => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | onAppear事件的回调函数，表示组件已挂载显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onareachange"></a>
## onAreaChange

```TypeScript
onAreaChange(event: (oldValue: Area, newValue: Area) => void): T
```

组件区域变化时触发该回调。仅会响应由布局变化所导致的组件大小、位置发生变化时的回调。

由绘制变化所导致的渲染属性变化不会响应回调，如[translate](arkts-arkui-commonmethod-c.md#translate-1)、[offset](arkts-arkui-commonmethod-c.md#offset-1)、[markAnchor](arkts-arkui-commonmethod-c.md#markanchor-1)、[scale](arkts-arkui-commonmethod-c.md#scale-1)、[transform](arkts-arkui-commonmethod-c.md#transform-1)。若组件自身位置由绘制变化决定也不会响应回调，如[bindSheet](arkts-arkui-commonmethod-c.md#bindsheet-1)。

> **说明：**  
>  
> 当组件同时绑定onAreaChange事件和[position](arkts-arkui-commonmethod-c.md#position-1)属性时，onAreaChange事件响应设置  
> [Position](../arkts-apis/arkts-arkui-position-t.md)类型的position属性变化，不响应设置[Edges](../arkts-apis/arkts-arkui-graphics-edges-i.md)和[LocalizedEdges](../arkts-apis/arkts-arkui-localizededges-i.md)  
> 类型的position属性变化。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onAreaChange(event: (oldValue: Area, newValue: Area) => void): T--><!--Device-CommonMethod-onAreaChange(event: (oldValue: Area, newValue: Area) => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (oldValue: Area, newValue: Area) =&gt; void | 是 | 返回目标元素位置信息变化情况，oldValue为目标元素变化之前的宽高以及目标元素相对父元素和页面左上角的坐标位置。newValue为目标元素变化之后的宽高以及目标元素相对父元素和页面左上角的坐标位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onareachange-1"></a>
## onAreaChange

```TypeScript
onAreaChange(event: AreaChangeCallback, options?: AreaChangeOptions): T
```

组件区域变化时触发该回调，可通过[AreaChangeOptions](arkts-arkui-areachangeoptions-i.md)中的expectedUpdateInterval设置触发回调的间隔。仅会响应由布局变化所导致的组件大小、位置发生变化时的回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onAreaChange(event: AreaChangeCallback, options?: AreaChangeOptions): T--><!--Device-CommonMethod-onAreaChange(event: AreaChangeCallback, options?: AreaChangeOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [AreaChangeCallback](arkts-arkui-areachangecallback-t.md) | 是 | onAreaChange事件的回调函数。组件显示的尺寸、位置发生变化时触发该回调。 |
| options | [AreaChangeOptions](arkts-arkui-areachangeoptions-i.md) | 否 | 区域变化相关的参数。缺省时，expectedUpdateInterval时间间隔按照0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onattach"></a>
## onAttach

```TypeScript
onAttach(callback: Callback<void>): T
```

组件挂载到组件树时触发此回调。由于以下说明中的限制，建议使用[onAppear](arkts-arkui-commonmethod-c.md#onappear-1)替代此接口。

> **说明：**  
>  
> - 回调在组件布局渲染前调用。  
>  
> - 不允许在回调中对组件树进行变更，例如启动动画或使用if-else变更组件树结构。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onAttach(callback: Callback<void>): T--><!--Device-CommonMethod-onAttach(callback: Callback<void>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | onAttach事件的回调函数，表示组件已经挂载至组件树。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onaxisevent"></a>
## onAxisEvent

```TypeScript
onAxisEvent(event: Callback<AxisEvent>): T
```

鼠标滚轮滚动或触控板双指轻触滑动、双指捏合时触发该回调。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onAxisEvent(event: Callback<AxisEvent>): T--><!--Device-CommonMethod-onAxisEvent(event: Callback<AxisEvent>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;AxisEvent&gt; | 是 | 获得[AxisEvent](arkts-arkui-axisevent-i.md)对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onblur"></a>
## onBlur

```TypeScript
onBlur(event: () => void): T
```

当前组件失去焦点时触发的回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onBlur(event: () => void): T--><!--Device-CommonMethod-onBlur(event: () => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | onBlur的回调函数，表示组件已失焦。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onchildtouchtest"></a>
## onChildTouchTest

```TypeScript
onChildTouchTest(event: (value: Array<TouchTestInfo>) => TouchResult): T
```

当前组件通过设置回调，可自定义触摸测试并控制触摸测试中的子节点行为。

> **说明：**  
>  
> - 子节点信息数组中仅包含命名节点的信息，即开发者通过id属性设置了id的节点。  
>  
> - 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onChildTouchTest(event: (value: Array<TouchTestInfo>) => TouchResult): T--><!--Device-CommonMethod-onChildTouchTest(event: (value: Array<TouchTestInfo>) => TouchResult): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (value: Array&lt;TouchTestInfo&gt;) =&gt; TouchResult | 是 | 触摸事件信息。value的值为包含子节点信息的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onclick"></a>
## onClick

```TypeScript
onClick(event: (event: ClickEvent) => void): T
```

点击动作触发该回调。

触发点击事件的设备类型为键盘或手柄时，事件的SourceTool值为Unknown，事件的[SourceType](arkts-arkui-sourcetype-e.md)值为KEY，JOYSTICK。

> **说明：**  
>  
> 从API version 9开始，使用卡片能力时存在以下限制：  
>  
> 1. 如果手指按下的持续时间超过800ms，不能触发点击事件。  
>  
> 2. 如果手指按下后移动位移超过20px，不能触发点击事件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-onClick(event: (event: ClickEvent) => void): T--><!--Device-CommonMethod-onClick(event: (event: ClickEvent) => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: ClickEvent) =&gt; void | 是 | 点击事件的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onclick-1"></a>
## onClick

```TypeScript
onClick(event: Callback<ClickEvent>, distanceThreshold: number): T
```

点击动作触发该回调。

当触发点击事件的设备类型为键盘或手柄时，事件的[SourceTool](arkts-arkui-sourcetool-e.md)值为Unknown，事件的[SourceType](arkts-arkui-sourcetype-e.md)值为KEY或JOYSTICK。

新增distanceThreshold参数，设置点击手势移动阈值。手指移动超出阈值时，点击手势识别失败。

对于无手指移动距离限制的点击场景，建议使用原有接口。若需限制点击时手指移动范围，建议使用该接口。

> **说明：**  
>  
> - 从API version 12开始，在使用卡片能力时，存在以下限制：  
> > 1. 如果手指按下的持续时间超过800ms，不能触发点击事件。  
> > 2. 如果手指按下后移动位移超过20px，不能触发点击事件。  
>  
> - 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-onClick(event: Callback<ClickEvent>, distanceThreshold: number): T--><!--Device-CommonMethod-onClick(event: Callback<ClickEvent>, distanceThreshold: number): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ClickEvent&gt; | 是 | 点击事件的回调函数。 |
| distanceThreshold | number | 是 | 点击事件移动阈值。当设置的值小于等于0时，会被转化为默认值。<br/>默认值：2^31-1<br/>单位：vp<br/>**说明：**<br/>当手指的移动距离超出开发者预设的移动阈值时，点击识别失败。如果初始化为默认阈值时，手指移动超过组件热区范围，点击识别失败。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ondetach"></a>
## onDetach

```TypeScript
onDetach(callback: Callback<void>): T
```

组件从组件树卸载时触发此回调。建议使用[onDisAppear](arkts-arkui-commonmethod-c.md#ondisappear-1)替代此接口。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onDetach(callback: Callback<void>): T--><!--Device-CommonMethod-onDetach(callback: Callback<void>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | onDetach事件的回调函数，表示组件已经从组件树卸载。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ondigitalcrown"></a>
## onDigitalCrown

```TypeScript
onDigitalCrown(handler: Optional<Callback<CrownEvent>>): T
```

组件获焦以后旋转表冠时触发该回调。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onDigitalCrown(handler: Optional<Callback<CrownEvent>>): T--><!--Device-CommonMethod-onDigitalCrown(handler: Optional<Callback<CrownEvent>>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-optional-t.md)&lt;Callback&lt;CrownEvent&gt;&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ondisappear"></a>
## onDisAppear

```TypeScript
onDisAppear(event: () => void): T
```

组件从组件树卸载时触发此回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-onDisAppear(event: () => void): T--><!--Device-CommonMethod-onDisAppear(event: () => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | onDisAppear事件的回调函数，表示组件已卸载消失。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ondragend"></a>
## onDragEnd

```TypeScript
onDragEnd(event: (event: DragEvent, extraParams?: string) => void): T
```

绑定此事件的组件触发的拖拽结束后，触发回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onDragEnd(event: (event: DragEvent, extraParams?: string) => void): T--><!--Device-CommonMethod-onDragEnd(event: (event: DragEvent, extraParams?: string) => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: DragEvent, extraParams?: string) =&gt; void | 是 | 回调函数。<br/>**说明：**<br/> event为拖拽事件信息，在onDragEnd调用中不包括拖拽点坐标。<br/> extraParams为拖拽事件额外信息，需要解析为JSON格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ondragenter"></a>
## onDragEnter

```TypeScript
onDragEnter(event: (event: DragEvent, extraParams?: string) => void): T
```

拖拽进入组件范围内时，触发回调，当监听了[onDrop](arkts-arkui-commonmethod-c.md#ondrop-1)事件时，此事件才有效。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onDragEnter(event: (event: DragEvent, extraParams?: string) => void): T--><!--Device-CommonMethod-onDragEnter(event: (event: DragEvent, extraParams?: string) => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: DragEvent, extraParams?: string) =&gt; void | 是 | 回调函数。<br/>**说明：**<br/> event为拖拽事件信息，包括拖拽点坐标。<br/> extraParams为拖拽事件额外信息，需要解析为JSON格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ondragleave"></a>
## onDragLeave

```TypeScript
onDragLeave(event: (event: DragEvent, extraParams?: string) => void): T
```

拖拽离开组件范围内时，触发回调，当监听了[onDrop](arkts-arkui-commonmethod-c.md#ondrop-1)事件时，此事件才有效。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onDragLeave(event: (event: DragEvent, extraParams?: string) => void): T--><!--Device-CommonMethod-onDragLeave(event: (event: DragEvent, extraParams?: string) => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: DragEvent, extraParams?: string) =&gt; void | 是 | 回调函数。<br/>**说明：**<br/> event为拖拽事件信息，包括拖拽点坐标。<br/> extraParams为拖拽事件额外信息，需要解析为JSON格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ondragmove"></a>
## onDragMove

```TypeScript
onDragMove(event: (event: DragEvent, extraParams?: string) => void): T
```

拖拽在组件范围内移动时，触发回调，当监听了[onDrop](arkts-arkui-commonmethod-c.md#ondrop-1)事件时，此事件才有效。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onDragMove(event: (event: DragEvent, extraParams?: string) => void): T--><!--Device-CommonMethod-onDragMove(event: (event: DragEvent, extraParams?: string) => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: DragEvent, extraParams?: string) =&gt; void | 是 | 回调函数。<br/>**说明：**<br/> event为拖拽事件信息，包括拖拽点坐标。<br/> extraParams为拖拽事件额外信息，需要解析为JSON格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ondragspringloading"></a>
## onDragSpringLoading

```TypeScript
onDragSpringLoading(callback: Callback<SpringLoadingContext> | null, configuration?: DragSpringLoadingConfiguration): T
```

绑定此事件的组件可作为具有悬停检测功能的拖拽响应目标。当拖拽对象悬停在目标上时，触发回调通知。此时只有一个目标可以成为响应方，并且子组件始终具有更高的响应优先级。

关于悬停检测的触发机制及详细使用方法，请参考开发指南[支持悬停检测](docroot://ui/arkts-common-events-drag-event.md#支持悬停检测)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onDragSpringLoading(callback: Callback<SpringLoadingContext> | null, configuration?: DragSpringLoadingConfiguration): T--><!--Device-CommonMethod-onDragSpringLoading(callback: Callback<SpringLoadingContext> | null, configuration?: DragSpringLoadingConfiguration): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;SpringLoadingContext&gt; \| null | 是 | 悬停检测回调函数，当值为null时禁用悬停检测。 |
| configuration | [DragSpringLoadingConfiguration](arkts-arkui-dragspringloadingconfiguration-t.md) | 否 | 悬停检测配置信息，为undefined时取[DragSpringLoadingConfiguration](../arkts-apis/arkts-arkui-dragcontroller-dragspringloadingconfiguration-i.md)默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ondragstart"></a>
## onDragStart

```TypeScript
onDragStart(event: (event: DragEvent, extraParams?: string) => CustomBuilder | DragItemInfo): T
```

在手势拖拽场景中，在可拖拽的组件上长按时间超过500ms，然后手指移动距离大于10vp时触发此回调；在鼠标拖拽场景中，鼠标左键在可拖拽的组件上按下并移动超过1vp时，即可触发此回调。

针对默认支持拖拽能力的组件，如果开发者设置了onDragStart，优先执行onDragStart，并根据执行情况决定是否使用系统默认的拖拽能力，具体规则为：

- 如果开发者返回了自定义预览图，则不再使用系统默认的拖拽预览图；  
- 如果开发者设置了拖拽数据，则不再使用系统默认填充的拖拽数据。

文本类组件[Text](../../apis-arkgraphics2d/arkts-apis/arkts-graphics-text.md)、[Search](arkts-arkui-search.md)、[TextInput](arkts-arkui-textinput.md)、[TextArea](arkts-arkui-textarea.md)、[RichEditor](arkts-arkui-richeditor.md)对选中的文本内容进行拖拽时，不支持自定义预览图。当onDragStart与菜单预览一起使用或使用了默认支持拖拽能力的组件时，预览及菜单项上的自定义内容不支持拖拽。

> **说明：**  
>  
> 从API version 13开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onDragStart(event: (event: DragEvent, extraParams?: string) => CustomBuilder | DragItemInfo): T--><!--Device-CommonMethod-onDragStart(event: (event: DragEvent, extraParams?: string) => CustomBuilder | DragItemInfo): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: DragEvent, extraParams?: string) =&gt; CustomBuilder \| DragItemInfo | 是 | 回调函数。<br/> **说明：**<br/> event参数为拖拽事件的信息。<br/> extraParams参数为拖拽事件的额外信息，需要解析为JSON格式。<br/>CustomBuilder为拖拽过程中显示的组件信息，不支持全局builder。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ondrop"></a>
## onDrop

```TypeScript
onDrop(event: (event: DragEvent, extraParams?: string) => void): T
```

绑定此事件的组件可作为释放目标。当在本组件范围内停止拖放行为时，将触发回调。如果开发者未在onDrop中主动调用event.setResult()来设置拖拽接收的结果，对于系统支持的默认可拖入组件，处理结果将以系统实际处理的数据为准。对于其他组件，系统将默认视为数据接收成功。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onDrop(event: (event: DragEvent, extraParams?: string) => void): T--><!--Device-CommonMethod-onDrop(event: (event: DragEvent, extraParams?: string) => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: DragEvent, extraParams?: string) =&gt; void | 是 | 回调函数。<br/>**说明：**<br/> event为拖拽事件信息，包括拖拽点坐标。<br/> extraParams为拖拽事件额外信息，需要解析为JSON格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ondrop-1"></a>
## onDrop

```TypeScript
onDrop(eventCallback: OnDragEventCallback, dropOptions?: DropOptions): T
```

绑定此事件的组件可作为拖拽释放目标，当在本组件范围内停止拖拽行为时，触发回调。如果开发者没有在onDrop中主动调用event.[setResult](arkts-arkui-dragevent-i.md#setresult-1)()设置拖拽接收的结果，若拖拽组件为系统支持默认拖入的组件，以系统实际处理数据结果为准，其它组件则系统按照数据接收成功处理。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onDrop(eventCallback: OnDragEventCallback, dropOptions?: DropOptions): T--><!--Device-CommonMethod-onDrop(eventCallback: OnDragEventCallback, dropOptions?: DropOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventCallback | [OnDragEventCallback](arkts-arkui-ondrageventcallback-t.md) | 是 | 回调函数。 |
| dropOptions | [DropOptions](arkts-arkui-dropoptions-i.md) | 否 | 落入过程的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onfocus"></a>
## onFocus

```TypeScript
onFocus(event: () => void): T
```

当前组件获取焦点时触发的回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onFocus(event: () => void): T--><!--Device-CommonMethod-onFocus(event: () => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | onFocus的回调函数，表示组件已获焦。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onfocusaxisevent"></a>
## onFocusAxisEvent

```TypeScript
onFocusAxisEvent(event: Callback<FocusAxisEvent>): T
```

给组件绑定焦点轴事件回调。绑定该方法的组件获焦后，游戏手柄上的摇杆、十字键等的操作会触发该回调。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onFocusAxisEvent(event: Callback<FocusAxisEvent>): T--><!--Device-CommonMethod-onFocusAxisEvent(event: Callback<FocusAxisEvent>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;FocusAxisEvent&gt; | 是 | 焦点轴事件回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ongesturecollectintercept"></a>
## onGestureCollectIntercept

```TypeScript
onGestureCollectIntercept(callback: GestureCollectInterceptCallback): T
```

在当前节点及更高优先级节点上的事件和手势被收集完成后触发该回调。该回调可用于干预事件和手势的收集结果。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onGestureCollectIntercept(callback: GestureCollectInterceptCallback): T--><!--Device-CommonMethod-onGestureCollectIntercept(callback: GestureCollectInterceptCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [GestureCollectInterceptCallback](arkts-arkui-gesturecollectinterceptcallback-t.md) | 是 | 组件进行触摸测试时使用的回调函数。在当前节点及更高优先级节点上的事件和手势收集完成后执行，以干预收集结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ongesturejudgebegin"></a>
## onGestureJudgeBegin

```TypeScript
onGestureJudgeBegin(callback: (gestureInfo: GestureInfo, event: BaseGestureEvent) => GestureJudgeResult): T
```

为组件绑定自定义手势判定回调。当手势即将成功时，触发用户定义的回调获取结果。

> **说明：**  
>  
> 在Text组件中使用该接口时，不支持对点击事件进行自定义手势判定。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onGestureJudgeBegin(callback: (gestureInfo: GestureInfo, event: BaseGestureEvent) => GestureJudgeResult): T--><!--Device-CommonMethod-onGestureJudgeBegin(callback: (gestureInfo: GestureInfo, event: BaseGestureEvent) => GestureJudgeResult): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (gestureInfo: GestureInfo, event: BaseGestureEvent) =&gt; GestureJudgeResult | 是 | A callback instance used when a gesture bound to this component will be accepted. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ongesturerecognizerjudgebegin"></a>
## onGestureRecognizerJudgeBegin

```TypeScript
onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback): T
```

给组件绑定自定义手势识别器判定回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback): T--><!--Device-CommonMethod-onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [GestureRecognizerJudgeBeginCallback](arkts-arkui-gesturerecognizerjudgebegincallback-t.md) | 是 | 自定义手势识别器判定回调。当绑定到该组件的手势即将成功时，会触发用户定义的回调来获取结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ongesturerecognizerjudgebegin-1"></a>
## onGestureRecognizerJudgeBegin

```TypeScript
onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback, exposeInnerGesture: boolean): T
```

给组件绑定自定义手势识别器判定回调。

新增exposeInnerGesture参数作为是否将ArkUI系统组合组件的内置组件的手势暴露给开发者的标识。当该标识置为true时，将ArkUI系统组合组件的内置组件的手势暴露给开发者。

对于不需要将ArkUI系统组合组件的内置组件的手势暴露给开发者的场景，建议采用原有[onGestureRecognizerJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturerecognizerjudgebegin-1)接口。若要求将ArkUI系统组合组件的内置组件的手势暴露给开发者，建议使用该接口并将exposeInnerGesture设置为true。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback, exposeInnerGesture: boolean): T--><!--Device-CommonMethod-onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback, exposeInnerGesture: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [GestureRecognizerJudgeBeginCallback](arkts-arkui-gesturerecognizerjudgebegincallback-t.md) | 是 | 自定义手势识别器判定回调，当绑定到该组件的手势即将成功时，会触发用户定义的回调来获取结果。 |
| exposeInnerGesture | boolean | 是 | 暴露内部手势标识。<br/>默认值：false<br/>**说明：** <br/>如果是组合组件，此参数设置true，回调中的current参数则会包含组合组件内部的手势识别器。<br>当前仅支持[Tabs](arkts-arkui-tabs.md)，其他组件请不要设置此参数。<br/>设置为false时，功能与原接口[onGestureRecognizerJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturerecognizerjudgebegin-1)相同。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onhover"></a>
## onHover

```TypeScript
onHover(event: (isHover: boolean, event: HoverEvent) => void): T
```

鼠标或手写笔进入或退出组件时，触发hover事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onHover(event: (isHover: boolean, event: HoverEvent) => void): T--><!--Device-CommonMethod-onHover(event: (isHover: boolean, event: HoverEvent) => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (isHover: boolean, event: HoverEvent) =&gt; void | 是 | 鼠标的状态信息。<br />event表示设置阻塞事件冒泡属性，并获取鼠标或手写笔悬浮的位置坐标，从API version 11开始支持。<br />isHover表示鼠标或手写笔是否悬浮在组件上，进入时为true， 离开时为false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onhovermove"></a>
## onHoverMove

```TypeScript
onHoverMove(event: Callback<HoverEvent>): T
```

手写笔悬浮于组件上方时触发悬浮移动事件。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onHoverMove(event: Callback<HoverEvent>): T--><!--Device-CommonMethod-onHoverMove(event: Callback<HoverEvent>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;HoverEvent&gt; | 是 | 设置阻塞事件冒泡属性，并获取手写笔悬浮的位置坐标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onkeyevent"></a>
## onKeyEvent

```TypeScript
onKeyEvent(event: (event: KeyEvent) => void): T
```

绑定该方法的组件获焦后，按键动作触发该回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onKeyEvent(event: (event: KeyEvent) => void): T--><!--Device-CommonMethod-onKeyEvent(event: (event: KeyEvent) => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: KeyEvent) =&gt; void | 是 | 获得KeyEvent对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onkeyevent-1"></a>
## onKeyEvent

```TypeScript
onKeyEvent(event: Callback<KeyEvent, boolean>): T
```

当绑定该方法的组件获焦后，按键操作将触发此回调。若此回调的返回值为`true`，则视为按键事件已被处理。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onKeyEvent(event: Callback<KeyEvent, boolean>): T--><!--Device-CommonMethod-onKeyEvent(event: Callback<KeyEvent, boolean>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;KeyEvent, boolean&gt; | 是 | 按键事件的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onkeyeventdispatch"></a>
## onKeyEventDispatch

```TypeScript
onKeyEventDispatch(event: Callback<KeyEvent, boolean>): T
```

对应组件收到按键事件时，会触发该回调，该按键事件不会分发给其子组件。不支持构造KeyEvent进行分发，只支持分发已有的按键事件。

该回调的返回值为`true`时，视作该按键事件已被消费，不会[冒泡](docroot://ui/arkts-interaction-basic-principles.md#事件冒泡)给父组件处理。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onKeyEventDispatch(event: Callback<KeyEvent, boolean>): T--><!--Device-CommonMethod-onKeyEventDispatch(event: Callback<KeyEvent, boolean>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;KeyEvent, boolean&gt; | 是 | 处理按键事件分发的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onkeypreime"></a>
## onKeyPreIme

```TypeScript
onKeyPreIme(event: Callback<KeyEvent, boolean>): T
```

绑定该方法的组件获焦后，按键动作优先触发该回调。

该回调的返回值为`true`时，视作该按键事件已被消费，后续的事件回调（`keyboardShortcut`、输入法事件、`onKeyEventDispatch`、`onKeyEvent`）会被拦截，不再触发。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onKeyPreIme(event: Callback<KeyEvent, boolean>): T--><!--Device-CommonMethod-onKeyPreIme(event: Callback<KeyEvent, boolean>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;KeyEvent, boolean&gt; | 是 | 处理按键事件的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onmouse"></a>
## onMouse

```TypeScript
onMouse(event: (event: MouseEvent) => void): T
```

当前组件被鼠标按键点击时或者鼠标在组件上悬浮移动时，触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onMouse(event: (event: MouseEvent) => void): T--><!--Device-CommonMethod-onMouse(event: (event: MouseEvent) => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: MouseEvent) =&gt; void | 是 | 返回触发事件时的时间戳、鼠标按键、动作、鼠标位置在整个屏幕上的坐标和相对于当前组件的坐标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onneedsoftkeyboard"></a>
## onNeedSoftkeyboard

```TypeScript
onNeedSoftkeyboard(onNeedSoftkeyboardCallback: OnNeedSoftkeyboardCallback | undefined): T
```

组件获焦时回调函数被调用，返回值表示是否需要拉起键盘。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onNeedSoftkeyboard(onNeedSoftkeyboardCallback: OnNeedSoftkeyboardCallback | undefined): T--><!--Device-CommonMethod-onNeedSoftkeyboard(onNeedSoftkeyboardCallback: OnNeedSoftkeyboardCallback | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onNeedSoftkeyboardCallback | [OnNeedSoftkeyboardCallback](arkts-arkui-onneedsoftkeyboardcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="onpredrag"></a>
## onPreDrag

```TypeScript
onPreDrag(callback: Callback<PreDragStatus>): T
```

绑定此事件的组件，当处于手势拖拽发起前的不同阶段时，触发回调。拖拽发起前的各阶段可参考[PreDragStatus](arkts-arkui-predragstatus-e.md)。此接口不支持在鼠标拖拽中触发。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onPreDrag(callback: Callback<PreDragStatus>): T--><!--Device-CommonMethod-onPreDrag(callback: Callback<PreDragStatus>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;PreDragStatus&gt; | 是 | 回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onsizechange"></a>
## onSizeChange

```TypeScript
onSizeChange(event: SizeChangeCallback): T
```

组件区域变化时触发该回调。仅会响应由布局变化所导致的组件尺寸发生变化时的回调。

> **说明：**  
>  
> 1. 该接口在布局发生变化时触发，由于计算精度的关系，其返回值可能与真实物理尺寸存在细微的差异。  
>  
> 2. onSizeChange是布局过程中触发的同步回调，直接在其中更改状态变量存在被纳入动画闭包的风险。具体而言，动画会对比动画前的布局与动画闭包后的布局，若onSizeChange的回调在动画前的布局中同步触发，那么  
> onSizeChange回调中所做的变更将与动画闭包中的变更一同纳入动画过程。为了避免此类问题，可在onSizeChange中使用延迟时间为0的  
> [setTimeout](api/@internal/ets/global:setTimeout)或  
> [postFrameCallback](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#postframecallback-1)，将UI处理逻辑  
> 延后至异步执行。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-onSizeChange(event: SizeChangeCallback): T--><!--Device-CommonMethod-onSizeChange(event: SizeChangeCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [SizeChangeCallback](arkts-arkui-sizechangecallback-t.md) | 是 | 目标元素变化前后的尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ontouch"></a>
## onTouch

```TypeScript
onTouch(event: (event: TouchEvent) => void): T
```

手指触摸动作触发该回调。触摸事件默认[冒泡](docroot://ui/arkts-interaction-basic-principles.md#事件冒泡)，会被多个组件消费，如果需阻止冒泡，可参考[TouchEvent](arkts-arkui-touchevent-i.md)的stopPropagation方法。鼠标左键按下时，对应的事件也会转换成触摸事件并触发该回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onTouch(event: (event: TouchEvent) => void): T--><!--Device-CommonMethod-onTouch(event: (event: TouchEvent) => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: TouchEvent) =&gt; void | 是 | 获得TouchEvent对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ontouchintercept"></a>
## onTouchIntercept

```TypeScript
onTouchIntercept(callback: Callback<TouchEvent, HitTestMode>): T
```

给组件绑定自定义事件拦截回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onTouchIntercept(callback: Callback<TouchEvent, HitTestMode>): T--><!--Device-CommonMethod-onTouchIntercept(callback: Callback<TouchEvent, HitTestMode>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;TouchEvent, HitTestMode&gt; | 是 | 自定义事件拦截回调。在做触摸测试时回调此函数。通过返回值设置组件的HitTestMode。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="ontouchtestdone"></a>
## onTouchTestDone

```TypeScript
onTouchTestDone(callback: TouchTestDoneCallback): T
```

提供在[触摸测试](docroot://ui/arkts-interaction-basic-principles.md#触摸测试)结束后，指定手势识别器是否参与后续处理的能力。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onTouchTestDone(callback: TouchTestDoneCallback): T--><!--Device-CommonMethod-onTouchTestDone(callback: TouchTestDoneCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TouchTestDoneCallback](arkts-arkui-touchtestdonecallback-t.md) | 是 | 回调函数，用于指定手势识别器是否参与后续处理。在[触摸测试](docroot://ui/arkts-interaction-basic-principles.md#触摸测试)结束后，开始识别用户手势之前，会触发该回调来动态指定手势识别器是否参与后续处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onvisibleareaapproximatechange"></a>
## onVisibleAreaApproximateChange

```TypeScript
onVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): T
```

设置onVisibleAreaApproximateChange事件的回调参数，限制它的执行间隔。

> **说明：**  
>  
> 从API version 23开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): T--><!--Device-CommonMethod-onVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [VisibleAreaEventOptions](arkts-arkui-visibleareaeventoptions-i.md) | 是 | 可见区域变化相关的参数。 |
| event | [VisibleAreaChangeCallback](arkts-arkui-visibleareachangecallback-t.md) \| undefined | 是 | onVisibleAreaChange事件的回调函数。当组件可见面积与自身面积的比值接近options中设置的阈值时触发该回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onvisibleareachange"></a>
## onVisibleAreaChange

```TypeScript
onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback): T
```

组件可见区域变化时触发该回调。开发指导及常见问题请参考[感知组件可见性](docroot://ui/arkts-manage-components-visibility.md)指南。

> **说明：**  
>  
> - 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。  
>  
> - 仅提供自身节点相对于所有祖先节点（直到window边界）的相对裁切面积与自身面积的比值及其变化趋势。  
>  
> - 不支持兄弟组件对自身节点的遮挡计算，不支持所有祖先的兄弟节点对自身节点的遮挡计算，不支持窗口遮挡计算，不支持组件旋转计算，如[Stack](../../apis-arkts/arkts-apis/arkts-arkts-util-stack-stack-c.md)、[Z序控制](arkts-arkui-commonmethod-c.md#zindex-1)、  
> [rotate](arkts-arkui-commonmethod-c.md#rotate-1)等。  
>  
> - 不支持非挂树节点的可见面积变化计算。例如，预加载的节点、通过[overlay](arkts-arkui-commonmethod-c.md#overlay-1)能力挂载的自定义节点。  
>  
> - 不支持[scale](arkts-arkui-commonmethod-c.md#scale-1)属性，如果想要支持  
> [scale](arkts-arkui-commonmethod-c.md#scale-1)，则需使用  
> [onVisibleAreaChange<sup>22+</sup>](arkts-arkui-commonmethod-c.md#onvisibleareachange-1)  
> ，将measureFromViewport设置为true。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback): T--><!--Device-CommonMethod-onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ratios | Array&lt;number&gt; | 是 | 阈值数组。其中，每个阈值代表组件可见面积（即组件在屏幕显示区的面积，只计算父组件内的面积，超出父组件部分不会计算）与组件自身面积的比值。当组件可见面积与自身面积的比值接近阈值时，均会触发该回调。每个阈值的取值范围为[0.0, 1.0]，如果开发者设置的阈值小于0.0，则实际取值为0.0；如果设置的阈值大于1.0，则实际取值为1.0。<br/>**说明：** <br/>当数值接近边界0和1时，将会按照误差不超过0.001的规则进行舍入。例如，0.9997会被近似为1。 |
| event | [VisibleAreaChangeCallback](arkts-arkui-visibleareachangecallback-t.md) | 是 | 组件可见区域变化事件的回调。<br>**起始版本：** 13 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="onvisibleareachange-1"></a>
## onVisibleAreaChange

```TypeScript
onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback, measureFromViewport: boolean): T
```

组件可见区域变化时触发该回调。可以通过measureFromViewport设置可见区域计算模式。开发指导及常见问题请参考[感知组件可见性](docroot://ui/arkts-manage-components-visibility.md)指南。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback, measureFromViewport: boolean): T--><!--Device-CommonMethod-onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback, measureFromViewport: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ratios | Array&lt;number&gt; | 是 | 阈值数组。其中，每个阈值代表组件可见面积与组件自身面积的比值。当组件可见面积与自身面积的比值接近阈值时，均会触发该回调。每个阈值的取值范围为[0.0, 1.0]，如果开发者设置的阈值小于0.0，则实际取值为0.0；如果设置的阈值大于1.0，则实际取值为1.0。<br/>**说明：**<br/>当数值接近边界0和1时，将会按照误差不超过0.001的规则进行舍入。例如，0.9997会被近似为1。 |
| event | [VisibleAreaChangeCallback](arkts-arkui-visibleareachangecallback-t.md) | 是 | 组件可见区域变化事件的回调。 |
| measureFromViewport | boolean | 是 | 设置可见区域计算模式。<br/>当measureFromViewport设置为true时，系统在计算该组件的可见区域时，会考虑父组件的[clip](arkts-arkui-commonmethod-c.md#clip-1) 属性设置。如果父组件的[clip](arkts-arkui-commonmethod-c.md#clip-1)为false，则认为其内的子组件可以超出其区域进行显示，因此超出父组件的区域也将被视为可见区域纳入计算；如果父组件的[clip](arkts-arkui-commonmethod-c.md#clip-1)设置为true，则组件超出父组件的区域会被裁剪，无法显示，因此会被视为不可见区域进行计算。而当measureFromViewport设置为false时，则不考虑[clip](arkts-arkui-commonmethod-c.md#clip-1)的影响，直接将组件超出父组件的部分视为不可见区域。<br/>measureFromViewport设置为true时，祖先节点设置[scale](arkts-arkui-commonmethod-c.md#scale-1)属性，组件可见比例会被正确计算。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="opacity"></a>
## opacity

```TypeScript
opacity(value: number | Resource): T
```

设置组件的不透明度。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-opacity(value: number | Resource): T--><!--Device-CommonMethod-opacity(value: number | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| Resource | 是 | 元素的不透明度，取值范围为0到1，若设置的值小于0时，则取值为0，若设置的值大于1时，则取值为1，1表示不透明，0表示完全透明，达到隐藏组件效果，但是在布局中占位。 <br> 默认值：1 <br/>**说明：** <br/> 子组件会继承父组件的透明度，并与自身的透明度属性叠加。如：父组件透明度为0.1，子组件设置透明度为0.8，则子组件实际透明度为0.1*0.8=0.08。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="opacity-1"></a>
## opacity

```TypeScript
opacity(opacity: Optional<number | Resource>): T
```

设置组件的不透明度。与[opacity](arkts-arkui-commonmethod-c.md#opacity-1)相比，opacity参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-opacity(opacity: Optional<number | Resource>): T--><!--Device-CommonMethod-opacity(opacity: Optional<number | Resource>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| opacity | [Optional](arkts-arkui-optional-t.md)&lt;number \| Resource&gt; | 是 | 元素的不透明度，取值范围为0到1，若设置的值小于0时，则取值为0，若设置的值大于1时，则取值为1，1表示不透明，0表示完全透明，达到隐藏组件效果，但是在布局中占位。 <br/> 默认值：1 <br/>**说明：** <br/> 子组件会继承父组件的透明度，并与自身的透明度属性叠加。如：父组件透明度为0.1，子组件设置透明度为0.8，则子组件实际透明度为0.1*0.8=0.08。<br/>当opacity的值为undefined时，恢复为默认不透明度为1的状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="outline"></a>
## outline

```TypeScript
outline(value: OutlineOptions): T
```

统一外描边样式设置接口。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-outline(value: OutlineOptions): T--><!--Device-CommonMethod-outline(value: OutlineOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [OutlineOptions](../arkts-apis/arkts-arkui-outlineoptions-i.md) | 是 | 外描边样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="outline-1"></a>
## outline

```TypeScript
outline(options: Optional<OutlineOptions>): T
```

统一外描边样式设置接口。与[outline](arkts-arkui-commonmethod-c.md#outline-1)相比，options参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-outline(options: Optional<OutlineOptions>): T--><!--Device-CommonMethod-outline(options: Optional<OutlineOptions>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;OutlineOptions&gt; | 是 | 外描边样式。<br/>当options的值为undefined时，恢复为无外边框效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="outlinecolor"></a>
## outlineColor

```TypeScript
outlineColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors): T
```

设置元素的外描边颜色。不设置该接口时，默认显示为黑色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-outlineColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors): T--><!--Device-CommonMethod-outlineColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| EdgeColors \| LocalizedEdgeColors | 是 | 设置元素的外描边颜色。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="outlinecolor-1"></a>
## outlineColor

```TypeScript
outlineColor(color: Optional<ResourceColor | EdgeColors | LocalizedEdgeColors>): T
```

设置元素的外描边颜色。不设置该接口时，默认显示为黑色。与[outlineColor](arkts-arkui-commonmethod-c.md#outlinecolor-1)相比，color参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-outlineColor(color: Optional<ResourceColor | EdgeColors | LocalizedEdgeColors>): T--><!--Device-CommonMethod-outlineColor(color: Optional<ResourceColor | EdgeColors | LocalizedEdgeColors>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)&lt;ResourceColor \| EdgeColors \| LocalizedEdgeColors&gt; | 是 | 设置元素的外描边颜色。<br/>当color的值为undefined时，恢复为描边颜色为Color.Black的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="outlineradius"></a>
## outlineRadius

```TypeScript
outlineRadius(value: Dimension | OutlineRadiuses): T
```

设置元素的外描边圆角半径。不设置该接口时，默认无变化。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-outlineRadius(value: Dimension | OutlineRadiuses): T--><!--Device-CommonMethod-outlineRadius(value: Dimension | OutlineRadiuses): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) \| OutlineRadiuses | 是 | 设置元素的外描边圆角半径，不支持百分比。<br/>最大生效值：组件width/2 + outlineWidth或组件height/2 +outlineWidth。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="outlineradius-1"></a>
## outlineRadius

```TypeScript
outlineRadius(radius: Optional<Dimension | OutlineRadiuses>): T
```

设置元素的外描边圆角半径。不设置该接口时，默认无变化。与[outlineRadius](arkts-arkui-commonmethod-c.md#outlineradius-1)相比，radius参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-outlineRadius(radius: Optional<Dimension | OutlineRadiuses>): T--><!--Device-CommonMethod-outlineRadius(radius: Optional<Dimension | OutlineRadiuses>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | [Optional](arkts-arkui-optional-t.md)&lt;Dimension \| OutlineRadiuses&gt; | 是 | 设置元素的外描边圆角半径，不支持百分比。<br/>最大生效值：组件width/2 + outlineWidth或组件height/2 + outlineWidth。<br/>当radius的值为undefined时，恢复为外描边圆角半径为0的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="outlinestyle"></a>
## outlineStyle

```TypeScript
outlineStyle(value: OutlineStyle | EdgeOutlineStyles): T
```

设置元素的外描边样式。不设置该接口时，默认显示为一条实线。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-outlineStyle(value: OutlineStyle | EdgeOutlineStyles): T--><!--Device-CommonMethod-outlineStyle(value: OutlineStyle | EdgeOutlineStyles): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [OutlineStyle](arkts-arkui-outlinestyle-e.md) \| EdgeOutlineStyles | 是 | 设置元素的外描边样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="outlinestyle-1"></a>
## outlineStyle

```TypeScript
outlineStyle(style: Optional<OutlineStyle | EdgeOutlineStyles>): T
```

设置元素的外描边样式。不设置该接口时，默认显示为一条实线。与[outlineStyle](arkts-arkui-commonmethod-c.md#outlinestyle-1)相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-outlineStyle(style: Optional<OutlineStyle | EdgeOutlineStyles>): T--><!--Device-CommonMethod-outlineStyle(style: Optional<OutlineStyle | EdgeOutlineStyles>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;OutlineStyle \| EdgeOutlineStyles&gt; | 是 | 设置元素的外描边样式。<br/>当style的值为undefined时，恢复为无外描边样式的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="outlinewidth"></a>
## outlineWidth

```TypeScript
outlineWidth(value: Dimension | EdgeOutlineWidths): T
```

设置元素的外描边宽度。不设置该接口时，默认无变化。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-outlineWidth(value: Dimension | EdgeOutlineWidths): T--><!--Device-CommonMethod-outlineWidth(value: Dimension | EdgeOutlineWidths): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) \| EdgeOutlineWidths | 是 | 设置元素的外描边宽度，不支持百分比。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="outlinewidth-1"></a>
## outlineWidth

```TypeScript
outlineWidth(width: Optional<Dimension | EdgeOutlineWidths>): T
```

设置元素的外描边宽度。不设置该接口时，默认无变化。与[outlineWidth](arkts-arkui-commonmethod-c.md#outlinewidth-1)相比，width参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-outlineWidth(width: Optional<Dimension | EdgeOutlineWidths>): T--><!--Device-CommonMethod-outlineWidth(width: Optional<Dimension | EdgeOutlineWidths>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-optional-t.md)&lt;Dimension \| EdgeOutlineWidths&gt; | 是 | 设置元素的外描边宽度，不支持百分比。<br/>当width的值为undefined时，恢复为无外描边宽度的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="overlay"></a>
## overlay

```TypeScript
overlay(value: string | CustomBuilder | ComponentContent, options?: OverlayOptions): T
```

在当前组件上，增加遮罩文本或者叠加自定义组件以及[ComponentContent](arkts-arkui-componentcontent-t.md)作为该组件的浮层。浮层的定位同样基于当前组件进行计算。浮层不通过组件树进行渲染，部分接口（例如[getRectangleById](api\@ohos.arkui.ComponentUtils#getRectangleById)）不支持获取浮层中的组件。

> **说明：**  
>  
> - overlay会将浮层组件覆盖在所绑定的组件上方，阻塞用户对浮层下方组件的所有交互操作。  
> - 多次调用overlay接口时，如果同时传入string类型和  
> [CustomBuilder](arkts-arkui-custombuilder-t.md)类型，或者同时传入string类型和  
> [ComponentContent](arkts-arkui-componentcontent-t.md)类型，浮层内容会叠加显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-overlay(value: string | CustomBuilder | ComponentContent, options?: OverlayOptions): T--><!--Device-CommonMethod-overlay(value: string | CustomBuilder | ComponentContent, options?: OverlayOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| CustomBuilder \| ComponentContent | 是 | 遮罩文本内容或自定义组件构造函数。<br/>**说明：**<br/>自定义组件作为浮层时，不支持键盘走焦到自定义组件中。通过CustomBuilder设置浮层时，浮层中的内容会在页面刷新时销毁并重新创建，存在一定的性能损耗，页面频繁刷新的场景推荐使用ComponentContent方式设置浮层。<br>**起始版本：** 12 |
| options | [OverlayOptions](arkts-arkui-overlayoptions-i.md) | 否 | 浮层的定位。<br/>**说明：**<br/>API version 12之前，options: <br/>{<br/>align?: [Alignment](../arkts-apis/arkts-arkui-alignment-e.md), <br/>offset?: {x?: number, y?: number}<br/>}<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="padding"></a>
## padding

```TypeScript
padding(value: Padding | Length | LocalizedPadding): T
```

设置组件的内边距属性。

从API version 10开始，该接口支持calc计算特性。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-padding(value: Padding | Length | LocalizedPadding): T--><!--Device-CommonMethod-padding(value: Padding | Length | LocalizedPadding): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Padding](../arkts-apis/arkts-arkui-padding-t.md) \| Length \| LocalizedPadding | 是 | Padding of the component to set<br>When the parameter is of the **Length** type, the four paddings take effect.<br>Default value: **0**<br>Unit: vp<br>When **padding** is set to a percentage, the width of the parent container is used as the basic value.<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="parallelgesture"></a>
## parallelGesture

```TypeScript
parallelGesture(gesture: GestureType, mask?: GestureMask): T
```

绑定可与子组件手势同时触发的手势。手势事件为非冒泡事件。父组件设置parallelGesture时，父子组件相同的手势事件都可以触发，实现类似冒泡效果。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-parallelGesture(gesture: GestureType, mask?: GestureMask): T--><!--Device-CommonMethod-parallelGesture(gesture: GestureType, mask?: GestureMask): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesture | [GestureType](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-gesturetype-t.md) | 是 | 绑定的手势对象。 |
| mask | [GestureMask](../arkts-apis/arkts-arkui-gesturemask-e.md) | 否 | 事件响应设置。<br/>默认值：GestureMask.Normal |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="pixelround"></a>
## pixelRound

```TypeScript
pixelRound(value: PixelRoundPolicy): T
```

指定当前组件在指定方向上的像素取整对齐方式，某方向不设置时默认在该方向进行四舍五入取整。

> **说明：**  
>  
> - 在API version 11，本接口采用半像素对齐方式（即0\~0.25取0，0.25\~0.75取0.5，0.75\~1.0取1）。从API version12开始，本接口采用四舍五入的取整方式，并支持组件级关闭像素取整的能力。  
>  
> - 从API version12开始，该接口支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

正常计算时，上下方向与组件高度相对应，左右方向（镜像的起始方向称为左）与宽度相对应。为方便描述将两组方向称为左上和右下。

- 计算当前组件左上角坐标： 左上角相对父容器偏移量。  
- 计算当前组件右下角坐标： 左上角相对于父容器偏移量 + 组件自身尺寸。  
- 重新计算当前组件尺寸： 右下角坐标四舍五入取整 - 左上角坐标四舍五入取整。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-pixelRound(value: PixelRoundPolicy): T--><!--Device-CommonMethod-pixelRound(value: PixelRoundPolicy): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PixelRoundPolicy](arkts-arkui-pixelroundpolicy-i.md) | 是 | 指定当前组件边界取整策略。<br/>**说明：**<br/>该属性用于因浮点数绘制产生视觉异常的场景。取整结果不仅和组件的宽高有关，也与组件的位置有关。即使设置组件的宽高相同，由于以浮点数描述的组件位置不同，舍入后组件的最终宽高也可能不同。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="pixelstretcheffect"></a>
## pixelStretchEffect

```TypeScript
pixelStretchEffect(options: PixelStretchEffectOptions): T
```

设置组件的图像边缘像素扩展距离。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-pixelStretchEffect(options: PixelStretchEffectOptions): T--><!--Device-CommonMethod-pixelStretchEffect(options: PixelStretchEffectOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PixelStretchEffectOptions](arkts-arkui-pixelstretcheffectoptions-i.md) | 是 | 设置组件的图像边缘像素扩展距离。<br/>参数`options`包括上下左右四个方向的边缘像素扩展距离。<br/>**说明：**<br/   >1. 如果距离为正值，表示向外扩展，放大原来图像大小。上下左右四个方向分别用边缘像素填充，填充的距离即为设置的边缘扩展的距离。<br/>2. 如果距离为负值，表示内缩，但是最终图像大小不变。<br/>内缩方式：<br/>图像根据`options`的设置缩小，缩小大小为四个方向边缘扩展距离的绝对值。<br/>图像用边缘像素扩展到原来大小。<br/>3. 对`options`的输入约束：<br/>上下左右四个方向的扩展统一为非正值或者非负值。即四个边同时向外扩或者内缩，方向一致。<br/>所有方向的输入均为百分比或者具体值，不支持百分比和具体值混用。<br/>所有异常情况下，显示为{0, 0, 0, 0}效果，即跟原图保持一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="pixelstretcheffect-1"></a>
## pixelStretchEffect

```TypeScript
pixelStretchEffect(options: Optional<PixelStretchEffectOptions>): T
```

设置组件的图像边缘像素扩展距离。与[pixelStretchEffect<sup>12+</sup>](arkts-arkui-commonmethod-c.md#pixelstretcheffect-1)相比，options参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-pixelStretchEffect(options: Optional<PixelStretchEffectOptions>): T--><!--Device-CommonMethod-pixelStretchEffect(options: Optional<PixelStretchEffectOptions>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;PixelStretchEffectOptions&gt; | 是 | 设置组件的图像边缘像素扩展距离。<br/>参数`options`包括上下左右四个方向的边缘像素扩展距离。<br/>**说明：**<br/>1. 如果距离为正值，表示向外扩展，放大原来图像大小。上下左右四个方向分别用边缘像素填充，填充的距离即为设置的边缘扩展的距离。<br/>2. 如果距离为负值，表示内缩，但是最终图像大小不变。<br/   >内缩方式：<br/>图像根据`options`的设置缩小，缩小大小为四个方向边缘扩展距离的绝对值。<br/>图像用边缘像素扩展到原来大小。<br/>3. 对`options`的输入约束：<br/>上下左右四个方向的扩展统一为非正值或者非负值。即四个边同时向外扩或者内缩，方向一致。<br/>所有方向的输入均为百分比或者具体值，不支持百分比和具体值混用。<br/>所有异常情况下，显示为{0, 0, 0, 0}效果，即跟原图保持一致。<br/>当options的值为undefined时，恢复为无像素扩展效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="position"></a>
## position

```TypeScript
position(value: Position | Edges | LocalizedEdges): T
```

绝对定位，确定子组件相对父组件内容区的位置，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

> **说明：**  
>  
> - position对位置的影响作用在组件的尺寸测量完成之后。  
> - 当父组件为[Row](Row)、[Column](Column)或[Flex](Flex)时，设置position的子组件不占位。在上述场景中，如果父组件包含的所有子组件均设置了position，此时父组件尺寸无法通过其他子组件确定，将基于尺寸(0, 0)进行布局测算。  
> -Position类型基于父组件内容区左上角确定位置；Edges类型基于父组件内容区四边确定位置，top/left/right/bottom分别为组件各边距离父组件内容区相应边的边距，通过边距来确定组件相对于父组件内容区的位置；Lo calizedEdges类型基于父组件内容区四边确定位置，支持镜像模式。  
> - 本属性适用于置顶显示、悬浮按钮等组件在父组件中位置固定的场景。  
> - 本属性不支持在宽高为零的布局组件上设置。  
> - 当父组件为[RelativeContainer](RelativeContainer)，且子组件设置了alignRules属性时，子组件的position属性不生效。  
> - 若本属性所在组件的父组件未设置固定宽高，那么本组件会参考第一个设置固定宽高的祖先组件进行绝对定位。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-position(value: Position | Edges | LocalizedEdges): T--><!--Device-CommonMethod-position(value: Position | Edges | LocalizedEdges): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Position](../arkts-apis/arkts-arkui-display-position-i.md) \| Edges \| LocalizedEdges | 是 | Absolute positioning that determines the child component's position relative to the parent's content area. The content area of the parent component is calculated by subtracting the [border](arkts-arkui-commonmethod-c.md#border-1), [padding](arkts-arkui-commonmethod-c.md#padding-1), and [safeAreaPadding](arkts-arkui-commonmethod-c.md#safeareapadding-1)values from the parent component's total size. This resulting content area defines the available layout space for child components. This attribute does not take effect when it is set to an abnormal value.<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="prioritygesture"></a>
## priorityGesture

```TypeScript
priorityGesture(gesture: GestureType, mask?: GestureMask): T
```

绑定优先识别手势。

1. 默认情况下，子组件优先识别通过gesture绑定的手势，当父组件配置priorityGesture时，父组件优先识别priorityGesture绑定的手势。2. 绑定长按手势时，设置触发长按的最短时间小的组件会优先响应，会忽略priorityGesture设置。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-priorityGesture(gesture: GestureType, mask?: GestureMask): T--><!--Device-CommonMethod-priorityGesture(gesture: GestureType, mask?: GestureMask): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesture | [GestureType](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-gesturetype-t.md) | 是 | 绑定的手势对象。 |
| mask | [GestureMask](../arkts-apis/arkts-arkui-gesturemask-e.md) | 否 | 事件响应设置。<br/>默认值：GestureMask.Normal |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="radialgradient"></a>
## radialGradient

```TypeScript
radialGradient(value: RadialGradientOptions): T
```

径向渐变。

Anonymous Object Rectification.

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-radialGradient(value: RadialGradientOptions): T--><!--Device-CommonMethod-radialGradient(value: RadialGradientOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RadialGradientOptions](arkts-arkui-radialgradientoptions-i.md) | 是 | 径向渐变。<br>**起始版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="radialgradient-1"></a>
## radialGradient

```TypeScript
radialGradient(options: Optional<RadialGradientOptions>): T
```

径向渐变。与[radialGradient](arkts-arkui-commonmethod-c.md#radialgradient-1)相比，options参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-radialGradient(options: Optional<RadialGradientOptions>): T--><!--Device-CommonMethod-radialGradient(options: Optional<RadialGradientOptions>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;RadialGradientOptions&gt; | 是 | 径向渐变。<br/>当options的值为undefined时，恢复为无径向渐变的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="renderfit"></a>
## renderFit

```TypeScript
renderFit(fitMode: RenderFit): T
```

设置宽高动画过程中的组件内容填充方式。不通过该接口设置，保持动画终态的内容大小，并且内容始终与组件保持左上角对齐。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-renderFit(fitMode: RenderFit): T--><!--Device-CommonMethod-renderFit(fitMode: RenderFit): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fitMode | [RenderFit](../arkts-apis/arkts-arkui-renderfit-e.md) | 是 | 设置宽高动画过程中的组件内容填充方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="renderfit-1"></a>
## renderFit

```TypeScript
renderFit(fitMode: Optional<RenderFit>): T
```

设置宽高动画过程中的组件内容填充方式。不通过该接口设置，保持动画终态的内容大小，并且内容始终与组件保持左上角对齐。与[renderFit](arkts-arkui-commonmethod-c.md#renderfit-1)相比，fitMode参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-renderFit(fitMode: Optional<RenderFit>): T--><!--Device-CommonMethod-renderFit(fitMode: Optional<RenderFit>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fitMode | [Optional](arkts-arkui-optional-t.md)&lt;RenderFit&gt; | 是 | 设置宽高动画过程中的组件内容填充方式。<br/>当fitMode的值为undefined时，取默认值。恢复为内容填充方式为RenderFit.TOP_LEFT的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="rendergroup"></a>
## renderGroup

```TypeScript
renderGroup(value: boolean): T
```

设置是否组成节点组。节点组表示当前组件和子组件组成的子树先在离屏画布中渲染，再与父组件融合绘制。设置为节点组后，系统会缓存绘制结果，提升性能。但如果节点组内的组件频繁更新，缓存失效，可能导致性能下降。此外，设置为节点组后，当前组件的不透明度不为1时，绘制效果可能有差异。

不设置该属性时，默认不组成节点组。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-renderGroup(value: boolean): T--><!--Device-CommonMethod-renderGroup(value: boolean): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置当前组件和子组件是否组成节点组。<br/> false表示不组成节点组，不进行离屏渲染直接绘制。<br/> true表示当前组件和子组件组成节点组，进行离屏渲染后再与父组件融合绘制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="rendergroup-1"></a>
## renderGroup

```TypeScript
renderGroup(isGroup: Optional<boolean>): T
```

设置是否组成节点组。节点组表示当前组件和子组件组成的子树先在离屏画布中渲染，再与父组件融合绘制。设置为节点组后，系统会缓存绘制结果，提升性能。但如果节点组内的组件频繁更新，缓存失效，可能导致性能下降。此外，设置为节点组后，当前组件的不透明度不为1时，绘制效果可能有差异。

与[renderGroup<sup>10+</sup>](arkts-arkui-commonmethod-c.md#rendergroup-1)相比，isGroup参数新增了对undefined类型的支持。

不设置该属性时，默认不组成节点组。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-renderGroup(isGroup: Optional<boolean>): T--><!--Device-CommonMethod-renderGroup(isGroup: Optional<boolean>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isGroup | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置当前组件和子组件是否组成节点组。<br/> false表示不组成节点组，不进行离屏渲染直接绘制。<br/> true表示当前组件和子组件组成节点组，进行离屏渲染后再与父组件融合绘制。<br/>当isGroup的值为undefined时，按照不组成节点组处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="responseregion"></a>
## responseRegion

```TypeScript
responseRegion(value: Array<Rectangle> | Rectangle): T
```

设置一个或多个触摸热区。从API版本26.0.0开始，未主动设置时[Button](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-mouseevent-button-e.md)、[Button模式的Toggle](arkts-arkui-toggle.md)、[Select](arkts-arkui-select.md)、[Chip](../arkts-apis/arkts-arkui-advanced-chip.md)和[ChipGroup](../arkts-apis/arkts-arkui-advanced-chipgroup.md)组件的触摸热区默认最小高度从28vp变更为32vp。该变更仅影响触摸命中范围，不影响组件实际显示高度。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-responseRegion(value: Array<Rectangle> | Rectangle): T--><!--Device-CommonMethod-responseRegion(value: Array<Rectangle> | Rectangle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;Rectangle&gt; \| Rectangle | 是 | 触摸热区，包括位置和大小。<br/>默认触摸热区为整个组件，默认值：<br/>{<br/>x：0,<br/>y：0,<br/>width：'100%',<br/>height：'100%'<br/>}<br/> |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="responseregionlist"></a>
## responseRegionList

```TypeScript
responseRegionList(regions: Array<ResponseRegion>): T
```

设置组件的触摸热区列表。调用该接口时，[responseRegion](arkts-arkui-commonmethod-c.md#responseregion-1)与[mouseResponseRegion](arkts-arkui-commonmethod-c.md#mouseresponseregion-1)接口不再生效。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-responseRegionList(regions: Array<ResponseRegion>): T--><!--Device-CommonMethod-responseRegionList(regions: Array<ResponseRegion>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| regions | Array&lt;ResponseRegion&gt; | 是 | 组件的触摸热区数组。<br/>每个触摸热区均包括输入工具类型、位置和大小。<br/>默认值：<br/>[{<br/>tool：ResponseRegionSupportedTool.ALL,<br/>x：LengthMetrics.vp(0),<br/>y：LengthMetrics.vp(0),<br/>width：LengthMetrics.percent(1),<br/>height：LengthMetrics.percent(1)<br/>}] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="restoreid"></a>
## restoreId

```TypeScript
restoreId(value: number): T
```

id for distribute identification.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-restoreId(value: number): T--><!--Device-CommonMethod-restoreId(value: number): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform@atomicservice |

<a id="reuse"></a>
## reuse

```TypeScript
reuse(options: ReuseOptions): T
```

Reuse id is used for identify the reuse type of each @ComponentV2 custom component, which can give user control of sub-component recycle and reuse.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-reuse(options: ReuseOptions): T--><!--Device-CommonMethod-reuse(options: ReuseOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ReuseOptions](arkts-arkui-reuseoptions-i.md) | 是 | The configuration parameter for reusable custom component. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="reuseid"></a>
## reuseId

```TypeScript
reuseId(id: string): T
```

Reuse id is used for identify the reuse type for each custom node.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-reuseId(id: string): T--><!--Device-CommonMethod-reuseId(id: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | The id for reusable custom node. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="rotate"></a>
## rotate

```TypeScript
rotate(value: RotateOptions): T
```

设置组件旋转。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-rotate(value: RotateOptions): T--><!--Device-CommonMethod-rotate(value: RotateOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RotateOptions](arkts-arkui-rotateoptions-i.md) | 是 | 可使组件在以组件左上角为坐标原点的[组件坐标系](docroot://ui/arkui-glossary.md#组件坐标系)中进行旋转（坐标系如下图所示）。其中，(x, y, z）指定一个矢量，作为旋转轴。<br/>旋转轴和旋转中心点都基于坐标系设定，组件发生位移时，坐标系不会随之移动。<br/>默认值: 在x、y、z都不指定时，x、y、z的默认值分别为0、0、1。指定了x、y、z任何一个值时，x、y、z中未指定的值默认为0。<br/>{<br/>centerX: '50%',<br/>centerY: '50%',<br/>centerZ: 0,<br/>perspective: 0<br/>}<br/>单位：vp<br/>![coordinates](docroot://reference/apis-arkui/arkui-ts/figures/coordinates.png) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="rotate-1"></a>
## rotate

```TypeScript
rotate(options: Optional<RotateOptions>): T
```

设置组件旋转。与[rotate](arkts-arkui-commonmethod-c.md#rotate-1)相比，options参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-rotate(options: Optional<RotateOptions>): T--><!--Device-CommonMethod-rotate(options: Optional<RotateOptions>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;RotateOptions&gt; | 是 | 可使组件在以组件左上角为坐标原点的[组件坐标系](docroot://ui/arkui-glossary.md#组件坐标系)中进行旋转（坐标系如下图所示）。其中，(x, y, z）指定一个矢量，作为旋转轴。<br/>旋转轴和旋转中心点都基于坐标系设定，组件发生位移时，坐标系不会随之移动。<br/>默认值: 在x、y、z都不指定时，x、y、z的默认值分别为0、0、1。指定了x、y、z任何一个值时，x、y、z中未指定的值默认为0。<br/>{<br/>centerX: '50%',<br/>centerY: '50%',<br/>centerZ: 0,<br/>perspective: 0<br/>}<br/>单位：vp<br/>![coordinates](docroot://reference/apis-arkui/arkui-ts/figures/coordinates.png)。<br/>当options的值为undefined时，恢复为无旋转效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="rotate-2"></a>
## rotate

```TypeScript
rotate(options: Optional<RotateOptions | RotateAngleOptions>): T
```

设置组件旋转效果。与[rotate](arkts-arkui-commonmethod-c.md#rotate-1)相比，options参数新增了对RotateAngleOptions类型的支持。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-rotate(options: Optional<RotateOptions | RotateAngleOptions>): T--><!--Device-CommonMethod-rotate(options: Optional<RotateOptions | RotateAngleOptions>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;RotateOptions \| RotateAngleOptions&gt; | 是 | RotateOptions可使组件在以组件左上角为坐标原点的坐标系中进行旋转（坐标系如下图所示）。其中，(x, y, z）指定一个矢量，作为旋转轴。<br/>旋转轴和旋转中心点都基于[组件坐标系](docroot://ui/arkui-glossary.md#组件坐标系)设定，组件发生位移时，坐标系不会随之移动。<br/>默认值：在x、y、z都不指定时，x、y、z的默认值分别为0、0、1。指定了x、y、z任何一个值时，x、y、z中未指定的值默认为0。<br/>{<br/>centerX: '50%',<br/>centerY: '50%',<br/>centerZ: 0,<br/>perspective: 0<br/>}<br/>RotateAngleOptions可使组件在以组件左上角为坐标原点的坐标系中进行旋转（坐标系如下图所示）。其中，(angleX, angleY, angleZ）指定三个轴方向上的旋转角。<br/>默认值：<br/>{<br/>angleX:0,<br />angleY:0,<br />angleZ:0,<br />centerX: '50%',<br/>centerY: '50%',<br/>centerZ: 0,<br/>perspective: 0<br/>}<br/>![coordinates](docroot://reference/apis-arkui/arkui-ts/figures/coordinates.png)<br/>当options的值为undefined时，恢复为无旋转效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="safeareapadding"></a>
## safeAreaPadding

```TypeScript
safeAreaPadding(paddingValue: Padding | LengthMetrics | LocalizedPadding): T
```

设置安全区边距属性。允许容器向自身添加组件级安全区域，供子组件延伸，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

> **说明**  
>  
>当父辈和祖先容器设置了组件级安全区域时，子组件可以感知并利用该区域，称该区域为累计安全区延伸（accumulatedSafeAreaExpand，下文简称SAE），表示子组件在四个方向上各可延伸的长度。当祖辈与更上一级祖辈的saf eAreaPadding相邻接（即未被margin、border、padding分隔）时，SAE将递归地向外累积，直至不存在相邻的更外层safeAreaPadding或递归至页面容器外。系统级避让区域（如状态栏、导航条、挖孔区等，详情参见安全区域中的说明）可视为页面容器特有的safeAreaPadding，同样参与该延伸范围的计算。  
>  
> 通过与其他属性配合使用，可对上述计算得到的组件级安全区区域加以利用。例如，对子组件设置[ignoreLayoutSafeArea](arkts-arkui-commonmethod-c.md#ignorelayoutsafearea-1)属性，即可利用SAE延伸组件的布局范围。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本14开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-safeAreaPadding(paddingValue: Padding | LengthMetrics | LocalizedPadding): T--><!--Device-CommonMethod-safeAreaPadding(paddingValue: Padding | LengthMetrics | LocalizedPadding): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| paddingValue | [Padding](../arkts-apis/arkts-arkui-padding-t.md) \| LengthMetrics \| LocalizedPadding | 是 | 设置组件的安全区边距。<br>单位为： vp。 默认值： 0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="saturate"></a>
## saturate

```TypeScript
saturate(value: number): T
```

为组件添加饱和度效果。不通过该接口设置时，默认无变化。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-saturate(value: number): T--><!--Device-CommonMethod-saturate(value: number): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 为当前组件添加饱和度效果，饱和度为颜色中的含色成分和消色成分(灰)的比例，入参为1时，显示原图像，大于1时含色成分越大，饱和度越大，小于1时消色成分越大，饱和度越小。<br/>推荐取值范围：[0, 50)<br/>**说明：**<br/>设置小于0的值时，按值为0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="saturate-1"></a>
## saturate

```TypeScript
saturate(saturate: Optional<number>): T
```

为组件添加饱和度效果。不通过该接口设置时，默认无变化。与[saturate](arkts-arkui-commonmethod-c.md#saturate-1)相比，saturate参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-saturate(saturate: Optional<number>): T--><!--Device-CommonMethod-saturate(saturate: Optional<number>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| saturate | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 为当前组件添加饱和度效果，饱和度为颜色中的含色成分和消色成分(灰)的比例，入参为1时，显示原图像，大于1时含色成分越大，饱和度越大，小于1时消色成分越大，饱和度越小。<br/>推荐取值范围：[0, 50)<br/>**说明：**<br/>设置小于0的值时，按值为0处理。<br/>当saturate的值为undefined时。恢复为饱和度为1的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="scale"></a>
## scale

```TypeScript
scale(value: ScaleOptions): T
```

设置组件缩放。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-scale(value: ScaleOptions): T--><!--Device-CommonMethod-scale(value: ScaleOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScaleOptions](arkts-arkui-scaleoptions-i.md) | 是 | 可以分别设置X轴、Y轴、Z轴的缩放比例，默认值为1，同时可以通过centerX和centerY设置缩放的中心点。<br/>默认值:<br/>{<br/>x: 1,<br/>y: 1,<br/>z: 1,<br/>centerX:'50%',<br/>centerY:'50%'<br/>} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="scale-1"></a>
## scale

```TypeScript
scale(options: Optional<ScaleOptions>): T
```

设置组件缩放。与[scale](arkts-arkui-commonmethod-c.md#scale-1)相比，options参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-scale(options: Optional<ScaleOptions>): T--><!--Device-CommonMethod-scale(options: Optional<ScaleOptions>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;ScaleOptions&gt; | 是 | 可以分别设置X轴、Y轴、Z轴的缩放比例，默认值为1，同时可以通过centerX和centerY设置缩放的中心点。<br/>默认值:<br/>{<br/>x: 1,<br/>y: 1,<br/>z: 1,<br/>centerX:'50%',<br/>centerY:'50%'<br/>}<br/>当options的值为undefined时，恢复为无缩放效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="sepia"></a>
## sepia

```TypeScript
sepia(value: number): T
```

将图像转换为深褐色。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-sepia(value: number): T--><!--Device-CommonMethod-sepia(value: number): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 将图像转换为深褐色，降低色彩度，产生温暖复古的图像风格。入参为褐色滤镜强度，值为1则完全是深褐色的，值小于等于0则图像无变化，值大于1会进一步放大色彩偏移比例，图像整体会变得更亮且色彩更加偏黄/偏红，但不属于标准sepia效果。<br/>取值范围：[0, +∞)，推荐取值范围：(0, 1]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="sepia-1"></a>
## sepia

```TypeScript
sepia(sepia: Optional<number>): T
```

将图像转换为深褐色。与[sepia](arkts-arkui-commonmethod-c.md#sepia-1)相比，sepia参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-sepia(sepia: Optional<number>): T--><!--Device-CommonMethod-sepia(sepia: Optional<number>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sepia | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 将图像转换为深褐色，降低色彩度，产生温暖复古的图像风格。入参为褐色滤镜强度，值为1则完全是深褐色的，值小于等于0则图像无变化，值大于1会进一步放大色彩偏移比例，图像整体会变得更亮且色彩更加偏黄/偏红，但不属于标准sepia效果。<br/>当sepia的值为undefined时，恢复为图像无变化的效果。<br/> 取值范围：[0, +∞)，推荐取值范围：(0, 1]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="shadow"></a>
## shadow

```TypeScript
shadow(value: ShadowOptions | ShadowStyle): T
```

为组件添加阴影效果。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-shadow(value: ShadowOptions | ShadowStyle): T--><!--Device-CommonMethod-shadow(value: ShadowOptions | ShadowStyle): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ShadowOptions](arkts-arkui-shadowoptions-i.md) \| ShadowStyle | 是 | 为当前组件添加阴影效果。<br/>入参类型为ShadowOptions时，可以指定模糊半径、阴影的颜色、X轴和Y轴的偏移量。<br/>入参类型为ShadowStyle时，可指定不同阴影样式。<br>**起始版本：** 7 - 9 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="shadow-1"></a>
## shadow

```TypeScript
shadow(options: Optional<ShadowOptions | ShadowStyle>): T
```

为组件添加阴影效果。与[shadow](arkts-arkui-commonmethod-c.md#shadow-1)相比，options参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-shadow(options: Optional<ShadowOptions | ShadowStyle>): T--><!--Device-CommonMethod-shadow(options: Optional<ShadowOptions | ShadowStyle>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;ShadowOptions \| ShadowStyle&gt; | 是 | 为当前组件添加阴影效果。<br/>入参类型为ShadowOptions时，可以指定模糊半径、阴影的颜色、X轴和Y轴的偏移量。<br/>入参类型为ShadowStyle时，可指定不同阴影样式。<br/>当options的值为undefined时，恢复为无样式的阴影效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="sharedtransition"></a>
## sharedTransition

```TypeScript
sharedTransition(id: string, options?: sharedTransitionOptions): T
```

设置共享元素转场动效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-sharedTransition(id: string, options?: sharedTransitionOptions): T--><!--Device-CommonMethod-sharedTransition(id: string, options?: sharedTransitionOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 两个页面中id值相同且不为空字符串的组件即为共享元素，在页面转场时可显示共享元素转场动效。 |
| options | [sharedTransitionOptions](arkts-arkui-sharedtransitionoptions-i.md) | 否 | 共享元素转场动画参数。不设置时使用默认转场动画参数。各参数具体默认值参考[sharedTransitionOptions](arkts-arkui-sharedtransitionoptions-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="shouldbuiltinrecognizerparallelwith"></a>
## shouldBuiltInRecognizerParallelWith

```TypeScript
shouldBuiltInRecognizerParallelWith(callback: ShouldBuiltInRecognizerParallelWithCallback): T
```

提供系统内置手势与响应链上其他组件的手势设置并行关系的回调事件。此接口对应的C API接口为[setInnerGestureParallelTo](docroot://reference/apis-arkui/capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setinnergestureparallelto)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-shouldBuiltInRecognizerParallelWith(callback: ShouldBuiltInRecognizerParallelWithCallback): T--><!--Device-CommonMethod-shouldBuiltInRecognizerParallelWith(callback: ShouldBuiltInRecognizerParallelWithCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ShouldBuiltInRecognizerParallelWithCallback](arkts-arkui-shouldbuiltinrecognizerparallelwithcallback-t.md) | 是 | 系统内置手势与响应链上其他组件的手势设置并行关系的回调事件，当该组件进行触摸碰撞测试时，会触发用户定义的回调来形成手势并行关系。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="shouldrecognizerparallelwith"></a>
## shouldRecognizerParallelWith

```TypeScript
shouldRecognizerParallelWith(callback: ShouldRecognizerParallelWithCallback): T
```

提供手势与响应链上其他组件的手势设置并行关系的回调事件。使用callback异步回调。此接口对应的C API接口为[setGestureParallelTo](docroot://reference/apis-arkui/capi-arkui-nativemodule-arkui-nativegestureapi-3.md#setgestureparallelto)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-shouldRecognizerParallelWith(callback: ShouldRecognizerParallelWithCallback): T--><!--Device-CommonMethod-shouldRecognizerParallelWith(callback: ShouldRecognizerParallelWithCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ShouldRecognizerParallelWithCallback](arkts-arkui-shouldrecognizerparallelwithcallback-t.md) | 是 | A callback instance used when a component is doing touch test. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="size"></a>
## size

```TypeScript
size(value: SizeOptions): T
```

设置组件自身的宽高尺寸。

从API version 10开始，该接口支持calc计算特性。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-size(value: SizeOptions): T--><!--Device-CommonMethod-size(value: SizeOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) | 是 | 设置宽高尺寸。异常值：参数为undefined时，属性设置不生效；其它异常值时，size属性恢复到不配置时的默认行为。单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="smartgestureshortcut"></a>
## smartGestureShortcut

```TypeScript
smartGestureShortcut(options?: SmartGestureShortcutOptions): T
```

设置组件智慧手势响应行为配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-smartGestureShortcut(options?: SmartGestureShortcutOptions): T--><!--Device-CommonMethod-smartGestureShortcut(options?: SmartGestureShortcutOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SmartGestureShortcutOptions](arkts-arkui-smartgestureshortcutoptions-i.md) | 否 | 组件智慧手势响应配置。SmartGestureShortcutOptions中enabled用于配置组件是否响应智慧手势。selectable用于设置组件被智慧手势操作选中后是否展示并保留选中态。action用于设置智慧手势响应优先级，当前仅支持GestureShortcut.PRIMARY，会使组件在智慧手势的滑动，点击等操作中作为首选响应目标。建议显式传入，避免因缺省配置导致预期不一致，缺省配置处理参考[SmartGestureShortcutOptions](arkts-arkui-smartgestureshortcutoptions-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="sphericaleffect"></a>
## sphericalEffect

```TypeScript
sphericalEffect(value: number): T
```

设置组件的图像球面化程度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-sphericalEffect(value: number): T--><!--Device-CommonMethod-sphericalEffect(value: number): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置组件的图像球面化程度。<br/>取值范围：[0,1]。<br/>**说明：**<br/>1. 如果value等于0则图像保持原样，如果value等于1则图像为完全球面化效果。在0和1之间，数值越大，则球面化程度越高。<br/>`value < 0 `或者` value > 1`为异常情况，`value < 0`按0处理，`value > 1`按1处理。<br/>2. 组件阴影和外描边不支持球面效果。<br>3. 设置value大于0时，组件冻屏并且把组件内容绘制到透明离屏buffer上，如果要更新组件属性则需要把value设置为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="sphericaleffect-1"></a>
## sphericalEffect

```TypeScript
sphericalEffect(effect: Optional<number>): T
```

设置组件的图像球面化程度。与[sphericalEffect<sup>12+</sup>](arkts-arkui-commonmethod-c.md#sphericaleffect-1)相比，effect参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-sphericalEffect(effect: Optional<number>): T--><!--Device-CommonMethod-sphericalEffect(effect: Optional<number>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 设置组件的图像球面化程度。<br/>取值范围：[0,1]。<br/>**说明：**<br/>1. 如果value等于0则图像保持原样，如果value等于1则图像为完全球面化效果。在0和1之间，数值越大，则球面化程度越高。<br/>`effect < 0 `或者` effect > 1`为异常情况，`effect < 0`按0处理，`effect > 1`按1处理。<br/>2. 组件阴影和外描边不支持球面效果。<br/>3. 设置effect大于0时，组件冻屏并且把组件内容绘制到透明离屏buffer上，如果要更新组件属性则需要把effect设置为0。<br/>当effect的值为undefined时，恢复为图像球面化程度为0的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="statestyles"></a>
## stateStyles

```TypeScript
stateStyles(value: StateStyles): T
```

设置组件不同状态下的样式。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-stateStyles(value: StateStyles): T--><!--Device-CommonMethod-stateStyles(value: StateStyles): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [StateStyles](arkts-arkui-statestyles-i.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="sweepgradient"></a>
## sweepGradient

```TypeScript
sweepGradient(value: SweepGradientOptions): T
```

角度渐变。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-sweepGradient(value: SweepGradientOptions): T--><!--Device-CommonMethod-sweepGradient(value: SweepGradientOptions): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SweepGradientOptions](arkts-arkui-sweepgradientoptions-i.md) | 是 | 角度渐变，仅绘制0-360度范围内的角度，超出时不绘制渐变色，只绘制纯色。<br>**起始版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@crossplatform@form@atomicservice |

<a id="sweepgradient-1"></a>
## sweepGradient

```TypeScript
sweepGradient(options: Optional<SweepGradientOptions>): T
```

角度渐变。与[sweepGradient](arkts-arkui-commonmethod-c.md#sweepgradient-1)相比，options参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-sweepGradient(options: Optional<SweepGradientOptions>): T--><!--Device-CommonMethod-sweepGradient(options: Optional<SweepGradientOptions>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;SweepGradientOptions&gt; | 是 | 角度渐变。<br/>当options的值为undefined时，恢复为无角度渐变的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="systembareffect"></a>
## systemBarEffect

```TypeScript
systemBarEffect(): T
```

根据背景进行智能反色并且带有模糊效果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-systemBarEffect(): T--><!--Device-CommonMethod-systemBarEffect(): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="systemmaterial"></a>
## systemMaterial

```TypeScript
systemMaterial(material: SystemUiMaterial | undefined): T
```

Set system-styled materials for the component. The material effect behaves differently on devices with different level of computing powers. On devices with lower computing power, it affects attributes such as the backgroundColor, borderWidth, borderColor, shadow. On devices with higher computing power, it adds a filter effect at the system material layer, which can produce an effect similar to glass.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-systemMaterial(material: SystemUiMaterial | undefined): T--><!--Device-CommonMethod-systemMaterial(material: SystemUiMaterial | undefined): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| material | [SystemUiMaterial](arkts-arkui-systemuimaterial-t.md) \| undefined | 是 | 组件的系统材质对象。设置为undefined时恢复为无材质的效果，若同时设置了材质对象影响的通用属性，会恢复至对应通用属性设置的值，冲突的属性由材质对象决定，参考[ImmersiveMaterial](docroot://reference/apis-arkui/arkts-apis-uimaterial.md#immersivematerial)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="tabindex"></a>
## tabIndex

```TypeScript
tabIndex(index: number): T
```

自定义组件tab键走焦能力。当组件未设置tabIndex时，默认按照预设的焦点移动规则进行焦点移动。

> **说明：**  
>  
> - tabIndex只能够自定义Tab键走焦，若想同时自定义方向键等走焦能力，建议使用[nextFocus](arkts-arkui-commonmethod-c.md#nextfocus-1)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-tabIndex(index: number): T--><!--Device-CommonMethod-tabIndex(index: number): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 自定义组件tab键走焦能力。若有配置了tabIndex大于0的组件，则tab键走焦只会在tabIndex大于0的组件内按照tabIndex的值从小到大并循环依次走焦。若没有配置tabIndex大于0的组件，则tabIndex等于0的组件按照组件预设的走焦规则走焦。<br />[UiExtension](../arkts-apis/arkts-arkui-uiextension.md)组件未适配tabIndex，在含有[UiExtension](../arkts-apis/arkts-arkui-uiextension.md)组件的[层级页面](docroot://ui/arkts-common-events-focus-event.md#基础概念)使用tabIndex会导致走焦错乱。<br />- tabIndex >= 0：表示元素是可聚焦的，并且可以通过tab键走焦来访问到该元素。<br />- tabIndex < 0（通常是tabIndex = -1）：表示元素是可聚焦的，但是不能通过tab键走焦来访问到该元素。<br/> **说明：**<br/>tabIndex与focusScopeId不能混用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="tabstop"></a>
## tabStop

```TypeScript
tabStop(isTabStop: boolean): T
```

设置当前容器组件的tabStop，可决定焦点在走焦时是否会停留在当前容器。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-tabStop(isTabStop: boolean): T--><!--Device-CommonMethod-tabStop(isTabStop: boolean): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isTabStop | boolean | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@atomicservice |

<a id="toolbar"></a>
## toolbar

```TypeScript
toolbar(value: CustomBuilder): T
```

Config toolbar for current component.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonMethod-toolbar(value: CustomBuilder): T--><!--Device-CommonMethod-toolbar(value: CustomBuilder): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform |

<a id="touchable"></a>
## touchable

```TypeScript
touchable(value: boolean): T
```

设置当前组件是否可以响应点击事件、触摸事件等手指交互事件。

> **说明：**

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [hitTestBehavior](arkts-arkui-commonmethod-c.md#hittestbehavior-1)

<!--Device-CommonMethod-touchable(value: boolean): T--><!--Device-CommonMethod-touchable(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置当前组件是否可以响应点击事件、触摸事件等手指交互事件。默认值：true，可以响应交互事件。设置为false时，不可以响应交互事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="transform"></a>
## transform

```TypeScript
transform(value: object): T
```

可用于显示二维变换时的矩阵变换。包含三维变换时应使用[transform3D](arkts-arkui-commonmethod-c.md#transform3d-1)接口。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-transform(value: object): T--><!--Device-CommonMethod-transform(value: object): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | object | 是 | 设置当前组件的变换矩阵。object当前仅支持[Matrix4Transit](../arkts-apis/arkts-arkui-matrix4-matrix4transit-i.md)矩阵对象类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="transform-1"></a>
## transform

```TypeScript
transform(transform: Optional<object>): T
```

可用于显示二维变换时的矩阵变换。包含三维变换时应使用[transform3D](arkts-arkui-commonmethod-c.md#transform3d-1)接口。与[transform](arkts-arkui-commonmethod-c.md#transform-1)相比，transform<sup>18+</sup>参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-transform(transform: Optional<object>): T--><!--Device-CommonMethod-transform(transform: Optional<object>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transform | [Optional](arkts-arkui-optional-t.md)&lt;object&gt; | 是 | 设置当前组件的变换矩阵。object当前仅支持[Matrix4Transit](../arkts-apis/arkts-arkui-matrix4-matrix4transit-i.md)矩阵对象类型。<br/>当transform的值为undefined时，恢复为单位矩阵的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="transform3d"></a>
## transform3D

```TypeScript
transform3D(transform: Optional<Matrix4Transit>): T
```

设置组件的三维变换矩阵。当涉及包含透视效果的三维变换时，transform接口显示效果可能有误，推荐使用transform3D接口。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-transform3D(transform: Optional<Matrix4Transit>): T--><!--Device-CommonMethod-transform3D(transform: Optional<Matrix4Transit>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transform | [Optional](arkts-arkui-optional-t.md)&lt;Matrix4Transit&gt; | 是 | 三维变换矩阵。<br/>当transform的值为undefined时，恢复为单位矩阵的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="transition"></a>
## transition

```TypeScript
transition(value: TransitionOptions | TransitionEffect): T
```

组件插入显示和删除隐藏的过渡效果。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-transition(value: TransitionOptions | TransitionEffect): T--><!--Device-CommonMethod-transition(value: TransitionOptions | TransitionEffect): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TransitionOptions](arkts-arkui-transitionoptions-i.md) \| TransitionEffect | 是 | 设置组件插入显示和删除隐藏的过渡效果。<br/>**说明：** <br/>详细描述见[TransitionOptions](arkts-arkui-transitionoptions-i.md)和[TransitionEffect](arkts-arkui-transitioneffect-c.md)对象说明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="transition-1"></a>
## transition

```TypeScript
transition(effect: TransitionEffect, onFinish: Optional<TransitionFinishCallback>): T
```

组件插入显示和删除隐藏的过渡效果。同[transition](arkts-arkui-commonmethod-c.md#transition-1)相比，增加了转场动画结束的回调。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-transition(effect: TransitionEffect, onFinish: Optional<TransitionFinishCallback>): T--><!--Device-CommonMethod-transition(effect: TransitionEffect, onFinish: Optional<TransitionFinishCallback>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [TransitionEffect](arkts-arkui-transitioneffect-c.md) | 是 | 设置组件插入显示和删除隐藏的过渡效果。 |
| onFinish | [Optional](arkts-arkui-optional-t.md)&lt;TransitionFinishCallback&gt; | 是 | 转场动画结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="translate"></a>
## translate

```TypeScript
translate(value: TranslateOptions): T
```

设置组件平移。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-translate(value: TranslateOptions): T--><!--Device-CommonMethod-translate(value: TranslateOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TranslateOptions](arkts-arkui-translateoptions-i.md) | 是 | 可使组件在以组件左上角为坐标原点的[组件坐标系](docroot://ui/arkui-glossary.md#组件坐标系)中进行移动（坐标系如下图所示）。其中，x，y，z的值分别表示在对应轴移动的距离，值为正时表示向对应轴的正向移动，值为负时表示向对应轴的反向移动。移动距离支持数字和字符串（比如'10px'，'10%'）两种类型。<br/>默认值:<br/>{<br/>x:0,<br/>y: 0,<br/>z: 0<br/>}<br/>单位：vp<br/>![coordinates](docroot://reference/apis-arkui/arkui-ts/figures/coordinates.png)<br/>**说明：**<br/>z轴方向移动时由于观察点位置不变，z的值接近观察点组件会有放大效果，远离则缩小。<br/>![coordinateNode](docroot://reference/apis-arkui/arkui-ts/figures/coordinateNote.png) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="translate-1"></a>
## translate

```TypeScript
translate(translate: Optional<TranslateOptions>): T
```

设置组件平移。与[translate](arkts-arkui-commonmethod-c.md#translate-1)相比，translate参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-translate(translate: Optional<TranslateOptions>): T--><!--Device-CommonMethod-translate(translate: Optional<TranslateOptions>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| translate | [Optional](arkts-arkui-optional-t.md)&lt;TranslateOptions&gt; | 是 | 可使组件在以组件左上角为坐标原点的[组件坐标系](docroot://ui/arkui-glossary.md#组件坐标系)中进行移动（坐标系如下图所示）。其中，x，y，z的值分别表示在对应轴移动的距离，值为正时表示向对应轴的正向移动，值为负时表示向对应轴的反向移动。移动距离支持数字和字符串（比如'10px'，'10%'）两种类型。<br/>默认值:<br/>{<br/>x: 0,<br/>y: 0,<br/>z: 0<br/>}<br/>单位：vp<br/>![coordinates](docroot://reference/apis-arkui/arkui-ts/figures/coordinates.png)<br/>**说明：**<br/>z轴方向移动时由于观察点位置不变，z的值接近观察点组件会有放大效果，远离则缩小。<br/>![coordinateNode](docroot://reference/apis-arkui/arkui-ts/figures/coordinateNote.png)<br/>当translate的值为undefined时，恢复为无平移效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="useeffect"></a>
## useEffect

```TypeScript
useEffect(useEffect: boolean, effectType: EffectType): T
```

用于设置组件是否应用<!--Del-->父级[EffectComponent](arkts-arkui-effectcomponent.md)或<!--DelEnd-->窗口定义的效果模板。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-useEffect(useEffect: boolean, effectType: EffectType): T--><!--Device-CommonMethod-useEffect(useEffect: boolean, effectType: EffectType): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| useEffect | boolean | 是 | 控制组件是否应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>useEffect为true时表示应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>默认值：false |
| effectType | [EffectType](arkts-arkui-effecttype-e.md) | 是 | 设置组件应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>默认值：EffectType.DEFAULT |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="useeffect-1"></a>
## useEffect

```TypeScript
useEffect(useEffect: Optional<boolean>, effectType?: EffectType): T
```

用于设置组件是否应用<!--Del-->父级[EffectComponent](arkts-arkui-effectcomponent.md)或<!--DelEnd-->窗口定义的效果模板。与[useEffect<sup>14+</sup>](arkts-arkui-commonmethod-c.md#useeffect-1)相比，useEffect参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-useEffect(useEffect: Optional<boolean>, effectType?: EffectType): T--><!--Device-CommonMethod-useEffect(useEffect: Optional<boolean>, effectType?: EffectType): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| useEffect | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 控制组件是否应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>useEffect为true时表示应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>默认值：false<br/>当useEffect的值为undefined时，维持之前取值。 |
| effectType | [EffectType](arkts-arkui-effecttype-e.md) | 否 | 设置组件应用<!--Del-->父级EffectComponent或<!--DelEnd-->窗口定义的效果模板。<br/>默认值：EffectType.DEFAULT |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="useeffect-2"></a>
## useEffect

```TypeScript
useEffect(value: boolean): T
```

用于对背景模糊等特效进行绘制合并。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-useEffect(value: boolean): T--><!--Device-CommonMethod-useEffect(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 控制组件是否继承特效绘制合并组件的特效属性参数，从而合并绘制特效。<br/>useEffect为true时子组件继承特效绘制合并组件的特效属性参数，为false时子组件不继承特效绘制合并组件的特效属性参数。<br/>默认值：false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="useshadowbatching"></a>
## useShadowBatching

```TypeScript
useShadowBatching(value: boolean): T
```

控件内部子节点的阴影进行同层绘制，同层元素阴影重叠。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-useShadowBatching(value: boolean): T--><!--Device-CommonMethod-useShadowBatching(value: boolean): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 控件内部子节点的阴影是否进行同层绘制。<br/>默认值：false<br/> true：控件内部子节点的阴影进行同层绘制，子节点的阴影不会产生重叠覆盖效果。<br/>false：控件内部子节点的阴影不进行同层绘制，子节点的阴影重叠区域有覆盖效果。<br/>**说明：**<br/>1. 默认不开启，如果子节点的阴影半径较大，阴影有重叠区域，后绘制的子节点阴影会覆盖在之前绘制的子节点阴影之上。 当开启时，子节点的阴影将同时绘制，不会产生覆盖效果。<br/>2. 不推荐useShadowBatching嵌套使用，如果嵌套使用，只会对当前的子节点生效，无法递推。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="useshadowbatching-1"></a>
## useShadowBatching

```TypeScript
useShadowBatching(use: Optional<boolean>): T
```

控件内部子节点的阴影进行同层绘制，同层元素阴影重叠。与[useShadowBatching<sup>11+</sup>](arkts-arkui-commonmethod-c.md#useshadowbatching-1)相比，use参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-useShadowBatching(use: Optional<boolean>): T--><!--Device-CommonMethod-useShadowBatching(use: Optional<boolean>): T-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| use | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 控件内部子节点的阴影是否进行同层绘制。<br/>默认值：false<br/> true：控件内部子节点的阴影进行同层绘制，子节点的阴影不会产生重叠覆盖效果。<br/> false：控件内部子节点的阴影不进行同层绘制，子节点的阴影重叠区域有覆盖效果。<br/>**说明：**<br/>1. 默认不开启，如果子节点的阴影半径较大，阴影有重叠区域，后绘制的子节点阴影会覆盖在之前绘制的子节点阴影之上。 当开启时，子节点的阴影将同时绘制，不会产生覆盖效果。<br/>2. 不推荐useShadowBatching嵌套使用，如果嵌套使用，只会对当前的子节点生效，无法递推。<br/>当use的值为undefined时，恢复为不使用元素阴影重叠的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。@stagemodelonly@crossplatform@form@atomicservice |

<a id="usesizetype"></a>
## useSizeType

```TypeScript
useSizeType(value: {
    xs?: number | { span: number; offset: number };
    sm?: number | { span: number; offset: number };
    md?: number | { span: number; offset: number };
    lg?: number | { span: number; offset: number };
  }): T
```

Sets the number of occupied columns and offset columns for a specific device width type.

**起始版本：** 7

**废弃版本：** 9

**替代接口：** grid_col/GridColColumnOption

<!--Device-CommonMethod-useSizeType(value: {
    xs?: number | { span: number; offset: number };
    sm?: number | { span: number; offset: number };
    md?: number | { span: number; offset: number };
    lg?: number | { span: number; offset: number };
  }): T--><!--Device-CommonMethod-useSizeType(value: {
    xs?: number | { span: number; offset: number };
    sm?: number | { span: number; offset: number };
    md?: number | { span: number; offset: number };
    lg?: number | { span: number; offset: number };
  }): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | {     xs?: number \| { span: number; offset: number };     sm?: number \| { span: number; offset: number };     md?: number \| { span: number; offset: number };     lg?: number \| { span: number; offset: number };   } | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full |

<a id="visibility"></a>
## visibility

```TypeScript
visibility(value: Visibility): T
```

控制组件的显示或隐藏。当未设置visibility时，组件默认为显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-visibility(value: Visibility): T--><!--Device-CommonMethod-visibility(value: Visibility): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Visibility](../../apis-arkdata/arkts-apis/arkts-arkdata-unifieddatachannel-visibility-e.md) | 是 | 控制当前组件显示或隐藏。根据具体场景需要可使用[条件渲染](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)代替。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="visualeffect"></a>
## visualEffect

```TypeScript
visualEffect(effect: VisualEffect): T
```

设置非滤镜视觉效果。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonMethod-visualEffect(effect: VisualEffect): T--><!--Device-CommonMethod-visualEffect(effect: VisualEffect): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [VisualEffect](arkts-arkui-visualeffect-t.md) | 是 | 非滤镜视觉效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

<a id="width"></a>
## width

```TypeScript
width(value: Length): T
```

设置组件自身的宽度，缺省时使用元素自身内容需要的宽度。若子组件的宽大于父组件的宽，则会超出父组件的范围。

从API version 10开始，该接口支持calc计算特性。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-width(value: Length): T--><!--Device-CommonMethod-width(value: Length): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 要设置的组件宽度   > **说明：**   >   > - 在{@link TextInput}组件中，width设置auto表示自适应文本宽度。   >   > - 在 [AlphabetIndexer](AlphabetIndexer)组件中，width设置auto表示自适应宽度最大索引项的宽度<br>单位为： vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="width-1"></a>
## width

```TypeScript
width(widthValue: Length | LayoutPolicy): T
```

设置组件自身的宽度或水平方向布局策略，缺省时使用元素自身内容需要的宽度。若子组件的宽大于父组件的宽，则会超出父组件的范围。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-width(widthValue: Length | LayoutPolicy): T--><!--Device-CommonMethod-width(widthValue: Length | LayoutPolicy): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| widthValue | [Length](../arkts-apis/arkts-arkui-length-t.md) \| LayoutPolicy | 是 | 要设置的组件宽度。<br>单位为： vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Current component. |

<a id="zindex"></a>
## zIndex

```TypeScript
zIndex(value: number): T
```

设置组件的堆叠顺序。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonMethod-zIndex(value: number): T--><!--Device-CommonMethod-zIndex(value: number): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 同一容器中兄弟组件显示层级关系。zIndex值越大，显示层级越高，即zIndex值大的组件会覆盖在zIndex值小的组件上方。当不涉及新增或减少兄弟节点，动态改变zIndex时会在zIndex改变前层级顺序的基础上进行稳定排序。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

