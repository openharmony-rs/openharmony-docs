# createDistributedObject

## createDistributedObject

```TypeScript
function createDistributedObject(source: object): DistributedObject
```

创建一个分布式数据对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [create](arkts-arkdata-create-f.md#create-1)

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | object | 是 | 设置分布式数据对象的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DistributedObject | 创建完成的分布式数据对象。 |

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

```

