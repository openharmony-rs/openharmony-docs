# isKeyItemExist

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## isKeyItemExist

```TypeScript
function isKeyItemExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>): void
```

Checks whether a key exists. This API uses an asynchronous callback to return the result.

If the key does not exist, the error code 12000011 is returned.

**Since:** 9

**System capability:** SystemCapability.Security.Huks.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the key to check. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Attribute tag of the key to be checked. If [HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md) is used to specify the security level of the key to be checked,<br>this parameter can be left empty. If the API version is 12 or later, the default value **CE** is passed in. If the API version is earlier than 12, the default value **DE** is passed in. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the key exists, the value of **data** is **true**. If the key does not exist, **data** is **undefined**, and the error code in **err** is **12000011** with the error description attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000004](../errorcode-huks.md#12000004-file-error) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | error occurred in crypto engine |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | the group id specified by the access group tag is invalid<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
ArkTS sample code:
```

```TypeScript
JS sample code:

> NOTE
> 
> The JS sample code is used only for the lightweight devices.
```

```TypeScript
.container {
  width: 454px;
  height: 800px;
  background-color: #ffffffff;
}

.existBtn {
  left: 77px;
  top: 100px;
  width: 300px;
  height: 80px;
  text-align: center;
  color: white;
  background-color: orange;
  font-size: 25px;
}

.result {
  left: 30px;
  top: 190px;
  width: 390px;
  height: 80px;
  text-align: center;
  color: #ff000000;
  background-color: #ffffffff;
  font-size: 25px;
}
```

```TypeScript
import huks from '@ohos.security.huks';

function testKeyExist() {
    let huksInfo;
    let keyAlias = 'keyAlias';
    let emptyOptions = {
        properties: []
    };

    huks.isKeyItemExist(keyAlias, emptyOptions, (err, data) => {
        if (err) {
            huksInfo = 'isKeyItemExist failed, code: ' + err.code + ', message: ' + err.message;
            console.error(huksInfo);
        } else {
            if (data) {
                huksInfo = `key: ${keyAlias} exists`;
                console.info(huksInfo);
            } else {
                huksInfo = 'key does not exist';
                console.error(huksInfo);
            }
        }
    });
    return huksInfo;
}

export default {
    data: {
        result: ''
    },

    existKey() {
        this.result = testKeyExist();
    },
};
```

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* Set options to emptyOptions. */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};

huks.isKeyItemExist(keyAlias, emptyOptions).then(() => {
  console.info(`keyAlias:${keyAlias} is existed!`);
});
```


## isKeyItemExist

```TypeScript
function isKeyItemExist(keyAlias: string, options: HuksOptions): Promise<boolean>
```

Checks whether a key exists. This API uses a promise to return the result.

If the key does not exist, the error code 12000011 is returned.

**Since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the key to check. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Attribute tag of the key to be checked. If [HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md) is used to specify the security level of the key to be checked,<br>this parameter can be left empty. If the API version is 12 or later, the default value **CE** is passed in. If the API version is earlier than 12, the default value **DE** is passed in. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. If the key exists, the value of **data** is **true**. If the key does not exist, the error code in **err** is **12000011** with the error description attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000004](../errorcode-huks.md#12000004-file-error) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | error occurred in crypto engine |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | the group id specified by the access group tag is invalid<br>**Applicable version:** 23 and later |

**Examples**

See [isKeyItemExist](#iskeyitemexist)
