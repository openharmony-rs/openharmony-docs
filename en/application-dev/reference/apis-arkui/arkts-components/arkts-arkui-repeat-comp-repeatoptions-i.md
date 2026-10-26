# RepeatOptions

```TypeScript
interface RepeatOptions
```

Defines the options for creating a **Repeat** component.

**Since:** 26.1.0

<!--Device-unnamed-interface RepeatOptions--><!--Device-unnamed-interface RepeatOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowReuseInAnimation

```TypeScript
allowReuseInAnimation?: boolean
```

Whether to allow child components to be reused during the animation when the **Repeat** component is updated. This parameter takes effect only when the parent container of **Repeat** is a **List**, **Grid**, or **WaterFlow** component. When **Repeat** is used together with animations, the reuse capability of **Repeat** may conflict with the animations, causing abnormal animation effects. In this case, you can set this parameter to **false**. In this way, **Repeat** does not reuse child components when it is updated during the animation, thereby adapting to the animations. **true**: Allow child components to be reused during the animation. **false**: Do not allow child components to be reused during the animation. if the parent container of **Repeat** is a **List** component; **true** if it is a **Grid** or **WaterFlow** component. Default value: false.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RepeatOptions-allowReuseInAnimation?: boolean--><!--Device-RepeatOptions-allowReuseInAnimation?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
