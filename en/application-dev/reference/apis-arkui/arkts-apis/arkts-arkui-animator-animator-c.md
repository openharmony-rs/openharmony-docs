# Animator

Creates an **Animator** object.

**Since:** 6

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Animator, AnimatorOptions, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';
```

## create

```TypeScript
static create(options: AnimatorOptions): AnimatorResult
```

Creates an **AnimatorResult** object for animations.

> **NOTE:** 
> 
> - Since API version 10, you can use the [createAnimator](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#createanimator) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md), which ensures that the object is created in the intended UI instance.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** createAnimator

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | Yes | Animator options. |

**Return value:**

| Type | Description |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Animator result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

**Examples**

```TypeScript
See ArkTS-based Declarative Development Paradigm.

> NOTE
> 
> For precise UI context management, use the createAnimator API in [UIContext](arkts-apis-uicontext-uicontext.md) to specify the execution context.
```

## create

```TypeScript
static create(options: AnimatorOptions | SimpleAnimatorOptions): AnimatorResult
```

Creates an **AnimatorResult** object for animations. Compared with [create](#create), this API accepts parameters of the [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) &#124; [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | Yes | Parameters of the animation. |

**Return value:**

| Type | Description |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Animator result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

**Examples**

See [create](#create)

## createAnimator

```TypeScript
static createAnimator(options: AnimatorOptions): AnimatorResult
```

Creates an animation.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** create

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | Yes | Animator options. |

**Return value:**

| Type | Description |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Animator result. |

**Examples**

```TypeScript
See ArkTS-based Declarative Development Paradigm.
```
