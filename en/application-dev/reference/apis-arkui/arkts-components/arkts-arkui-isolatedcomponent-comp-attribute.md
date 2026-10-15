# IsolatedComponent properties/events

```TypeScript
declare class IsolatedComponentAttribute extends CommonMethod<IsolatedComponentAttribute>
```

Only the [width](arkts-arkui-common-comp-commonmethod-c.md#width1), [height](arkts-arkui-common-comp-commonmethod-c.md#height1), and [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor1) universal attributes are supported.

The [universal events](arkts-arkui-common-comp.md) are not supported.

Events are asynchronously passed to the restricted Worker thread after coordinate conversion. Inter-thread event bubbling is not supported, and event conflicts may occur during inter-thread UI interactions.

The following events are supported:

**Inheritance/Implementation:** IsolatedComponentAttribute extends CommonMethod&lt;IsolatedComponentAttribute&gt;

**Since:** 12

<!--Device-unnamed-declare class IsolatedComponentAttribute extends CommonMethod<IsolatedComponentAttribute>--><!--Device-unnamed-declare class IsolatedComponentAttribute extends CommonMethod<IsolatedComponentAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
