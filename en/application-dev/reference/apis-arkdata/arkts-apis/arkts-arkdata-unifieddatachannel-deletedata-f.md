# deleteData

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## deleteData

```TypeScript
function deleteData(options: Options, callback: AsyncCallback<Array<UnifiedData>>): void
```

Deletes data from the UDMF public data channel and returns the deleted data set. This API uses an asynchronous callback to return the result.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-unifiedDataChannel-function deleteData(options: Options, callback: AsyncCallback<Array<UnifiedData>>): void--><!--Device-unifiedDataChannel-function deleteData(options: Options, callback: AsyncCallback<Array<UnifiedData>>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Options](arkts-arkdata-unifieddatachannel-options-i.md) | Yes | Configuration parameters. Both key and intention are optional, and intention supports only DATA_HUB. The corresponding verification is performed based on the passed parameters to return different values. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md)&gt;&gt; | Yes | Callback invoked to return all the deleted data.<br>If key is specified in options, the data corresponding to the key is deleted and returned.<br>If intention is specified in options, all data under the intention is deleted and returned.<br>If both intention and key are specified, the intersection of the two is deleted and returned, which is consistent with the result when only key is specified in options; an error is reported if there is no intersection. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Sync/Async] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**Examples**

```TypeScript
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let options: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
};

try {
  unifiedDataChannel.deleteData(options, (err, data) => {
    if (err === undefined) {
      console.info(`Succeeded in deleting data. size = ${data.length}`);
      for (let i = 0; i < data.length; i++) {
        let records = data[i].getRecords();
        for (let j = 0; j < records.length; j++) {
          if (records[j].getTypes().includes(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT)) {
            let text =
              records[j].getEntry(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) as uniformDataStruct.PlainText;
            console.info(`${i + 1}.${text.textContent}`);
          }
        }
      }
    } else {
      console.error(`Failed to delete data. code is ${err.code}, message is ${err.message}`);
    }
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Delete data throws an exception. code is ${error.code}, message is ${error.message}`);
}
```


## deleteData

```TypeScript
function deleteData(options: Options): Promise<Array<UnifiedData>>
```

Deletes data from the UDMF public data channel and returns the deleted data set. This API uses a promise to return the result asynchronously.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-unifiedDataChannel-function deleteData(options: Options): Promise<Array<UnifiedData>>--><!--Device-unifiedDataChannel-function deleteData(options: Options): Promise<Array<UnifiedData>>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Options](arkts-arkdata-unifieddatachannel-options-i.md) | Yes | Configuration parameters. Both key and intention are optional, and intention supports only DATA_HUB. The parameters are verified based on the values passed in to return different results. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md)&gt;&gt; | Promise used to return all deleted data.<br>If key is specified in options, the data corresponding to key is deleted and returned.<br>If intention is specified in options, all data under intention is deleted and returned.<br>If both intention and key are specified, the intersection of the two data sets is deleted and returned, which is the same as the result when only key is specified in options. An error is reported if there is no intersection. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Sync/Async] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**Examples**

```TypeScript
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let options: unifiedDataChannel.Options = {
  key: 'udmf://DataHub/com.ohos.test/0123456789'
};

try {
  unifiedDataChannel.deleteData(options).then((data) => {
    console.info(`Succeeded in deleting data. size = ${data.length}`);
    for (let i = 0; i < data.length; i++) {
      let records = data[i].getRecords();
      for (let j = 0; j < records.length; j++) {
        if (records[j].getTypes().includes(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT)) {
          let text =
            records[j].getEntry(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) as uniformDataStruct.PlainText;
          console.info(`${i + 1}.${text.textContent}`);
        }
      }
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to delete data. code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Delete data throws an exception. code is ${error.code}, message is ${error.message}`);
}
```
