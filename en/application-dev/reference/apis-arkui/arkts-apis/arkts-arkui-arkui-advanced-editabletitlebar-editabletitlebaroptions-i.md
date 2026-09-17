# EditableTitleBarOptions

Indicates the options of the editable title bar.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconType, EditableTitleBar, EditableTitleBarMenuItem, EditableTitleBarItem, EditableTitleBarOptions } from '@kit.ArkUI';
```

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the title bar.

Default value: **BlurStyle.NONE**

**Type:** [BlurStyle](../arkts-components/arkts-arkui-blurstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the title bar.

Default value: **'#00000000'**

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## safeAreaEdges

```TypeScript
safeAreaEdges?: Array<SafeAreaEdge>
```

Edges for expanding the safe area.

Default value: **[SafeAreaEdge.TOP]**

**Type:** Array&lt;[SafeAreaEdge](../arkts-components/arkts-arkui-safeareaedge-e.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## safeAreaTypes

```TypeScript
safeAreaTypes?: Array<SafeAreaType>
```

Types of the expanded safe areas.

Default value: **[SafeAreaType.SYSTEM]**

**Type:** Array&lt;[SafeAreaType](../arkts-components/arkts-arkui-safeareatype-e.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
