# CommonConfiguration

```TypeScript
declare interface CommonConfiguration<T>
```

You need a custom class to implement the **ContentModifier** API.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentModifier

```TypeScript
contentModifier: ContentModifier<T>
```

Content modifier that sends the component information required by users to the custom content area.

**Type:** [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;T&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled: boolean
```

Whether to enable the content modifier and respond to operations such as **triggerChange**. The value **true** means to enable the content modifier and respond to operations such as **triggerChange**, and **false** means the opposite.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
