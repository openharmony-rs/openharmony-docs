# fromSendableAsset

## Modules to Import

```TypeScript
import { sendableRelationalStore } from '@kit.ArkData';
```

## fromSendableAsset

```TypeScript
function fromSendableAsset(asset: Asset): NonSendableAsset
```

Converts the asset data that can be passed across threads into the data that cannot be passed across threads.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| asset | [Asset](arkts-arkdata-sendablerelationalstore-asset-i.md) | Yes | Asset data that can be passed across threads. |

**Return value:**

| Type | Description |
| --- | --- |
| [NonSendableAsset](arkts-arkdata-sendablerelationalstore-nonsendableasset-t.md) | Asset data that cannot be passed across threads. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |

**Examples**

```TypeScript
const asset1: sendableRelationalStore.NonSendableAsset = {
  name: 'hangman',
  uri: '//path/example',
  path: '//path/example',
  createTime: 'createTime1',
  modifyTime: 'modifyTime1',
  size: 'size1'
};
const sendableAsset = sendableRelationalStore.toSendableAsset(asset1);
const normalAsset = sendableRelationalStore.fromSendableAsset(sendableAsset);
```
