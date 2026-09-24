# IsolatedComponent properties/events

```TypeScript
declare class IsolatedComponentAttribute extends CommonMethod<IsolatedComponentAttribute>
```

Only the [width](arkts-arkui-common-comp-commonmethod-c.md#width), [height](arkts-arkui-common-comp-commonmethod-c.md#height), and [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor) universal attributes are supported.

The [universal events](arkts-arkui-common-comp.md#common) are not supported.

Events are asynchronously passed to the restricted Worker thread after coordinate conversion.

The following events are supported:

**Inheritance/Implementation:** IsolatedComponentAttribute extends CommonMethod<IsolatedComponentAttribute>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
