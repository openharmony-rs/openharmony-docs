# SwipeRefresher

```TypeScript
export declare struct SwipeRefresher
```

The swipe refresher is a component used to obtain and load content, typically with a pull-down gesture.

> **NOTE:** 
> 
> - This component and its child components are supported since API version 10. Updates will be marked with a superscript to indicate their
> 
> - This component can be used only in the stage model.
> 
> - If the **SwipeRefresher** component has [universal attributes](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) and [universal events](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **SwipeRefresher** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **SwipeRefresher** component.

The [universal events](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) are not supported.

**Since:** 10

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SwipeRefresher } from '@kit.ArkUI';
```

## content

```TypeScript
content?: ResourceStr
```

Text displayed when the content is loaded.

The default value is an empty string.

**NOTE:** 

If the text length exceeds the column width, it will be truncated. The Resource type is supported since API version 20.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isLoading

```TypeScript
isLoading: boolean
```

Whether content is being loaded.

**true**: yes

**false**: no

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
