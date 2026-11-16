# @ohos.sendableResourceManager (Resource Manager)

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=a8446c9be4dbeea364560754c05cf5bc58bb15cf translatedAt=2026-11-04T04:25:05.186Z pushedAt=2026-11-04T10:13:14.942Z nl=1 -->

This module provides the conversion between [Resource](#resource) and [SendableResource](#sendableresource) objects. SendableResource implements the [ISendable](../../arkts-utils/arkts-sendable.md#isendable) interface and supports cross-thread transfer. After cross-thread transfer, a SendableResource object can be converted back to a Resource object and passed as a parameter to the [resource management](./js-apis-resource-manager.md) APIs to obtain resources.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { sendableResourceManager } from '@kit.LocalizationKit';
```

## sendableResourceManager.resourceToSendableResource

resourceToSendableResource(resource: Resource): SendableResource

Converts a Resource object into a SendableResource object that can be transferred across threads.

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

Converts a SendableResource object transferred across threads into a Resource object.

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

Represents sendable resource-related information transferred across threads, including the application bundle name, application module name, resource ID, resource type, and other resource parameters.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Global.ResourceManager

| Type        | Description    |
| ---------- | ------ | 
| [_SendableResource](js-apis-sendableResource.md#sendableresource-1)|**SendableResource** object.|