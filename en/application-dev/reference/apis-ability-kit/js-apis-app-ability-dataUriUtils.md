# @ohos.app.ability.dataUriUtils (DataUriUtils Module)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=a914ec5c20531defc3768aa8242b62bbe2d1d08f translatedAt=2026-09-03T10:14:14.534Z pushedAt=2026-09-05T10:47:30.376Z -->

The DataUriUtils module provides the capability to process URI objects, including obtaining, attaching, deleting, and updating the ID at the end of the path of a specified URI object.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { dataUriUtils } from '@kit.AbilityKit';
```

## dataUriUtils.getId

getId(uri: string): number

Obtains the ID attached to the end of a given URI.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type  | Mandatory | Description                       |
| ---- | ------ | ---- | --------------------------- |
| uri  | string | Yes   | URI object from which the ID is to be obtained. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| number | ID obtained. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { dataUriUtils } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let id = dataUriUtils.getId('com.example.dataUriUtils/1221');
  console.info(`get id: ${id}`);
} catch (err) {
  console.error(`get id err, code: ${JSON.stringify((err as BusinessError).code)}, msg: ${JSON.stringify((err as BusinessError).message)}`);
}
```



## dataUriUtils.attachId

attachId(uri: string, id: number): string

Attaches an ID to the end of a given URI.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type  | Mandatory | Description                       |
| ---- | ------ | ---- | --------------------------- |
| uri  | string | Yes   | URI object to which the ID is to be attached. |
| id   | number | Yes  | ID to be attached.           |

**Return value**

| Type  | Description                 |
| ------ | --------------------- |
| string | URI object with the ID attached. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { dataUriUtils } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let id = 1122;
try {
  let uri = dataUriUtils.attachId(
    'com.example.dataUriUtils',
    id,
  );
  console.info(`attachId the uri is: ${uri}`);
} catch (err) {
  console.error(`attachId err, code: ${JSON.stringify((err as BusinessError).code)}, msg: ${JSON.stringify((err as BusinessError).message)}`);
}
```



## dataUriUtils.deleteId

deleteId(uri: string): string

Deletes the ID from the end of a given URI.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type  | Mandatory | Description                       |
| ---- | ------ | ---- | --------------------------- |
| uri  | string | Yes  | URI object from which the ID is to be deleted. |

**Return value**

| Type  | Description               |
| ------ | ------------------- |
| string | URI object with the ID deleted. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { dataUriUtils } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let uri = dataUriUtils.deleteId('com.example.dataUriUtils/1221');
  console.info(`delete id with the uri is: ${uri}`);
} catch (err) {
  console.error(`delete id err, code: ${JSON.stringify((err as BusinessError).code)}, msg: ${JSON.stringify((err as BusinessError).message)}`);
}
```



## dataUriUtils.updateId

updateId(uri: string, id: number): string

Updates the ID in a given URI.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type  | Mandatory | Description               |
| ---- | ------ | ---- | ------------------- |
| uri  | string | Yes   | URI object whose ID is to be updated. |
| id   | number | Yes   | ID to be updated. |

**Return value**

| Type  | Description           |
| ------ | --------------- |
| string | URI object with the new ID. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { dataUriUtils } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let id = 1122;
  let uri = dataUriUtils.updateId(
    'com.example.dataUriUtils/1221',
    id
  );
  console.info(`update id with the uri is: ${uri}`);
} catch (err) {
  console.error(`update id err, code: ${JSON.stringify((err as BusinessError).code)}, msg: ${JSON.stringify((err as BusinessError).message)}`);
}
```

