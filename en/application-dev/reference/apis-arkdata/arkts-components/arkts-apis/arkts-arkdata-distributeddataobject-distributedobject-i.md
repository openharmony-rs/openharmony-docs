# DistributedObject

Provides APIs for managing a distributed data object. Before using any API of this class, use createDistributedObject() to create a DistributedObject object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## Modules to Import

```TypeScript
import { distributedDataObject } from '@kit.ArkData';
```

## off('change')

```TypeScript
off(type: 'change', callback?: (sessionId: string, fields: Array<string>) => void): void
```

Unsubscribes from data changes of this distributed data object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [off](arkts-arkdata-distributeddataobject-dataobject-i.md#offchange)(type: 'change', callback?: (sessionId: string, fields: Array&lt;string&gt;) =&gt; void )

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Event type. The value is 'change', which indicates data changes. |
| callback | (sessionId: string, fields: Array&lt;string&gt;) =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unsubscribes from all callbacks for data changes of this distributed object.sessionId indicates the session ID of the distributed data object. fields indicates the changed properties of the distributed data object. |

## off('status')

```TypeScript
off(
      type: 'status',
      callback?: (sessionId: string, networkId: string, status: 'online' | 'offline' ) => void
    ): void
```

Unsubscribes from the status change of this distributed data object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [off](arkts-arkdata-distributeddataobject-dataobject-i.md#offstatus)( type: 'status', callback?: (sessionId: string, networkId: string, status: 'online' | 'offline' ) =&gt; void )

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'status' | Yes | Event type. The value is 'status', which indicates the status change (online or offline) of the distributed object. |
| callback | (sessionId: string, networkId: string, status: 'online' &#124; 'offline' ) =&gt; void | No | Callback to unregister. If this parameter is not specified, this API unsubscribes from all callbacks for status changes of this distributed object. sessionId indicates the session ID of the distributed data object. networkId identifies the distributed data object. status indicates the object status, which can be online or offline. |

## on('change')

```TypeScript
on(type: 'change', callback: (sessionId: string, fields: Array<string>) => void): void
```

Subscribes to data changes of this distributed data object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-arkdata-distributeddataobject-dataobject-i.md#onchange)(type: 'change', callback: (sessionId: string, fields: Array&lt;string&gt;) =&gt; void )

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Event type. The value is 'change', which indicates data changes. |
| callback | (sessionId: string, fields: Array&lt;string&gt;) =&gt; void | Yes | Callback used to return the changes of the distributed data object. sessionId indicates the session ID of the distributed data object. fields indicates the changed properties of the distributed data object. |

## on('status')

```TypeScript
on(
      type: 'status',
      callback: (sessionId: string, networkId: string, status: 'online' | 'offline' ) => void
    ): void
```

Subscribes to status changes of this distributed data object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-arkdata-distributeddataobject-dataobject-i.md#onstatus)( type: 'status', callback: (sessionId: string, networkId: string, status: 'online' | 'offline' ) =&gt; void )

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'status' | Yes | Event type. The value is 'status', which indicates the status change (online or offline) of the distributed object. |
| callback | (sessionId: string, networkId: string, status: 'online' &#124; 'offline' ) =&gt; void | Yes | Callback used to return the status change. sessionId indicates the session ID of the distributed data object. networkId identifies the device. status indicates the object status, which can be online or offline. |

## setSessionId

```TypeScript
setSessionId(sessionId?: string): boolean
```

Sets a session ID. For the devices in the collaboration state in a trusted network, data of the distributed objects with the same session ID can be automatically synced across devices.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setSessionId](arkts-arkdata-distributeddataobject-dataobject-i.md#setsessionid)(sessionId: string, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | No | ID of a distributed data object on a trusted network. To remove a distributed data object from the network, set this parameter to "" or leave it empty. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the session ID is set successfully; returns false otherwise. |

**Examples**

```TypeScript
class SourceObject {
  name: string
  age: number
  isVis: boolean

  constructor(name: string, age: number, isVis: boolean) {
    this.name = name;
    this.age = age;
    this.isVis = isVis;
  }
}

let source: SourceObject = new SourceObject('jack', 18, false);
let g_object: distributedDataObject.DistributedObject = distributedDataObject.createDistributedObject(source);
// Add g_object to the distributed network.
g_object.setSessionId(distributedDataObject.genSessionId());
// Remove g_object from the distributed network.
g_object.setSessionId('');
```
