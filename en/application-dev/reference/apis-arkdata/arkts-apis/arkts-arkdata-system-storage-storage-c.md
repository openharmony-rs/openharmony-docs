# Storage

```TypeScript
export default class Storage
```

**Since:** 3

**Deprecated since:** 6

<!--Device-unnamed-export default class Storage--><!--Device-unnamed-export default class Storage-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## Modules to Import

```TypeScript
```

## clear

```TypeScript
static clear(options?: ClearStorageOptions): void
```

Clears the stored content.

**Since:** 3

**Deprecated since:** 6

**Substitutes:** clear

**Model restriction:** This API can be used only in the FA model.

<!--Device-Storage-static clear(options?: ClearStorageOptions): void--><!--Device-Storage-static clear(options?: ClearStorageOptions): void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ClearStorageOptions](arkts-arkdata-system-storage-clearstorageoptions-i.md) | No | Indicates the target options. |

**Examples**

ArkTS example:

```TypeScript
export default {    
  storageClear() {        
    storage.clear({            
      success: function() {                
        console.info('call storage.clear success.');            
      },            
      fail: function(data, code) {                
        console.error('call storage.clear fail, code: ' + code + ', data: ' + data);            
      },        
    });    
  }
}
```

JS example:

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        Clear Data
    </text>
    <input type="button" value="Clear Data" style="width: 240px; height: 50px; margin: 5px;" onclick="storageClear"></input>
</div>
```

```TypeScript
/* xxx.css */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}
.button {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
```

```TypeScript
// xxx.js
import storage from '@system.storage';

export default {
    data: {
        fontSize: '30px',
        fontColor: '#FF1AFF00',
    },
    storageClear() {
        storage.clear({
            success: function() {
                console.info('call storage.clear success.');
            },
            fail: function(data, code) {
                console.error('call storage.clear fail, code: ' + code + ', data: ' + data);
            },
        });
    }
}
```

## delete

```TypeScript
static delete(options: DeleteStorageOptions): void
```

Deletes the stored content.

**Since:** 3

**Deprecated since:** 6

**Substitutes:** delete

**Model restriction:** This API can be used only in the FA model.

<!--Device-Storage-static delete(options: DeleteStorageOptions): void--><!--Device-Storage-static delete(options: DeleteStorageOptions): void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DeleteStorageOptions](arkts-arkdata-system-storage-deletestorageoptions-i.md) | Yes | Indicates the target options. |

**Examples**

ArkTS example:

```TypeScript
export default {    
  storageDelete() {        
    storage.delete({            
      key: 'Storage1',            
      success: function() {                
        console.info('call storage.delete success.');            
      },            
      fail: function(data, code) {                
        console.error('call storage.delete fail, code: ' + code + ', data: ' + data);            
      },        
    });    
  }
}
```

JS example:

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        Delete Data
    </text>
    <input type="button" value="Delete Data" style="width: 240px; height: 50px; margin: 5px;" onclick="storageDelete"></input>
</div>
```

```TypeScript
/* xxx.css */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}
.button {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
```

```TypeScript
// xxx.js
import storage from '@system.storage';

export default {
    data: {
        fontSize: '30px',
        fontColor: '#FF1AFF00',
    },
    storageDelete() {
        storage.delete({
            key: 'storage_key',
            success: function() {
                console.info('call storage.delete success.');
            },
            fail: function(data, code) {
                console.error('call storage.delete fail, code: ' + code + ', data: ' + data);
            },
        });
    }
}
```

## get

```TypeScript
static get(options: GetStorageOptions): void
```

Reads the stored content.

**Since:** 3

**Deprecated since:** 6

**Substitutes:** get

**Model restriction:** This API can be used only in the FA model.

<!--Device-Storage-static get(options: GetStorageOptions): void--><!--Device-Storage-static get(options: GetStorageOptions): void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GetStorageOptions](arkts-arkdata-system-storage-getstorageoptions-i.md) | Yes | Indicates the target options. |

**Examples**

ArkTS example:

```TypeScript
export default {    
  storageGet() {        
    storage.get({            
      key: 'storage_key',            
      success: function(data) {                
        console.info('call storage.get success: ' + data);            
      },            
      fail: function(data, code) {                
        console.error('call storage.get fail, code: ' + code + ', data: ' + data);            
      },            
      complete: function() {                
        console.info('call complete');            
      },
    });    
  }
}
```

JS example:

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        Get Data
    </text>
    <input type="button" value="Get Data" style="width: 240px; height: 50px; margin: 5px;" onclick="storageGet"></input>
</div>
```

```TypeScript
/* xxx.css */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}
.button {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
```

```TypeScript
// xxx.js
import storage from '@system.storage';

export default {
    data: {
        fontSize: '30px',
        fontColor: '#FF1AFF00',
    },
    storageGet() {
        storage.get({
            key: 'storage_key',
            success: function(data) {
                console.info('call storage.get success: ' + data);
            },
            fail: function(data, code) {
                console.error('call storage.get fail, code: ' + code + ', data: ' + data);
            }
        });
    },
}
```

## set

```TypeScript
static set(options: SetStorageOptions): void
```

Modifies the stored content.

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-Storage-static set(options: SetStorageOptions): void--><!--Device-Storage-static set(options: SetStorageOptions): void-End-->

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SetStorageOptions](arkts-arkdata-system-storage-setstorageoptions-i.md) | Yes | Indicates the target options. |

**Examples**

ArkTS example:

```TypeScript
export default {    
  storageSet() {        
    storage.set({            
      key: 'storage_key',            
      value: 'storage value',            
      success: function() {                
        console.info('call storage.set success.');            
      },            
      fail: function(data, code) {                
        console.error('call storage.set fail, code: ' + code + ', data: ' + data);            
      },        
    });    
  }
}
```

JS example:

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        Set Data
    </text>
    <input type="button" value="Set Data" style="width: 240px; height: 50px; margin: 5px;" onclick="storageSet"></input>
</div>
```

```TypeScript
/* xxx.css */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}
.button {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
```

```TypeScript
// xxx.js
import storage from '@system.storage';

export default {
    data: {
        fontSize: '30px',
        fontColor: '#FF1AFF00',
    },
    storageSet() {
        storage.set({
            key: 'storage_key',
            value: 'test_storage_value',
            success: function() {
                console.info('call storage.set success.');
            },
            fail: function(data, code) {
                console.error('call storage.set fail, code: ' + code + ', data: ' + data);
            },
        });
    }
}
```
