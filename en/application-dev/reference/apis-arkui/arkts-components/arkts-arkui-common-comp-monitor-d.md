# @Monitor

```TypeScript
declare const Monitor: MonitorDecorator
```

**\@Monitor** is used in [state management V2](../../../ui/state-management/arkts-state-management-overview.md) to listen for changes to state variables, so that the state variables support deep listening. It is applicable to scenarios where custom logic (such as data synchronization, UI refresh, and log recording) needs to be executed when state variables or their nested properties change. Compared with [@Watch](arkts-arkui-common-comp-watch-d.md#watch) in [state management V1](../../../ui/state-management/arkts-state-management-overview.md), **\@Monitor** supports deep listening to changes in nested object properties. Since API version 26.0.0, **\@Monitor** also supports wildcard characters, allowing for more flexible matching of variable paths.

For details, see [@Monitor Decorator: Listening for Value Changes of the State Variables](../../../ui/state-management/arkts-new-monitor.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-unnamed-declare const Monitor: MonitorDecorator--><!--Device-unnamed-declare const Monitor: MonitorDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
