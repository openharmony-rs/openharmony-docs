# Element

Element

@interface Element

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## addChild

```TypeScript
addChild(child: Element): void
```

Adds a node to the end of the child node list of the current node.

**Since:** 8

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| child | [Element](arkts-arkui-viewmodel-element-i.md) | Yes | Subnode object to be added |

## animate

```TypeScript
animate(keyframes: Array<AnimateStyle>, options: AnimateOptions): AnimationResult
```

Creates and runs an animation shortcut on the component. Specify the keyframes and options required for the animation.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyframes | Array&lt;[AnimateStyle](arkts-arkui-viewmodel-animatestyle-i.md)&gt; | Yes | keyframes is used to describe key frame parameters of the animation. |
| options | [AnimateOptions](arkts-arkui-viewmodel-animateoptions-i.md) | Yes | Options. is used to describe animation parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| [AnimationResult](arkts-arkui-viewmodel-animationresult-i.md) | This method returns the animation object. |

## createIntersectionObserver

```TypeScript
createIntersectionObserver(param: { ratios: Array<number> }): observer
```

If 0.5 is returned, 50% of the current component is visible.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | { ratios: Array&lt;number&gt; } | Yes | Scope of Monitoring components. |

**Return value:**

| Type | Description |
| --- | --- |
| [observer](arkts-arkui-viewmodel-observer-i.md) |  |

## focus

```TypeScript
focus(obj?: FocusParamObj): void
```

Requests or cancels the focus for a component. If focus is set to true, the focus is requested for the component. If focus is set to false, the focus is canceled for the component. This attribute can be defaulted to true.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | [FocusParamObj](arkts-arkui-viewmodel-focusparamobj-i.md) | No | { focus: true &#124; false } |

## getBoundingClientRect

```TypeScript
getBoundingClientRect(): RectObj
```

Obtains the size and position of the element.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [RectObj](arkts-arkui-viewmodel-rectobj-i.md) | RectObj the size position of the element. |

## rotation

```TypeScript
rotation(obj?: FocusParamObj): void
```

Requests or cancels the crown rotation focus for a component. If focus is set to true, the crown event focus is requested. If focus is set to false, the crown event focus is canceled. This attribute can be defaulted to true.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | [FocusParamObj](arkts-arkui-viewmodel-focusparamobj-i.md) | No | { focus: true &#124; false } |

## setAttribute

```TypeScript
setAttribute(name: string, value: string): void
```

Sets the value of an attribute on a specified element. If the attribute already exists, update the value. Otherwise, a new attribute is added with the specified name and value.

**Since:** 8

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | attribute name |
| value | string | Yes | attribute value¡¢ |

## setStyle

```TypeScript
setStyle(name: string, value: string): boolean
```

Sets a style value on a specified element. If the style exists and the style value is valid, the setting is successful. Otherwise, the setting is invalid.

**Since:** 8

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | style name |
| value | string | Yes | style value |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | If the setting is successful, true is returned. If the setting fails, false is returned. |
