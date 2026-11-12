# @ohos.resourceschedule.suspendManager(Suspend Manager)

Manages the freeze state of background applications. The **suspendManager** module provides APIs for system applications and system abilities to listen for application freeze state changes and query the current freeze state by PID list.

> **NOTE:** 
> 
> - The APIs provided by this module are system APIs.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace suspendManager--><!--Device-unnamed-declare namespace suspendManager-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

## Modules to Import

```TypeScript
import { suspendManager } from '@ohos.resourceschedule.suspendManager';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getSuspendStateByPidList](arkts-backgroundtasks-suspendmanager-getsuspendstatebypidlist-f-sys.md#getsuspendstatebypidlist-1) | Queries the frozen state list by the PID list of processes. |
| [registerSuspendStateObserver](arkts-backgroundtasks-suspendmanager-registersuspendstateobserver-f-sys.md#registersuspendstateobserver-1) | Registers a suspend state observer to listen for application freeze state changes. |
| [unregisterSuspendStateObserver](arkts-backgroundtasks-suspendmanager-unregistersuspendstateobserver-f-sys.md#unregistersuspendstateobserver-1) | Unregisters a previously registered suspend state observer. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [SuspendStateObserver](arkts-backgroundtasks-suspendmanager-suspendstateobserver-i-sys.md) | Defines the observer for suspend state changes. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [FreezeState](arkts-backgroundtasks-suspendmanager-freezestate-e-sys.md) | Enumerates the freeze states of an application. |
<!--DelEnd-->
