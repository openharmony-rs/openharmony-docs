# Functions
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=cc99e5187aa152bc96569f8b87fca412b6552a60 translatedAt=2026-11-04T10:36:26.289Z pushedAt=2026-11-04T10:39:18.509Z nl=1 -->

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This module can be imported only to ArkTS files (with the file name extension .ets).

## Modules to Import

```ts
import { ArkTSUtils } from '@kit.ArkTS';
```

## ArkTSUtils.isSendable

isSendable(value: Object | null | undefined): boolean

Checks whether the passed-in value is of the sendable data type.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | Object \| null \| undefined  | Yes | Object to be checked for whether it is a Sendable data type. |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the passed-in value is of the sendable data type; otherwise, **false** is returned.|

**Example**

```ts
import { ArkTSUtils } from '@kit.ArkTS';

@Sendable
function sendableFunc() {
  console.info("sendableFunc");
}

if (ArkTSUtils.isSendable(sendableFunc)) {
  console.info("sendableFunc is Sendable");
} else {
  console.info("sendableFunc is not Sendable");
}
// Expected output: 'sendableFunc is Sendable'
```