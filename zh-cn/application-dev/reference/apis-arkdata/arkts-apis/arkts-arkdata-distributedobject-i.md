# DistributedObject

表示一个分布式数据对象。在使用以下接口前，需调用[createDistributedObject()](arkts-arkdata-createdistributedobject-f.md#createdistributedobject-1)获取
DistributedObject对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## off('change')

```TypeScript
off(type: 'change', callback?: (sessionId: string, fields: Array<string>) => void): void
```

当不再进行数据变更监听时，使用此接口删除对象的变更监听。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off(type:

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'change' | 是 | 事件类型，固定为'change'，表示数据变更。 |
| callback | (sessionId: string, fields: Array&lt;string&gt;) =&gt; void | 否 | 需要删除的数据变更回调，若不设置则删除该对象所有的数据变更回调。<br>sessionId：标识变更对象的sessionId；<br>fields：标识对象变更的属性名。 |

**示例：**

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
// 删除数据变更回调changeCallback
g_object.off('change', (sessionId: string, fields: Array<string>) => {
    console.info('change' + sessionId);
    if (fields != null && fields != undefined) {
        for (let index: number = 0; index < fields.length; index++) {
            console.info('changed !' + fields[index] + ' ' + g_object[fields[index]]);
        }
    }
});
// 删除所有的数据变更回调
g_object.off('change');

```

## off('status')

```TypeScript
off(
      type: 'status',
      callback?: (sessionId: string, networkId: string, status: 'online' | 'offline' ) => void
    ): void
```

当不再进行对象上下线监听时，使用此接口删除对象的上下线监听。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off(

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'status' | 是 | 事件类型，固定为'status'，表示对象上下线。 |
| callback | (sessionId: string, networkId: string, status: 'online' \| 'offline' ) =&gt; void | 否 | 需要删除的上下线回调，若不设置则删除该对象所有的上下线回调。<br>sessionId：标识变更对象的sessionId；<br>networkId：标识对象设备；<br>status：标识对象为'online'(上线)或'offline'(下线)的状态。 |

**示例：**

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
// 删除上下线回调changeCallback
g_object.off('status', (sessionId: string, networkId: string, status: 'online' | 'offline') => {
    console.info('status changed ' + sessionId + ' ' + status + ' ' + networkId);
});
// 删除所有的上下线回调
g_object.off('status');

```

## on('change')

```TypeScript
on(type: 'change', callback: (sessionId: string, fields: Array<string>) => void): void
```

监听分布式数据对象的变更。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on(type:

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'change' | 是 | 事件类型，固定为'change'，表示数据变更。 |
| callback | (sessionId: string, fields: Array&lt;string&gt;) =&gt; void | 是 | 变更回调对象实例。<br>sessionId：标识变更对象的sessionId；<br>fields：标识对象变更的属性名。 |

**示例：**

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
g_object.on('change', (sessionId: string, fields: Array<string>) => {
    console.info('change' + sessionId);
    if (fields != null && fields != undefined) {
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
      callback: (sessionId: string, networkId: string, status: 'online' | 'offline' ) => void
    ): void
```

监听分布式数据对象的上下线。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on(

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'status' | 是 | 事件类型，固定为'status'，表示对象上下线。 |
| callback | (sessionId: string, networkId: string, status: 'online' \| 'offline' ) =&gt; void | 是 | 监听上下线回调实例。<br>sessionId：标识变更对象的sessionId；<br>networkId：标识对象设备；<br>status：标识对象为'online'(上线)或'offline'(下线)的状态。 |

**示例：**

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

g_object.on('status', (sessionId: string, networkId: string, status: 'online' | 'offline') => {
    console.info('status changed ' + sessionId + ' ' + status + ' ' + networkId);
});

```

## setSessionId

```TypeScript
setSessionId(sessionId?: string): boolean
```

设置sessionId。当可信组网中有多个设备处于协同状态时，如果多个设备间的分布式对象设置为同一个sessionId，就能自动同步。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setSessionId(sessionId:

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 否 | 分布式数据对象在可信组网中的标识ID。如果要退出分布式组网，设置为""或不设置均可。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：标识设置sessionId成功。<br>false：标识设置sessionId失败。 |

**示例：**

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
// g_object加入分布式组网
g_object.setSessionId(distributedDataObject.genSessionId());
// 设置为""退出分布式组网
g_object.setSessionId('');

```

