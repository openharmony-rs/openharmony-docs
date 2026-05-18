# DynamicComponent (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

**DynamicComponent** is designed to support the embedding and display of UIs provided by independent .abc files within the current page, with the displayed content running in a worker thread.

It is typically used in modular development scenarios where .abc pages are dynamically loaded.

> **NOTE**
>
> - The APIs provided by this module are system APIs.
> - The APIs of this module can be used only in the stage model.

 **Since:** 26.0.0

## Child Components

None

## APIs

DynamicComponent(options: DynamicOptions)

Creates a **DynamicComponent** component to display the .abc UI running in the worker thread.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [DynamicOptions](#dynamicoptions) | Yes| Configuration parameters for constructing a **DynamicComponent**, which are used to configure the entry of the .abc page to be loaded, worker thread to run, and display options.|

## Worker

type Worker = Worker

Defines the worker thread object for running the .abc file.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type| Description|
| -------- | -------- |
| [Worker](../../apis-arkts/js-apis-worker.md) | An independent thread that runs the .abc file.|

## ErrorCallback

type ErrorCallback = ErrorCallback

Defines the error callback type, which is used to receive exception information.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type| Description|
| -------- | -------- |
| [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | Callback used to receive exception information during running.|

## DynamicOptions

Defines the parameters to be passed during **DynamicComponent** construction.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| entryPoint | string | No| No| Entry of the .abc page to be loaded.|
| worker | [Worker](#worker) | No| No| Worker for running the .abc file.|
| backgroundTransparent | boolean | No| Yes| Whether to enable the transparent background for the component.<br>**true**: yes; **false**: no.<br>The default value is **false**.|
| allowCrossProcessNesting | boolean | No| Yes| Whether to allow cross-process [UIExtensionComponent](./ts-container-ui-extension-component-sys.md) nesting.<br>**true**: yes; **false**: no.<br>The default value is **false**.|

## Attributes

The [universal attributes](ts-component-general-attributes.md) are supported.

## Events

The following events are supported:

### onError

onError(callback: ErrorCallback)

Triggered when an exception occurs during the running of the **DynamicComponent**. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | Yes| Callback used to receive exception information.|
