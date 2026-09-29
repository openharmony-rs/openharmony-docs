# TabContentInfo

```TypeScript
export interface TabContentInfo
```

Provides the **TabContent** switching information.

**Since:** 12

<!--Device-uiObserver-export interface TabContentInfo--><!--Device-uiObserver-export interface TabContentInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## id

```TypeScript
id: string
```

ID of the **Tabs** component.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabContentInfo-id: string--><!--Device-TabContentInfo-id: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

Index of the **TabContent** component. The index is zero-based.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabContentInfo-index: number--><!--Device-TabContentInfo-index: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lastIndex

```TypeScript
lastIndex?: number
```

Subscript index of the most recently focused **TabContent** component. The index starts from 0. It exists only in the callback of [on('tabChange')](../../../reference/apis-arkui/arkts-apis-uicontext-uiobserver.md#ontabchange22).

**Type:** number

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-TabContentInfo-lastIndex?: number--><!--Device-TabContentInfo-lastIndex?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state: TabContentState
```

State of the **TabContent** component.

**Type:** [TabContentState](arkts-arkui-uiobserver-tabcontentstate-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabContentInfo-state: TabContentState--><!--Device-TabContentInfo-state: TabContentState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tabContentId

```TypeScript
tabContentId: string
```

ID of the **TabContent** component.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabContentInfo-tabContentId: string--><!--Device-TabContentInfo-tabContentId: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tabContentUniqueId

```TypeScript
tabContentUniqueId: number
```

Unique ID of the **TabContent** component.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabContentInfo-tabContentUniqueId: number--><!--Device-TabContentInfo-tabContentUniqueId: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## uniqueId

```TypeScript
uniqueId: number
```

Unique ID of the **Tabs** component.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabContentInfo-uniqueId: number--><!--Device-TabContentInfo-uniqueId: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
