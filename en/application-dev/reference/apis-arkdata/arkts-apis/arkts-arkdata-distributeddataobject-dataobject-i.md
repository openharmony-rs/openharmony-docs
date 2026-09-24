# DataObject

```TypeScript
interface DataObject
```

Provides APIs for managing a distributed data object. Before using any API of this class, use create() to create a DataObject object.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## Modules to Import

```TypeScript
import { distributedDataObject } from '@kit.ArkData';
```

## bindAssetStore

```TypeScript
bindAssetStore(assetKey: string, bindInfo: BindInfo, callback: AsyncCallback<void>): void
```

Binds joint assets. Currently, only the binding between an asset in a distributed data object and an asset in an RDB store is supported. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assetKey | string | Yes | Key of the joint asset in the distributed data object. |
| bindInfo | [BindInfo](arkts-arkdata-distributeddataobject-bindinfo-i.md) | Yes | Information about the joint asset in the RDB store, including the RDB store name, table name, primary key, column name, and asset name in the RDB store. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { commonType } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

class Note {
  title: string | undefined
  text: string | undefined
  attachment: commonType.Asset | undefined

  constructor(title: string | undefined, text: string | undefined, attachment: commonType.Asset | undefined) {
    this.title = title;
    this.text = text;
    this.attachment = attachment;
  }
}

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let attachment: commonType.Asset = {
      name: 'test_img.jpg',
      uri: 'file://com.example.myapplication/data/storage/el2/distributedfiles/dir/test_img.jpg',
      path: '/dir/test_img.jpg',
      createTime: '2024-01-02 10:00:00',
      modifyTime: '2024-01-02 10:00:00',
      size: '5',
      status: commonType.AssetStatus.ASSET_NORMAL
    }
    let note: Note = new Note('test', 'test', attachment);
    let g_object: distributedDataObject.DataObject = distributedDataObject.create(this.context, note);
    g_object.setSessionId('123456');

    const bindInfo: distributedDataObject.BindInfo = {
      storeName: 'notepad',
      tableName: 'note_t',
      primaryKey: {
        'uuid': '00000000-0000-0000-0000-000000000000'
      },
      field: 'attachment',
      assetName: attachment.name as string
    }

    g_object.bindAssetStore('attachment', bindInfo, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to bind asset store. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('bindAssetStore success.');
    });
  }
}
```

<a id="bindassetstore-1"></a>

## bindAssetStore

```TypeScript
bindAssetStore(assetKey: string, bindInfo: BindInfo): Promise<void>
```

Binds joint assets. Currently, only the binding between an asset in a distributed data object and an asset in an RDB store is supported. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assetKey | string | Yes | Key of the joint asset in the distributed data object. |
| bindInfo | [BindInfo](arkts-arkdata-distributeddataobject-bindinfo-i.md) | Yes | Information about the joint asset in the RDB store, including the RDB store name, table name, primary key, column name, and asset name in the RDB store. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { commonType } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

class Note {
  title: string | undefined
  text: string | undefined
  attachment: commonType.Asset | undefined

  constructor(title: string | undefined, text: string | undefined, attachment: commonType.Asset | undefined) {
    this.title = title;
    this.text = text;
    this.attachment = attachment;
  }
}

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let attachment: commonType.Asset = {
      name: 'test_img.jpg',
      uri: 'file://com.example.myapplication/data/storage/el2/distributedfiles/dir/test_img.jpg',
      path: '/dir/test_img.jpg',
      createTime: '2024-01-02 10:00:00',
      modifyTime: '2024-01-02 10:00:00',
      size: '5',
      status: commonType.AssetStatus.ASSET_NORMAL
    }
    let note: Note = new Note('test', 'test', attachment);
    let g_object: distributedDataObject.DataObject = distributedDataObject.create(this.context, note);
    g_object.setSessionId('123456');

    const bindInfo: distributedDataObject.BindInfo = {
      storeName: 'notepad',
      tableName: 'note_t',
      primaryKey: {
        'uuid': '00000000-0000-0000-0000-000000000000'
      },
      field: 'attachment',
      assetName: attachment.name as string
    }

    g_object.bindAssetStore('attachment', bindInfo).then(() => {
      console.info('bindAssetStore success.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to bind asset store. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## off('change')

```TypeScript
off(type: 'change', callback?: (sessionId: string, fields: Array<string>) => void ): void
```

Unsubscribes from data changes of this distributed data object.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Event type. The value is 'change', which indicates data changes. |
| callback | (sessionId: string, fields: Array&lt;string&gt;) =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unsubscribes from all callbacks for data changes of this distributed object. sessionId indicates the session ID of the distributed data object. fields indicates the changed properties of the distributed data object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Examples**

```TypeScript
// Delete the data change callback.
g_object.off('change', (sessionId: string, fields: Array<string>) => {
    console.info('change' + sessionId);
    if (g_object != null && fields != null && fields != undefined) {
        for (let index: number = 0; index < fields.length; index++) {
            console.info('changed !' + fields[index] + ' ' + g_object[fields[index]]);
        }
    }
});
// Unregister all data change callbacks.
g_object.off('change');
```

## off('status')

```TypeScript
off(
      type: 'status',
      callback?: (sessionId: string, networkId: string, status: 'online' | 'offline') => void
    ): void
```

Unsubscribes from the status change of this distributed data object.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'status' | Yes | Event type. The value is 'status', which indicates the status change (online or offline) of the distributed object. |
| callback | (sessionId: string, networkId: string, status: 'online' &#124; 'offline') =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unsubscribes from all callbacks for status changes of this distributed object. sessionId indicates the session ID distributed data object. networkId identifies the distributed data object. status indicates the indicates the object status, which can be online or offline. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Examples**

```TypeScript
// Delete the online/offline callback.
g_object.off('status', (sessionId: string, networkId: string, status: 'online' | 'offline') => {
    console.info('status changed ' + sessionId + ' ' + status + ' ' + networkId);
});
// Unregister all status change callbacks.
g_object.off('status');
```

## off('change')

```TypeScript
off(type: 'change', callback?: DataObserver): void
```

Unsubscribes from data changes of this distributed object.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Event type. The value is 'change', which indicates data changes. |
| callback | [DataObserver](arkts-arkdata-distributeddataobject-dataobserver-t.md) | No | Callback to unregister. If this parameter is not specified, this API unsubscribes from all callbacks for data changes of this distributed object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const changeCallback1: distributedDataObject.DataObserver = (sessionId: string, fields: Array<string>) => {
  console.info('change callback1 ' + sessionId);
  if (fields != null && fields != undefined) {
      for (let index: number = 0; index < fields.length; index++) {
          console.info('change !' + fields[index]);
      }
  }
}

const changeCallback2: distributedDataObject.DataObserver = (sessionId: string, fields: Array<string>) => {
  console.info('change callback2 ' + sessionId);
  if (fields != null && fields != undefined) {
      for (let index: number = 0; index < fields.length; index++) {
          console.info('change !' + fields[index]);
      }
  }
}

try {
  // Unregister a single data change callback function.
  g_object.on('change', changeCallback1);
  g_object.off('change', changeCallback1);

  // Unregister all data change callback functions.
  g_object.on('change', changeCallback1);
  g_object.on('change', changeCallback2);
  g_object.off('change');
} catch (error) {
  let err = error as BusinessError;
  console.error(`Failed to execute. Code: ${err.code}, message: ${err.message}`);
}
```

## off('status')

```TypeScript
off(type: 'status', callback?: StatusObserver): void
```

Unsubscribes from status changes of this distributed object.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'status' | Yes | Event type. The value is 'status', which indicates the status changes of a distributed object. |
| callback | [StatusObserver](arkts-arkdata-distributeddataobject-statusobserver-t.md) | No | Callback to unregister. If this parameter is not specified, this API unsubscribes from all callbacks for status changes of this distributed object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const statusCallback1: distributedDataObject.StatusObserver = (sessionId: string, networkId: string, status: string) => {
  console.info('status callback1' + sessionId);
}

const statusCallback2: distributedDataObject.StatusObserver = (sessionId: string, networkId: string, status: string) => {
  console.info('status callback2' + sessionId);
}
try {
  // Unregister a single status change callback function.
  g_object.on('status', statusCallback1);
  g_object.off('status', statusCallback1);

  // Unregister all status change callback functions.
  g_object.on('status', statusCallback1);
  g_object.on('status', statusCallback2);
  g_object.off('status');
} catch (error) {
  let err = error as BusinessError;
  console.error(`Failed to execute. Code: ${err.code}, message: ${err.message}`);
}
```

## off('progressChanged')

```TypeScript
off(type: 'progressChanged', callback?: ProgressObserver): void
```

Unsubscribes from asset transfer progress changes.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'progressChanged' | Yes | Event type. The value is 'progressChanged', which indicates the asset transfer progress changes. |
| callback | [ProgressObserver](arkts-arkdata-distributeddataobject-progressobserver-t.md) | No | Callback to unregister. If this parameter is not specified, this API unsubscribes from all callbacks for progress changes of this distributed object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const progressChangedCallback1: distributedDataObject.ProgressObserver = (sessionId: string, progress: number) => {
  console.info('progressChanged callback1' + sessionId);
  console.info('progressChanged callback1' + progress);
}

const progressChangedCallback2: distributedDataObject.ProgressObserver = (sessionId: string, progress: number) => {
  console.info('progressChanged callback2' + sessionId);
  console.info('progressChanged callback2' + progress);
}
try {
  g_object.on('progressChanged', progressChangedCallback1);
  // Unsubscribes from the asset transfer progress changes.
  g_object.off('progressChanged', progressChangedCallback1);

  g_object.on('progressChanged', progressChangedCallback1);
  g_object.on('progressChanged', progressChangedCallback2);
  // Unsubscribes from all asset transfer progress changes.
  g_object.off('progressChanged');
} catch (error) {
  let err = error as BusinessError;
  console.error(`Failed to execute. Code: ${err.code}, message: ${err.message}`);
}
```

## on('change')

```TypeScript
on(type: 'change', callback: (sessionId: string, fields: Array<string>) => void ): void
```

Subscribes to data changes of this distributed data object.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Event type. The value is **'change'**, which indicates data changes. sessionId |
| callback | (sessionId: string, fields: Array&lt;string&gt;) =&gt; void | Yes | Callback used to return the changes of the distributed data object. indicates the session ID of the distributed data object. fields indicates the changed properties of the distributed data object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Examples**

```TypeScript
g_object.on('change', (sessionId: string, fields: Array<string>) => {
    console.info('change' + sessionId);
    if (g_object != null && fields != null && fields != undefined) {
        for (let index: number = 0; index < fields.length; index++) {
            console.info('changed !' + fields[index] + ' ' + g_object[fields[index]]);
        }
    }
});
```

## on('status')

```TypeScript
on(
      type: 'status',
      callback: (sessionId: string, networkId: string, status: 'online' | 'offline') => void
    ): void
```

Subscribes to status changes of this distributed data object.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'status' | Yes | Event type. The value is 'status', which indicates the status change (online or offline) of the distributed object. |
| callback | (sessionId: string, networkId: string, status: 'online' &#124; 'offline') =&gt; void | Yes | Callback used to return the status change. sessionId indicates the session ID of the distributed data object. networkId identifies the device. status indicates the object status, which can be online or offline. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Examples**

```TypeScript
g_object.on('status', (sessionId: string, networkId: string, status: 'online' | 'offline') => {
    console.info('status changed ' + sessionId + ' ' + status + ' ' + networkId);
});
```

## on('change')

```TypeScript
on(type: 'change', callback: DataObserver): void
```

Subscribes to data changes of this distributed data object.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Event type. The value is 'change', which indicates data changes. |
| callback | [DataObserver](arkts-arkdata-distributeddataobject-dataobserver-t.md) | Yes | Callback used to listen for data changes of a distributed object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const changeCallback1: distributedDataObject.DataObserver = (sessionId: string, fields: Array<string>) => {
  console.info('change callback1 ' + sessionId);
  if (fields != null && fields != undefined) {
      for (let index: number = 0; index < fields.length; index++) {
          console.info('change !' + fields[index]);
      }
  }
}
try {
  g_object.on('change', changeCallback1);
} catch (error) {
  let err = error as BusinessError;
  console.error(`Failed to execute. Code: ${err.code}, message: ${err.message}`);
}
```

## on('status')

```TypeScript
on(type: 'status', callback: StatusObserver): void
```

Subscribes to the status changes of this distributed object.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'status' | Yes | Event type. The value is 'status', which indicates the status changes of a distributed object. |
| callback | [StatusObserver](arkts-arkdata-distributeddataobject-statusobserver-t.md) | Yes | Callback used to listen for status changes of a distributed object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const statusCallback1: distributedDataObject.StatusObserver = (sessionId: string, networkId: string, status: string) => {
  console.info('status callback ' + sessionId);
}
try {
  g_object.on('status', statusCallback1);
} catch (error) {
  let err = error as BusinessError;
  console.error(`Failed to execute. Code: ${err.code}, message: ${err.message}`);
}
```

## on('progressChanged')

```TypeScript
on(type: 'progressChanged', callback: ProgressObserver): void
```

Subscribes to the asset transfer progress changes.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'progressChanged' | Yes | Event type. The value is 'progressChanged', which indicates the asset transfer progress changes. |
| callback | [ProgressObserver](arkts-arkdata-distributeddataobject-progressobserver-t.md) | Yes | Callback used to listen for the asset transfer progress changes. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const progressChangedCallback: distributedDataObject.ProgressObserver = (sessionId: string, progress: number) => {
  console.info('progressChanged callback' + sessionId);
  console.info('progressChanged callback' + progress);
}
try {
  g_object.on('progressChanged', progressChangedCallback);
} catch (error) {
  let err = error as BusinessError;
  console.error(`Failed to execute. Code: ${err.code}, message: ${err.message}`);
}
```

## revokeSave

```TypeScript
revokeSave(callback: AsyncCallback<RevokeSaveSuccessResponse>): void
```

Revokes the data of this distributed data object saved. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RevokeSaveSuccessResponse](arkts-arkdata-distributeddataobject-revokesavesuccessresponse-i.md)&gt; | Yes | Callback used to return RevokeSaveSuccessResponse, which contains the session ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

```TypeScript
g_object.setSessionId('123456');
// Save data for persistence. 
g_object.save('local', (err: BusinessError, result: distributedDataObject.SaveSuccessResponse) => {
    if (err) {
        console.error(`Failed to save. Code: ${err.code}, message: ${err.message}`);
        return;
    }
    console.info('save callback');
    console.info('save sessionId: ' + result.sessionId);
    console.info('save version: ' + result.version);
    console.info('save deviceId:  ' + result.deviceId);
});
// Delete the persistence data.
g_object.revokeSave((err: BusinessError, result: distributedDataObject.RevokeSaveSuccessResponse) => {
    if (err) {
      console.error(`Failed to revoke save. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('revokeSave callback');
    console.info('revokeSave sessionId ' + result.sessionId);
});
```

<a id="revokesave-1"></a>

## revokeSave

```TypeScript
revokeSave(): Promise<RevokeSaveSuccessResponse>
```

Revokes the data of this distributed data object saved. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RevokeSaveSuccessResponse](arkts-arkdata-distributeddataobject-revokesavesuccessresponse-i.md)&gt; | Promise used to return RevokeSaveSuccessResponse, which contains the session ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

```TypeScript
g_object.setSessionId('123456');
// Save data for persistence. 
g_object.save('local').then((result: distributedDataObject.SaveSuccessResponse) => {
    console.info('save callback');
    console.info('save sessionId ' + result.sessionId);
    console.info('save version ' + result.version);
    console.info('save deviceId ' + result.deviceId);
}).catch((err: BusinessError) => {
    console.error(`Failed to save. Code: ${err.code}, message: ${err.message}`);
});
// Delete the persistence data.
g_object.revokeSave().then((result: distributedDataObject.RevokeSaveSuccessResponse) => {
    console.info('revokeSave callback');
    console.info('sessionId' + result.sessionId);
}).catch((err: BusinessError) => {
    console.error(`Failed to revoke save. Code: ${err.code}, message: ${err.message}`);
});
```

## save

```TypeScript
save(deviceId: string, callback: AsyncCallback<SaveSuccessResponse>): void
```

Saves a distributed data object. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the device where the data is stored. The value local indicates a local device. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SaveSuccessResponse](arkts-arkdata-distributeddataobject-savesuccessresponse-i.md)&gt; | Yes | Callback used to return SaveSuccessResponse, which contains information such as session ID, version, and device ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

```TypeScript
g_object.setSessionId('123456');
g_object.save('local', (err: BusinessError, result:distributedDataObject.SaveSuccessResponse) => {
    if (err) {
        console.error(`Failed to save. Code: ${err.code}, message: ${err.message}`);
        return;
    }
    console.info('save callback');
    console.info('save sessionId: ' + result.sessionId);
    console.info('save version: ' + result.version);
    console.info('save deviceId:  ' + result.deviceId);
});
```

<a id="save-1"></a>

## save

```TypeScript
save(deviceId: string): Promise<SaveSuccessResponse>
```

Saves a distributed data object. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the device where the data is saved. The default value is local, which indicates a local device. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SaveSuccessResponse](arkts-arkdata-distributeddataobject-savesuccessresponse-i.md)&gt; | Promise used to return SaveSuccessResponse, which contains information such as session ID, version, and device ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

```TypeScript
g_object.setSessionId('123456');
g_object.save('local').then((callbackInfo: distributedDataObject.SaveSuccessResponse) => {
    console.info('save callback');
    console.info('save sessionId ' + callbackInfo.sessionId);
    console.info('save version ' + callbackInfo.version);
    console.info('save deviceId ' + callbackInfo.deviceId);
}).catch((err: BusinessError) => {
    console.error(`Failed to save. Code: ${err.code}, message: ${err.message}`);
});
```

## setAsset

```TypeScript
setAsset(assetKey: string, uri: string): Promise<void>
```

Sets the property information about a single asset in a distributed object. This API must be called before the setSessionId API is called. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assetKey | string | Yes | Property name of the asset in the distributed object. |
| uri | string | Yes | URI of the new asset to be set, indicating the distributed path for storing the asset. The value must correspond to an existing asset. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15400002](../errorcode-distributed-dataObject.md#15400002-incorrect-parameter) | Parameter error. Possible causes: 1. The assetKey is invalid, such as ""; 2. The uri is invalid, such as "". |
| [15400003](../errorcode-distributed-dataObject.md#15400003-sessionid-already-set) | The sessionId of the distributed object has been set. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { commonType, distributedDataObject } from '@kit.ArkData';

class Note {
  title: string | undefined
  text: string | undefined
  attachment: commonType.Asset | undefined

  constructor(title: string | undefined, text: string | undefined, attachment: commonType.Asset | undefined) {
    this.title = title;
    this.text = text;
    this.attachment = attachment;
  }
}

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let attachment: commonType.Asset = {
      name: 'test_img.jpg',
      uri: 'file://com.example.myapplication/data/storage/el2/distributedfiles/dir/test_img.jpg',
      path: '/dir/test_img.jpg',
      createTime: '2024-01-02 10:00:00',
      modifyTime: '2024-01-02 10:00:00',
      size: '5',
      status: commonType.AssetStatus.ASSET_NORMAL
    }
    let note: Note = new Note('test', 'test', attachment);
    let g_object: distributedDataObject.DataObject = distributedDataObject.create(this.context, note);

    let uri = 'file://test/test.img';
    g_object.setAsset('attachment', uri).then(() => {
      console.info('setAsset success.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to set asset. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## setAssets

```TypeScript
setAssets(assetsKey: string, uris: Array<string>): Promise<void>
```

Sets the property information about multiple assets in a distributed object. This API must be called before the setSessionId API is called. The number of values contained in the uris array ranges from 1 to 50. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assetsKey | string | Yes | Property name of the assets in the distributed object. |
| uris | Array&lt;string&gt; | Yes | URIs of the new asset array to be set, indicating the distributed paths for storing each element of the asset. The number of array elements ranges from 1 to 50. The URI of an element must be the distributed path corresponding to an actual asset. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15400002](../errorcode-distributed-dataObject.md#15400002-incorrect-parameter) | Parameter error. Possible causes: 1. The assetsKey is invalid, such as ""; 2. The uris is invalid, such as the length of uris is more than 50. |
| [15400003](../errorcode-distributed-dataObject.md#15400003-sessionid-already-set) | The sessionId of the distributed object has been set. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { commonType, distributedDataObject } from '@kit.ArkData';

class Note {
  title: string | undefined
  text: string | undefined
  attachment: commonType.Asset | undefined

  constructor(title: string | undefined, text: string | undefined, attachment: commonType.Asset | undefined) {
    this.title = title;
    this.text = text;
    this.attachment = attachment;
  }
}

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let attachment: commonType.Asset = {
      name: 'test_img.jpg',
      uri: 'file://com.example.myapplication/data/storage/el2/distributedfiles/dir/test_img.jpg',
      path: '/dir/test_img.jpg',
      createTime: '2024-01-02 10:00:00',
      modifyTime: '2024-01-02 10:00:00',
      size: '5',
      status: commonType.AssetStatus.ASSET_NORMAL
    }
    let note: Note = new Note('test', 'test', attachment);
    let g_object: distributedDataObject.DataObject = distributedDataObject.create(this.context, note);

    let uris: Array<string> = ['file://test/test_1.txt', 'file://test/test_2.txt'];
    g_object.setAssets('attachment', uris).then(() => {
      console.info('setAssets success.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to set assets. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## setSessionId

```TypeScript
setSessionId(sessionId: string, callback: AsyncCallback<void>): void
```

Sets a session ID. This API uses an asynchronous callback to return the result. For the devices in the collaboration state in a trusted network, data of the distributed objects with the same session ID can be automatically synced across devices.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | ID of a distributed data object on a trusted network. The value can contain only letters, digits, and underscores (_), and cannot exceed 128 characters. If this parameter is set to "" or null, the distributed data object exits the network. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Asynchronous callback invoked when the session ID is successfully set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. The sessionId allows only letters, digits, and underscores(_), and cannot exceed 128 in length. |
| [15400001](../errorcode-distributed-dataObject.md#15400001-failed-to-create-the-in-memory-database) | Failed to create the in-memory database. |

**Examples**

```TypeScript
// Add g_object to the distributed network.
g_object.setSessionId(distributedDataObject.genSessionId(), () => {
    console.info('join session');
});
// g_object exits the distributed network.
g_object.setSessionId('', () => {
    console.info('leave all session');
});
```

<a id="setsessionid-1"></a>

## setSessionId

```TypeScript
setSessionId(callback: AsyncCallback<void>): void
```

Exits all sessions. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** 
- API version 20 and later: N/A
- API versions 9 to 19: ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked when the distributed data object exits all sessions. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 9 - 19 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Incorrect parameter types. |
| [15400001](../errorcode-distributed-dataObject.md#15400001-failed-to-create-the-in-memory-database) | Failed to create the in-memory database. |

**Examples**

```TypeScript
// Add g_object to the distributed network.
g_object.setSessionId(distributedDataObject.genSessionId(), () => {
    console.info('join session');
});
// Exit the distributed network.
g_object.setSessionId(() => {
    console.info('leave all session.');
});
```

<a id="setsessionid-2"></a>

## setSessionId

```TypeScript
setSessionId(sessionId?: string): Promise<void>
```

Sets a session ID or exits the distributed network. This API uses a promise to return the result. If this parameter is set to "" or null, or left empty, the distributed data object exits the network. For the devices in the collaboration state in a trusted network, data of the distributed objects with the same session ID can be automatically synced across devices.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | No | ID of a distributed data object on a trusted network. The value can contain only letters, digits, and underscores (_), and cannot exceed 128 characters. If this parameter is set to "" or null, or left empty, the distributed data object exits the network. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. The sessionId allows only letters, digits, and underscores(_), and cannot exceed 128 in length. |
| [15400001](../errorcode-distributed-dataObject.md#15400001-failed-to-create-the-in-memory-database) | Failed to create the in-memory database. |

**Examples**

```TypeScript
// Add g_object to the distributed network.
g_object.setSessionId(distributedDataObject.genSessionId()).then(() => {
    console.info('join session.');
}).catch((error: BusinessError) => {
    console.error(`Failed to set sessionId. Code: ${error.code}, message: ${error.message}`);
});
// Exit the distributed network.
g_object.setSessionId().then(() => {
    console.info('leave all session.');
}).catch((error: BusinessError) => {
    console.error(`Failed to set sessionId. Code: ${error.code}, message: ${error.message}`);
});
```
