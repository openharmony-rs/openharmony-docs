# PageTransitionExitInterface

```TypeScript
interface PageTransitionExitInterface extends CommonTransition<PageTransitionExitInterface>
```

Provide an interface to set transition style when a page exits.

@extends CommonTransition&lt;PageTransitionExitInterface&gt; @interface PageTransitionExitInterface

**Inheritance/Implementation:** PageTransitionExitInterface extends CommonTransition<PageTransitionExitInterface>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [[Call]]

```TypeScript
(value: PageTransitionOptions): PageTransitionExitInterface
```

Sets the page exit animation.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PageTransitionOptions](arkts-arkui-pagetransitionenter-comp-pagetransitionoptions-i.md) | Yes | pageTransition options |

**Return value:**

| Type | Description |
| --- | --- |
| [PageTransitionExitInterface](arkts-arkui-pagetransitionenter-comp-pagetransitionexitinterface-i.md) |  |

## onExit

```TypeScript
onExit(event: PageTransitionCallback): PageTransitionExitInterface
```

Invoked on a per-frame basis until the exit animation is complete, with the **progress** parameter changing from 0 to 1.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [PageTransitionCallback](arkts-arkui-pagetransitionenter-comp-pagetransitioncallback-t.md) | Yes | Callback invoked on a per-frame basis until the exit animation is complete, with the **progress** parameter changing from 0 to 1.<br>**Since:** 18 |

**Return value:**

| Type | Description |
| --- | --- |
| [PageTransitionExitInterface](arkts-arkui-pagetransitionenter-comp-pagetransitionexitinterface-i.md) |  |
