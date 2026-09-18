# FaultLogExtensionAbility

This module implements the delayed fault notification feature.

When the crash and freeze events are subscribed by [HiAppEvent](arkts-performanceanalysis-hiappevent-n.md), the previous event can be received only after the application restarts. If the application fails to start or remains unresponsive for a long time, the fault may not be reported in time.

> **NOTE:** 
> 
> - The APIs of this module can be used only in the stage model.
> 
> - Exceptions may occur if some APIs are called by this module. For details, see [Appendix](../../../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-FaultLogExtensionAbility.md#appendix).

**Since:** 21

**System capability:** SystemCapability.HiviewDFX.Hiview.FaultLogger

## Modules to Import

```TypeScript
import { FaultLogExtensionAbility } from '@kit.PerformanceAnalysisKit';
```

## onConnect

```TypeScript
onConnect(): void
```

Called to perform the initialization operation when the system service completes the connection. This API can be overridden selectively.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.HiviewDFX.Hiview.FaultLogger

**Examples**

```TypeScript
export default class MyFaultLogExtension extends FaultLogExtensionAbility {
    onConnect() {
      console.info('onConnect');
    }
}
```

## onDisconnect

```TypeScript
onDisconnect(): void
```

Called to release resources and clear the running status when the system service completes the disconnection. This API can be overridden selectively.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.HiviewDFX.Hiview.FaultLogger

**Examples**

```TypeScript
export default class MyFaultLogExtension extends FaultLogExtensionAbility {
    onDisconnect() {
      console.info('onDisconnect');
    }
}
```

## onFaultReportReady

```TypeScript
onFaultReportReady(): void
```

Called to subscribe to and process fault events when the system service notifies the FaultLogExtensionAbility to process faults.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.HiviewDFX.Hiview.FaultLogger

**Examples**

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';

export default class MyFaultLogExtension extends FaultLogExtensionAbility {
    onFaultReportReady() {
        hiAppEvent.addWatcher({
            name: "watcher",
            appEventFilters: [
                {
                    domain: hiAppEvent.domain.OS,
                    names: [hiAppEvent.event.APP_CRASH, hiAppEvent.event.APP_FREEZE]
                }
            ],
            onReceive: (domain: string, appEventGroups: Array<hiAppEvent.AppEventGroup>) => {
                // Process the fault event.
            }
        });
    }
}
```

## context

```TypeScript
context: FaultLogExtensionContext
```

Context of the FaultLogExtensionAbility. This context is inherited from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md).

**Type:** [FaultLogExtensionContext](arkts-performanceanalysis-hiviewdfx-faultlogextensioncontext-faultlogextensioncontext-c.md)

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.HiviewDFX.Hiview.FaultLogger
