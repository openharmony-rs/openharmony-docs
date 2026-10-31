# @ohos.sendableResourceManager (Resource Manager)

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=cc8fe8b0f1b2859346994908b98ebf9b3df1ff9d translatedAt=2026-07-17T00:25:04.772Z pushedAt=2026-07-17T06:12:20.928Z -->

This module provides the mutual conversion between [Resource](#resource) objects and [SendableResource](#sendableresource) objects. `SendableResource` implements the [ISendable](../../arkts-utils/arkts-sendable.md#isendable) API and supports cross-thread transmission. After cross-thread transmission, the `SendableResource` object can be converted back to a `Resource` object and passed as a parameter to the [resource management](./js-apis-resource-manager.md) APIs to obtain resources.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { sendableResourceManager } from '@kit.LocalizationKit';
```

## sendableResourceManager.resourceToSendableResource

resourceToSendableResource(resource: Resource): SendableResource

Converts a `Resource` object to a `SendableResource` object that can be used for cross-thread transmission.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Global.ResourceManager

**Parameters**

| Name     | Type                                      | Mandatory  | Description                           |
| -------- | ---------------------------------------- | ---- | ----------------------------- |
| resource | [Resource](#resource) | Yes   | **Resource** object.|

**Return value**

| Type    | Description         |
| ------ | ---------------------------- |
| [SendableResource](#sendableresource)  | **SendableResource** object after conversion.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed.                 |

**Example**

```json5
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}
```

```js
import { sendableResourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let sendableResource: sendableResourceManager.SendableResource = sendableResourceManager.resourceToSendableResource($r('app.string.test'));
} catch (error) {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error(`resourceToSendableResource failed, error code: ${code}, message: ${message}.`);
}
```

## sendableResourceManager.sendableResourceToResource

sendableResourceToResource(resource: SendableResource): Resource

Converts a `SendableResource` object transmitted across threads to a `Resource` object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Global.ResourceManager

**Parameters**

| Name     | Type                                      | Mandatory  | Description                           |
| -------- | ---------------------------------------- | ---- | ----------------------------- |
| resource | [SendableResource](#sendableresource) | Yes   | **SendableResource** object.|

**Return value**

| Type    | Description         |
| ------ | ---------------------------- |
| [Resource](#resource) | **Resource** object after conversion.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**Example**

```json5
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}
```

```js
import { sendableResourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let resource: sendableResourceManager.Resource = sendableResourceManager.sendableResourceToResource(sendableResourceManager.resourceToSendableResource($r('app.string.test')));
} catch (error) {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error(`sendableResourceToResource failed, error code: ${code}, message: ${message}.`);
}
```

## Resource

type Resource = _Resource

Represents resource-related information, including the application bundle name, application module name, resource ID, resource type, and other resource parameters.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Global.ResourceManager

| Type   | Description  |
| ------  | ---- | 
|[_Resource](js-apis-resource.md#resource-1)| Defines a **Resource** object.|

## SendableResource

type SendableResource = _SendableResource

Represents Sendable resource-related information for cross-thread transmission, including the application bundle name, application module name, resource ID, resource type, and other resource parameters.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Global.ResourceManager

| Type        | Description    |
| ---------- | ------ | 
| [_SendableResource](js-apis-sendableResource.md#sendableresource-1)|**SendableResource** object.|