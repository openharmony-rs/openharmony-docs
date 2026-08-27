# Storage

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## 导入模块

```TypeScript
```

## clear

```TypeScript
static clear(options?: ClearStorageOptions): void
```

清空缓存中存储的键值对。

**起始版本：** 3

**废弃版本：** 6

**替代接口：** clear

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ClearStorageOptions](arkts-arkdata-system-storage-clearstorageoptions-i.md) | 否 | Indicates the target options. |

**示例**

ArkTS示例：

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

JS示例：

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

删除缓存中索引对应的键值对。

**起始版本：** 3

**废弃版本：** 6

**替代接口：** delete

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DeleteStorageOptions](arkts-arkdata-system-storage-deletestorageoptions-i.md) | 是 | Indicates the target options. |

**示例**

ArkTS示例：

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

JS示例：

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

通过索引读取缓存中存储的值。

**起始版本：** 3

**废弃版本：** 6

**替代接口：** get

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetStorageOptions](arkts-arkdata-system-storage-getstorageoptions-i.md) | 是 | Indicates the target options. |

**示例**

ArkTS示例：

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

JS示例：

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

修改缓存中索引对应的值。

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SetStorageOptions](arkts-arkdata-system-storage-setstorageoptions-i.md) | 是 | Indicates the target options. |

**示例**

ArkTS示例：

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

JS示例：

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
