# @system.storage (Data Storage)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @cuile44-->
<!--Designer: @cuile44-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=46486cda4babacde48f0ca5226e7dc9df57d7cc8 translatedAt=2026-09-15T14:45:40.503Z pushedAt=2026-09-16T07:50:15.766Z -->

>  **NOTE**
>
>  - Module maintenance policy:
>    - For the Lite Wearable device type, this module is maintained over the long term and can be used normally.
>    - For other device types that support this module, this module is no longer maintained since API version 6. You can use the module [@ohos.data.storage (Lightweight Storage)](js-apis-data-storage.md). Since API version 9, you are advised to use the new module [@ohos.data.preferences (User Preferences)](js-apis-data-preferences.md).
>
>  - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  
>  - The APIs of this module can be used only in the FA model.
>  
>  - In the following content, for the Lite Wearable device type, refer to "JS Example"; for other device types that support this module, refer to "ArkTS Example".

## Modules to Import

```js
import storage from '@system.storage';
```

## storage.get

get(options: GetStorageOptions): void

Reads the value stored in the cache based on the specified key.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters**

| Name | Type                   | Mandatory| Description      |
| ------- | -------------------- | ---- | ---------- |
| options | [GetStorageOptions](#getstorageoptions) | Yes  | API configuration.|

**Example**

ArkTS example:

```js
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

```xml
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        Get Data
    </text>
    <input type="button" value="Get Data" style="width: 240px; height: 50px; margin: 5px;" onclick="storageGet"></input>
</div>
```
```css
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
```js
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

## storage.set

set(options: SetStorageOptions): void

Sets the value in the cache based on the specified key.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters**

| Name | Type                  | Mandatory| Description      |
| ------- | ------------------- | ---- | ---------- |
| options | [SetStorageOptions](#setstorageoptions) | Yes  | API configuration.|

**Example**

ArkTS example:

```js
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

```xml
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        Set Data
    </text>
    <input type="button" value="Set Data" style="width: 240px; height: 50px; margin: 5px;" onclick="storageSet"></input>
</div>
```
```css
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
```js
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
## storage.clear

clear(options?: ClearStorageOptions): void

Clears the key-value pairs from the cache.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters**

| Name | Type                                       | Mandatory| Description          |
| ------- | ------------------------------------------- | ---- | -------------- |
| options | [ClearStorageOptions](#clearstorageoptions) | No  | API configuration.|

**Example**

ArkTS example:

```js
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

```xml
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        Clear Data
    </text>
    <input type="button" value="Clear Data" style="width: 240px; height: 50px; margin: 5px;" onclick="storageClear"></input>
</div>
```
```css
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
```js
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

## storage.delete

delete(options: DeleteStorageOptions): void

Deletes the key-value pair based on the specified key.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core.Lite

**Parameters**

| Name | Type                                         | Mandatory| Description          |
| ------- | --------------------------------------------- | ---- | -------------- |
| options | [DeleteStorageOptions](#deletestorageoptions) | Yes  | API configuration.|

**Example**

ArkTS example:

```js
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

```xml
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        Delete Data
    </text>
    <input type="button" value="Delete Data" style="width: 240px; height: 50px; margin: 5px;" onclick="storageDelete"></input>
</div>
```
```css
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
```js
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

## GetStorageOptions

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core.Lite

| Name    | Type         | Mandatory| Description                    |
| -------- | ---------------- | ---- | ------------------- |
| key      | string                               | Yes  | Key of the data to obtain.                                            |
| default  | string                               | No  | Default value returned when the specified key does not exist.                             |
| success  | (data: any) => void                  | No  | Called to return the value obtained when **storage.get()** is successfully called.    |
| fail     | (data: string, code: number) => void | No  | Called to return the result when **storage.get()** fails to be called. **data** indicates the error information, and **code** indicates the error code.|
| complete | () => void                           | No  | Called when **storage.get()** is complete.                              |


## SetStorageOptions

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core.Lite

| Name    | Type               | Mandatory| Description                  |
| -------- | ------------------- | ---- | -------------------- |
| key      | string                               | Yes  | Key of the data to set.                                |
| value    | string                               | Yes  | New value to set. The length must be less than 128 bytes.                             |
| success  | () => void                           | No  | Called when **storage.set()** is successfully called.                              |
| fail     | (data: string, code: number) => void | No  | Called to return the result when **storage.set()** fails to be called. **data** indicates the error information, and **code** indicates the error code.|
| complete | () => void                           | No  | Called when **storage.set()** is complete.                              |


## ClearStorageOptions

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core.Lite

| Name    | Type            | Mandatory| Description                        |
| -------- | --------------------- | ---- | -------------------- |
| success  | () => void                           | No  | Called when **storage.clear()** is successfully called.                              |
| fail     | (data: string, code: number) => void | No  | Called to return the result when **storage.clear()** fails to be called. **data** indicates the error information, and **code** indicates the error code.|
| complete | () => void                           | No  | Called when **storage.clear()** is complete.                              |


## DeleteStorageOptions

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core.Lite

| Name    | Type                | Mandatory| Description                 |
| -------- | -------------------- | ---- | ------------------ |
| key      | string                               | Yes  | Key of the data to delete.                                            |
| success  | () => void                           | No  | Called when **storage.delete()** is successfully called.                              |
| fail     | (data: string, code: number) => void | No  | Called to return the result when **storage.delete()** fails to be called. **data** indicates the error information, and **code** indicates the error code.|
| complete | () => void                           | No  | Called when **storage.delete()** is complete.                              |