# fromSendableValuesBucket

## fromSendableValuesBucket

```TypeScript
function fromSendableValuesBucket(valuesBucket: ValuesBucket): NonSendableBucket
```

将可用于跨线程传递的键值对数据，转换为不能用于跨线程传递的键值对数据。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-sendableRelationalStore-function fromSendableValuesBucket(valuesBucket: ValuesBucket): NonSendableBucket--><!--Device-sendableRelationalStore-function fromSendableValuesBucket(valuesBucket: ValuesBucket): NonSendableBucket-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| valuesBucket | ValuesBucket | 是 | 可用于跨线程传递的ValuesBucket数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NonSendableBucket](arkts-arkdata-sendablerelationalstore-nonsendablebucket-t.md) | 不可跨线程传递的ValuesBucket数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; &lt;br&gt;3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |

## 示例

```TypeScript
const asset1: sendableRelationalStore.NonSendableAsset = {
  name: 'hangman',
  uri: '//path/example',
  path: '//path/example',
  createTime: 'createTime1',
  modifyTime: 'modifyTime1',
  size: 'size1'
};
const asset2: sendableRelationalStore.NonSendableAsset = {
  name: 'hangman',
  uri: '//path/example',
  path: '//path/example',
  createTime: 'createTime1',
  modifyTime: 'modifyTime1',
  size: 'size1'
};
const u8 = new Uint8Array([1, 2, 3]);

const sendableValuesBucket = sendableRelationalStore.toSendableValuesBucket({
  age: 18,
  name: "hangman",
  salary: 100.5,
  passed: true,
  data1: asset1,
  blobType: u8,
  bigValue: BigInt("15822401018187971961171"),
  data2: [asset1, asset2]
});
const nonSendableBucket = sendableRelationalStore.fromSendableValuesBucket(sendableValuesBucket);
```

