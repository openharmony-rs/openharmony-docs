# @ohos.app.ability.errorManager(Error Management Module)

The ErrorManager module provides capabilities for registering and unregistering error observers, which are primarily used to listen for errors such as JavaScript crashes and application freezes.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [off](arkts-ability-errormanager-off-f.md#offerror) | Unregisters an error observer. This API uses an asynchronous callback to return the result. |
| [off](arkts-ability-errormanager-off-f.md#offerror) | Unregisters an error observer. This API uses a promise to return the result. |
| [off](arkts-ability-errormanager-off-f.md#offloopobserver) | Unregisters an observer for the message processing duration of the main thread. |
| [off](arkts-ability-errormanager-off-f.md#offunhandledrejection) | Unregisters an observer for the promise rejection. |
| [off](arkts-ability-errormanager-off-f.md#offglobalunhandledrejectiondetected) | Unregisters a rejected promise observer. After the deregistration, promise exceptions in the process cannot be listened for. |
| [off](arkts-ability-errormanager-off-f.md#offfreeze) | Unregisters an observer for the main thread freeze event of the application. |
| [off](arkts-ability-errormanager-off-f.md#offglobalerroroccurred) | Unregisters a global error observer. Once unregistered, global listening cannot be implemented. |
| [on](arkts-ability-errormanager-on-f.md#onerror) | Registers an error observer. Once registered, it can capture JavaScript crashes occurring within the application, which are a type of application crash. When the observer captures such an exception, the application will not exit automatically. You are advised to add a synchronous exit operation after the callback function completes. |
| [on](arkts-ability-errormanager-on-f.md#onloopobserver) | Registers an observer for the message processing duration of the main thread. After the registration, the execution time of a message processed by the main thread of the application can be captured. |
| [on](arkts-ability-errormanager-on-f.md#onunhandledrejection) | Registers an observer for the promise rejection. After the registration, a rejected promise that is not captured in the current thread of the application can be captured. |
| [on](arkts-ability-errormanager-on-f.md#onglobalunhandledrejectiondetected) | Registers a rejected promise observer with any thread in the process. Once registered, it can capture a rejected promise that is not captured in the current thread of the application. |
| [on](arkts-ability-errormanager-on-f.md#onfreeze) | Registers an observer for the main thread freeze event of the application. If the observer is registered multiple times, only the last one takes effect. |
| [on](arkts-ability-errormanager-on-f.md#onglobalerroroccurred) | Registers a global error observer via the **errorManager.on** API within any thread of a process. Once registered, it can capture exceptions occurring in any thread across the entire process. When the observer captures such an exception, the application will not exit automatically. You are advised to add a synchronous exit operation after the callback function completes. |
| [setDefaultErrorHandler](arkts-ability-errormanager-setdefaulterrorhandler-f.md) | Returns the previously registered handler when a JavaScript crash exception occurs. It can only be used in the main thread. |
| [setDefaultFreezeObserver](arkts-ability-errormanager-setdefaultfreezeobserver-f.md) | Set the default freeze observer, This function will be executed right after the callback function registered through errorManager.on is executed. You can use it to implement chain calls instead of errorManager.on. If an empty observer is set for a certain module, it will cause the call chain to be interrupted. This API must be called in the main thread. |
| [setDefaultResourceUsageObserver](arkts-ability-errormanager-setdefaultresourceusageobserver-f.md) | Set the default resource usage observer. You can use it to implement chain calls. If an empty observer is set for a certain module, it will cause the call chain to be interrupted. This API must be called on the main thread. |

### Interfaces

| Name | Description |
| --- | --- |
| [GlobalError](arkts-ability-errormanager-globalerror-i.md) | Describes the object related to the exception event name, message, error stack information, exception thread name, and exception thread type. |

### Enums

| Name | Description |
| --- | --- |
| [InstanceType](arkts-ability-errormanager-instancetype-e.md) | Enumerates the VM instance types. |
| [ResourceType](arkts-ability-errormanager-resourcetype-e.md) | Define the resource types of the application. |

### Types

| Name | Description |
| --- | --- |
| [ErrorHandler](arkts-ability-errormanager-errorhandler-t.md) | The ErrorHandler will be called when the ArkTS runtime throws an exception that is not caught by the user. |
| [ErrorObserver](arkts-ability-errormanager-errorobserver-t.md) | Defines the ErrorObserver module. |
| [FreezeObserver](arkts-ability-errormanager-freezeobserver-t.md) | Defines an observer for the main thread freeze event of the application. It is used by the application to customize freeze information. |
| [GlobalObserver](arkts-ability-errormanager-globalobserver-t.md) | Defines an exception observer that can be used as an input parameter for [errorManager.on('globalErrorOccurred')](arkts-ability-errormanager-on-f.md#onglobalerroroccurred) and [errorManager.on('globalUnhandledRejectionDetected')](arkts-ability-errormanager-on-f.md#onglobalunhandledrejectiondetected) to monitor event processing on the main thread of the current application. |
| [LoopObserver](arkts-ability-errormanager-loopobserver-t.md) | Defines the LoopObserver module. It can be used as a parameter of **errormanager.on** to listen for and handle main thread timeout events in the current application. |
| [ResourceUsageObserver](arkts-ability-errormanager-resourceusageobserver-t.md) | The observer will be called by the system when resource usage exceed threshold. |
| [UnhandledRejectionObserver](arkts-ability-errormanager-unhandledrejectionobserver-t.md) | Defines an observer to capture the cause of a rejected promise. |
